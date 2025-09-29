---
title: 'Blog Post number 1'
date: 2012-08-14
permalink: /posts/bliss1
tags:
  - cool posts
  - category1
  - category2
---

# SLURM GPU-Only Cluster Guide 🚀

## 🎯 **System Configuration (GPU-Optimized)**

Your SLURM cluster is **optimized exclusively for GPU workloads**:
- **Node**: `bliss1` 
- **GPUs**: 4x NVIDIA L40S GPUs (48GB VRAM each)
- **CPUs**: 128 cores (32 cores per GPU optimal)
- **Memory**: ~1TB RAM
- **Purpose**: GPU computing only (ML/AI/CUDA workloads)

## 🚀 **Single Partition Design**

### **`gpu`** - The Only Partition You Need
- ✅ **Default partition** - All jobs go here
- ✅ **1-4 GPU allocation** - Request what you need
- ✅ **Automatic CPU pairing** - CPUs allocated with GPUs  
- ✅ **No CPU contention** - No CPU-only jobs to compete
- ✅ **Simplified workflow** - No partition selection needed

## 📝 **GPU Job Examples**

### Request 1 GPU:
```bash
#!/bin/bash
#SBATCH --partition=gpu
#SBATCH --gres=gpu:1          # Request 1 GPU
#SBATCH --cpus-per-task=8     # CPUs to go with GPU
#SBATCH --mem=32G             # Memory
#SBATCH --time=01:00:00

# Your GPU code here
python train_model.py
```

### Request Multiple GPUs:
```bash
#!/bin/bash
#SBATCH --partition=gpu
#SBATCH --gres=gpu:3          # Request 3 GPUs
#SBATCH --cpus-per-task=24    # More CPUs for 3 GPUs
#SBATCH --mem=96G             # More memory
#SBATCH --time=02:00:00

# Multi-GPU training
python -m torch.distributed.launch train_multi_gpu.py
```

### Request All 4 GPUs:
```bash
#!/bin/bash
#SBATCH --partition=gpu
#SBATCH --gres=gpu:4          # All GPUs
#SBATCH --cpus-per-task=64    # Half the CPUs
#SBATCH --mem=256G            # Large memory
#SBATCH --time=04:00:00

# Full GPU utilization
python train_large_model.py
```

## ⚡ **Optimal GPU Job Templates**

### Single GPU Job (Recommended ratios):
```bash
#!/bin/bash
#SBATCH --job-name=my_gpu_job
#SBATCH --gres=gpu:1          # 1 GPU
#SBATCH --cpus-per-task=32    # 32 CPUs per GPU (optimal)
#SBATCH --mem=200G            # ~200GB per GPU
#SBATCH --time=24:00:00       # Up to 24 hours

# Your GPU code
python train_model.py
```

### Multi-GPU Job (All 4 GPUs):
```bash
#!/bin/bash  
#SBATCH --job-name=multi_gpu
#SBATCH --gres=gpu:4          # All 4 GPUs
#SBATCH --cpus-per-task=128   # All CPUs
#SBATCH --mem=800G            # Most memory
#SBATCH --time=48:00:00       # Longer for big jobs

# Multi-GPU training
python -m torch.distributed.launch --nproc_per_node=4 train.py
```

## 🔧 **Key Commands**

### Job Submission (Simplified):
```bash
sbatch my_gpu_job.sh               # Submit GPU job (auto-partition)

### Monitoring:
```bash
squeue                              # See all GPU jobs
squeue -u $USER                     # See your jobs  
sinfo -o "%P %F %G"                 # GPU availability
scontrol show job <job_id>          # Detailed job info
nvidia-smi                          # Real-time GPU usage
```

## 🖥️ **Interactive Development with `srun`**

### **Perfect for GPU Development:**
`srun` is ideal for interactive work - you get guaranteed GPU access with the flexibility of real-time development.

### **Basic Interactive Sessions:**
```bash
# Standard development session (2 hours)
srun --gres=gpu:1 --cpus-per-task=32 --mem=200G --time=02:00:00 --pty bash

# Quick testing session (1 hour)
srun --gres=gpu:1 --cpus-per-task=16 --mem=100G --time=01:00:00 --pty bash

# Heavy development (8 hours, 2 GPUs)
srun --gres=gpu:2 --cpus-per-task=64 --mem=400G --time=08:00:00 --pty bash

# Multi-GPU experimentation
srun --gres=gpu:4 --cpus-per-task=128 --mem=800G --time=04:00:00 --pty bash
```

### **Interactive Development Workflow:**
```bash
# 1. Start interactive session
$ srun --gres=gpu:1 --cpus-per-task=32 --mem=200G --pty bash

# 2. Now on compute node with GPU access
(gpu-node)$ nvidia-smi                    # Check GPU allocation
(gpu-node)$ conda activate my-env         # Activate environment
(gpu-node)$ python3                       # Interactive Python
>>> import torch
>>> torch.cuda.is_available()            # Should be True
>>> device = torch.cuda.current_device()
>>> print(f"Using GPU: {device}")

# 3. Development work
(gpu-node)$ jupyter lab --no-browser --port=8888  # Start Jupyter
# OR
(gpu-node)$ ipython                       # Interactive Python
# OR
(gpu-node)$ vim model.py                  # Edit code
(gpu-node)$ python model.py              # Test immediately

# 4. Exit when done
(gpu-node)$ exit
$  # Back to login node
```

### **Development Use Cases:**

#### **Model Development:**
```bash
# Interactive model building and testing
srun --gres=gpu:1 --cpus-per-task=32 --mem=200G --time=04:00:00 --pty bash
# Perfect for: Building models, debugging, hyperparameter tuning
```

#### **Quick GPU Testing:**
```bash
# Just need to test if something works
srun --gres=gpu:1 --cpus-per-task=8 --mem=50G --time=00:30:00 --pty bash
# Perfect for: Quick tests, checking GPU compatibility
```

#### **Interactive Jupyter:**
```bash
# Start Jupyter with GPU access
srun --gres=gpu:1 --cpus-per-task=32 --mem=200G --time=06:00:00 --pty bash
(gpu-node)$ jupyter lab --no-browser --port=8888 --ip=0.0.0.0
# Then tunnel: ssh -L 8888:bliss1:8888 user@bliss1
```

### **Pro Tips for Interactive Sessions:**

#### **Using Screen/Tmux:**
```bash
# Start persistent session
screen -S gpu-dev

# Get GPU allocation within screen
srun --gres=gpu:1 --cpus-per-task=32 --mem=200G --pty bash

# If disconnected, reconnect:
screen -r gpu-dev
```

#### **Check Availability First:**
```bash
# See what's available
sinfo -o "%P %F %G"

# Check specific GPU usage
squeue -o "%.10i %.12P %.10j %.8u %.2t %b"
```

#### **Resource Management:**
```bash
# Check your session resources
echo "GPUs: $CUDA_VISIBLE_DEVICES"
echo "CPUs: $SLURM_CPUS_PER_TASK" 
nvidia-smi  # Current GPU usage
```

### **Interactive Session Best Practices:**

#### **DO:**
- ✅ **Specify reasonable time limits** - Don't hog resources unnecessarily
- ✅ **Use appropriate resources** - Match GPUs/CPUs/memory to your needs
- ✅ **Save work frequently** - Sessions can timeout
- ✅ **Exit when done** - Free resources for teammates
- ✅ **Activate your conda environment** - Access your packages

#### **DON'T:**
- ❌ **Leave sessions idle** - Others might need the GPU
- ❌ **Request excessive resources** - Be considerate of team usage
- ❌ **Forget time limits** - Sessions will terminate automatically
- ❌ **Run long training** - Use batch jobs for multi-hour training

### **Common Interactive Workflows:**

#### **Model Development Cycle:**
```bash
# 1. Get development session
srun --gres=gpu:1 --cpus-per-task=32 --mem=200G --time=04:00:00 --pty bash

# 2. Iterative development
vim model.py          # Edit
python model.py       # Test
vim model.py          # Fix issues  
python model.py       # Test again

# 3. Once working, submit batch job for full training
exit
sbatch --gres=gpu:1 train_job.sh
```

#### **Data Exploration:**
```bash
# Interactive data analysis with GPU
srun --gres=gpu:1 --cpus-per-task=16 --mem=100G --time=02:00:00 --pty bash
python3
>>> import pandas as pd, torch
>>> # Explore data interactively with GPU acceleration
```

**Interactive sessions are perfect for development work** - you get the resource guarantees of SLURM with the flexibility of interactive development! 🚀

## 📊 **GPU Resource Allocation (Optimized)**

### **Intelligent GPU Sharing**:
- ✅ **1-4 GPUs per job** - Request exactly what you need
- ✅ **Concurrent jobs** - Multiple users can run simultaneously
- ✅ **No resource waste** - Unused GPUs available to others
- ✅ **CPU paired with GPUs** - Optimal CPU:GPU ratios

### **Example Scenarios**:
- **User A**: 2 GPUs + 64 CPUs (training large model)
- **User B**: 1 GPU + 32 CPUs (inference/fine-tuning) 
- **User C**: 1 GPU + 32 CPUs (experimentation)
- **All run together** - No waiting, maximum efficiency!

## 💡 **GPU-Only Best Practices**

### **Optimal Resource Requests**:
- **1 GPU jobs**: `--gres=gpu:1 --cpus-per-task=32 --mem=200G` 
- **2 GPU jobs**: `--gres=gpu:2 --cpus-per-task=64 --mem=400G`
- **4 GPU jobs**: `--gres=gpu:4 --cpus-per-task=128 --mem=800G`
- **Rule of thumb**: 32 CPUs and ~200GB RAM per GPU

### **Why This is Optimal for GPU-Only**:
- ❌ **No CPU competition** - No CPU-only jobs stealing resources
- ✅ **Predictable performance** - GPU jobs get consistent CPU support
- ✅ **Simplified management** - One partition, no confusion
- ✅ **Maximum GPU utilization** - All resources dedicated to GPU workloads

## 🎯 **GPU Workflow Examples**

### Typical Multi-User Scenario:
```bash
# User A: Large model training
sbatch --gres=gpu:2 --time=48:00:00 large_training.sh

# User B: Model inference  
sbatch --gres=gpu:1 --time=02:00:00 inference.sh

# User C: Hyperparameter tuning
sbatch --gres=gpu:1 --time=12:00:00 hyperopt.sh
```
