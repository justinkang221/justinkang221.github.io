---
permalink: /
title: "Justin Kang"
excerpt: "About Me"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---
I am a PhD candidate at UC Berkeley (EECS), affiliated with <a href='https://bair.berkeley.edu/'>BAIR</a> and advised by <a href='https://people.eecs.berkeley.edu/~kannanr'>Prof. Kannan Ramchandran</a>. My research develops efficient algorithms for **ML interpretability and attribution** — explaining which input features, training data, and interactions drive model predictions in LLMs and other large-scale models. I am an <a href="https://www.nserc-crsng.gc.ca/">NSERC</a> Doctoral Fellow and Berkeley Graduate Fellow, and have interned with Google Research, Bosch AI Research, and Intel.

<div class="job-market-callout">
  <strong>I am on the job market for research scientist and ML engineer positions starting in 2026.</strong>
  <a href="/files/Resume.pdf" class="cv-btn">CV / Resume</a>
</div>

News
======
* Papers <a href="https://arxiv.org/abs/2602.02639">*A Positive Case for Faithfulness*</a> and <a href="https://arxiv.org/abs/2602.01399">*An Odd Estimator for Shapley Values*</a> accepted to **ICML 2026**.
* <a href="https://arxiv.org/abs/2602.02639">*A Positive Case for Faithfulness*</a> presented at the **ICLR 2026 Trustworthy AI** conference.
* Featured in <a href="https://www.together.ai/blog/einsteinarena">Together AI's blog post on EinsteinArena</a> — reclaimed **#1** on the <a href="https://einsteinarena.com/">second autocorrelation inequality leaderboard</a>.
* New blog post: <a href="/posts/2026/03/human-ai-collaboration-on-open-math-problems-lessons-from-the-autocorrelation-inequality/">Human-AI Collaboration on Open Math Problems</a> — how I used AI agents to achieve #1 on the EinsteinArena leaderboard.
* BAIR blog post: <a href="https://bair.berkeley.edu/blog/2026/03/13/spex/">Identifying Interactions at Scale for LLMs</a> — an overview of our SPEX line of work on scalable feature interaction explanations.
* Talk at ITA 2026 graduation day — won the *sea award*. (<a href="/files/ITA 2026.pdf">slides</a>)
* I was selected as a 2026 <a href="https://www.heronsec.ai/">Heron AI Security Fellow</a>.
* Papers *ProxySPEX* (Spotlight) and *SHAP-Zero* (Poster) accepted to NeurIPS 2025.
* Prof. Bin Yu presented our work at the Flatiron Institute <a href="https://www.simonsfoundation.org/video/bin-yu-understanding-deep-learning-models-via-interaction-importance/">Understanding Deep Learning Models via Interaction Importance</a>.

<details>
<summary><strong>Older Announcements</strong></summary>
<ul>
<li><em>SPEX: Scaling Feature Interaction Explanations for LLMs</em> accepted to ICML 2025.</li>
<li>Presented research on interpreting LLMs at <a href="https://arl.devcom.army.mil/">DEVCOM Army Research Lab</a>.</li>
<li>Joining Bosch AI Research for summer 2025, working on autolabeling and data filtering with Suraj Srinivas, Jorge Piazentin Ono, and Jared Evans.</li>
<li><em>Learning to Understand: Identifying Interactions via the Mobius Transform</em> accepted to NeurIPS 2024.</li>
<li>Interviewed for a <a href="https://builtin.com/articles/what-is-federated-learning">Built In article on Federated Learning</a>.</li>
<li>My paper won the <a href="https://www.itsoc.org/news/recipients-2024-ieee-communication-society-and-information-theory-society-joint-paper-award">2024 IEEE Communication Society and Information Theory Society Joint Paper Award</a>.</li>
<li>Joined Google for summer 2024 as a Student Researcher in the Cloud Platforms Systems Research Group (SRG).</li>
</ul>
</details>

<br>

Research Highlights
======
<figure class="research-figure">
  <img src="/images/proxy_spex_image.png" alt="ProxySPEX pipeline: masked inference, proxy fitting, and Fourier extraction for LLM interpretability">
  <figcaption>The ProxySPEX pipeline — scalable feature interaction explanations for LLMs</figcaption>
</figure>

* **Interpretability & Data Attribution:** I build scalable tools (SPEX, ProxySPEX) that identify important feature interactions and data attribution in LLMs, achieving up to 20% better faithfulness than prior methods like SHAP, and scaling to 1000+ input features. Check out the <a href="https://github.com/mmschlk/shapiq">shapiq</a> library to try it out!
* **Signal Processing → ML:** I bring a strong signal processing and information theory perspective to ML problems, which leads to unique algorithmic solutions — including sparse Möbius/Fourier transforms for efficient model explanation.
* **Faithfulness of Explanations:** I recently led work on evaluating whether <a href="https://arxiv.org/abs/2602.02639">LLM self-explanations are faithful</a> to actual model behavior in collaboration with Noah Siegel from Google Deepmind.
* **Award-Winning Research:** My work on scheduling in massive random access networks won the <a href="https://www.itsoc.org/news/recipients-2024-ieee-communication-society-and-information-theory-society-joint-paper-award">2024 IEEE ComSoc & IT Society Joint Paper Award</a>. <span class="venue-badge award">Joint Paper Award</span>

<br>

Selected Papers
======
<small>(<span class="equal-contrib">\*</span> denotes equal contribution)</small>

1. A Positive Case for Faithfulness: LLM Self-Explanations Help Predict Model Behavior.<br>*Mayne, H.<span class="equal-contrib">\*</span>, <b>Kang, J.S.</b><span class="equal-contrib">\*</span>, Gould, D., Ramchandran, K., Mahdi, A., Siegel, N.Y.* <br><span class="venue-badge conference">ICML 2026</span> <span class="venue-badge workshop">ICLR 2026 Trustworthy AI</span> <span class="paper-links"><a href="https://arxiv.org/abs/2602.02639">paper</a></span>

2. An Odd Estimator for Shapley Values.<br>*Fumagalli, F., Butler, L., <b>Kang, J.S.</b>, Ramchandran, K., Witter, R.T.* <br><span class="venue-badge conference">ICML 2026</span> <span class="paper-links"><a href="https://arxiv.org/abs/2602.01399">paper</a></span>

3. ProxySPEX: Inference-Efficient Interpretability via Sparse Feature Interactions in LLMs.<br>*Butler, L.<span class="equal-contrib">\*</span>, Agarwal, A.<span class="equal-contrib">\*</span>, <b>Kang, J.S.</b><span class="equal-contrib">\*</span>, Erginbas, Y.E., Ramchandran, K., Yu, B.* <br><span class="venue-badge spotlight">NeurIPS 2025 Spotlight</span> <span class="paper-links"><a href="https://arxiv.org/abs/2505.17495">paper</a> <a href="/files/ProxySPEX_Poster.pdf">poster</a> <a href="https://www.youtube.com/watch?v=k0Osjkj7l0s">video</a></span>

4. SHAP-Zero explains biological sequence models with near-zero marginal cost.<br>*Tsui, D., Musharaf, A., Erginbas, Y.E., <b>Kang, J.S.</b>, Aghazadeh, A.* <br><span class="venue-badge conference">NeurIPS 2025</span> <span class="paper-links"><a href="https://arxiv.org/abs/2410.19236">paper</a> <a href="/files/SHAPzero_poster.png">poster</a> <a href="https://www.youtube.com/watch?v=FUjjYlrKlUM">video</a></span>

5. SPEX: Scaling Feature Interaction Explanations for LLMs.<br>*<b>Kang, J.S.</b><span class="equal-contrib">\*</span>, Butler, L.<span class="equal-contrib">\*</span>, Agarwal, A.<span class="equal-contrib">\*</span>, Erginbas, Y.E., Pedarsani, R., Ramchandran, K., Yu, B.* <br><span class="venue-badge conference">ICML 2025</span> <span class="paper-links"><a href="https://arxiv.org/abs/2502.13870">paper</a> <a href="/files/SPEX_Poster.pdf">poster</a> <a href="https://www.youtube.com/watch?v=cV5UWAx8TPg">video</a></span>

6. Learning to Understand: Identifying Interactions via the Mobius Transform.<br>*<b>Kang, J.S.</b>, Erginbas, Y.E., Butler, L., Pedarsani, R., Ramchandran, K.* <br><span class="venue-badge conference">NeurIPS 2024</span> <span class="paper-links"><a href="https://arxiv.org/abs/2402.02631">paper</a> <a href="/files/Learning_to_understand_poster.pdf">poster</a> <a href="https://www.youtube.com/watch?v=5-OHk25H1mE">video</a></span>

7. The Fair Value of Data Under Heterogeneous Privacy Constraints in Federated Learning.<br>*<b>Kang, J.S.</b>, Pedarsani, R., Ramchandran, K.* <br><span class="venue-badge conference">TMLR 2024</span> <span class="venue-badge workshop">NeurIPS FL@FM 2023 Workshop Oral</span> <span class="paper-links"><a href="https://arxiv.org/abs/2301.13336">paper</a> <a href="/files/Fairness_Poster.pdf">poster</a> <a href="https://www.youtube.com/watch?v=S_DBTIlaodE">video</a></span>

Industry Experience
======
* **Google** — Student Researcher, Cloud Platforms Systems Research Group (Summer 2024)
* **Bosch AI Research** — Research Intern, working on autolabeling and data filtering (Summer 2025)
* **Intel** — Non-Volatile Memory Solutions Group, Storage Systems Research Intern (previously)

Education
======
* **PhD** in EECS, UC Berkeley (in progress)
* **M.A.Sc.** in ECE, University of Toronto — advised by <a href='https://www.comm.utoronto.ca/~weiyu/'>Prof. Wei Yu</a>
* **B.A.Sc.** in <a href="https://www.engphys.ubc.ca/">Engineering Physics</a>, University of British Columbia
