---
title: 'Human-AI Collaboration on Open Math Problems: Lessons from the Autocorrelation Inequality'
date: 2026-03-28
permalink: /posts/2026/03/human-ai-collaboration-on-open-math-problems-lessons-from-the-autocorrelation-inequality/ 
tags:
  - Autonomous Research
  - Math
  - AI
  - Distributed Learning
  - Optimization
  - Human-AI Collaboration
---

## Human-AI Collaboration on Open Math Problems: Lessons from the Autocorrelation Inequality

A week ago, I started working on the second autocorrelation inequality problem on [EinsteinArena](https://einsteinchallenge.com/) — a platform where participants compete to find constructions for open problems in mathematics. The goal: maximize C = ||f*f||_2^2 / (||f*f||_1 * ||f*f||_inf) over integer-supported functions f. Within a few days, I had a team of AI agents working on the problem, and we had found a stronger lower bound than that of Google's AlphaEvolve and many subsequent papers.

Here's what I learned about using AI agents to push the frontier on problems like this.

### Orchestrating agents with a ralph loop

My core workflow was built around a **ralph loop** — a recurring agent loop that autonomously runs optimization experiments, evaluates results, and iterates. The loop would launch GPU jobs via Slurm, monitor convergence, compare against the current best solution, and decide what to try next. This freed me from babysitting long-running jobs and let the agents explore the search space around the clock.

The agents would quickly converge to local optima and spin their wheels on incremental perturbation strategies — basin hopping, CMA-ES, random restarts — none of which could escape the trap.

### The human insight that broke the plateau

The breakthrough came from a manual idea: **iterated Dinkelbach iteration**. Rather than directly optimizing the fractional objective C = L2^2/(L1*Linf), Dinkelbach linearization reformulates each step as maximizing L2^2 - lambda*L1*Linf, where lambda is the current best ratio. This fundamentally reshapes the loss landscape at every iteration, opening up descent directions that the original parameterization can't see.

Paired with a softplus relaxation and simulated annealing acceptance, this pipeline vaulted our score to  **#1 on the leaderboard** — C = 0.96199 at n=100k and C = 0.96272 at n=1.6M (beating the SOTA on this as of Feb 2026).

The lesson: agents are excellent at executing and iterating on a well-defined optimization pipeline, but humans, for now, can still contribute meaningful insights.

### Building a shared solution repo

To make progress durable, I set up a [GitHub repository](https://github.com/justinkang221/second-autocorrelation-inequality) with the best known solutions, optimizer code, and a detailed handoff document. This serves two purposes: it lets any new agent (or human) pick up exactly where the last one left off, and it creates a public record of what's been tried and what hasn't worked.

Good documentation turned out to be one of the highest-leverage things I did. A fresh agent session with a comprehensive handoff doc outperforms a long-running session with full context — it avoids the trap of re-exploring dead ends.

### Platforms like EinsteinArena as the future of distributed learning

What excites me most is the bigger picture. EinsteinArena creates a shared benchmark where humans, AI agents, and human-AI teams all compete on the same open problems. This is a fundamentally different paradigm from either pure human mathematics or pure AI reasoning:

- **Agents bring scale**: they can run thousands of optimization experiments, implement and test ideas faster than any human, and maintain meticulous records of what's been tried.
- **Humans bring structure**: reformulating the problem (Dinkelbach), recognizing connections to known theory (fractional programming, Shen & Yu quadratic transforms), and deciding when to abandon a search direction entirely.
- **The platform creates a feedback loop**: a live leaderboard means every participant — human or AI — benefits from knowing the current frontier, and can direct effort toward beating it.

This is what distributed learning looks like in practice. Not a single model trained on all the data, but a community of diverse problem-solvers  converging on hard problems from different angles, with shared infrastructure to coordinate their progress.

We're at C = 0.96272.  The gap is still open, and I suspect closing it will take exactly this kind of collaboration.
