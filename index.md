---
layout: default
title: Home
description: "Tanmana Sadhu — AI researcher at LG Electronics working on LLM agents, long-horizon planning, and safety for autonomous systems."
---

<section class="hero">
  <h1>Tanmana Sadhu</h1>
  <p class="role">
    AI Researcher · <span class="accent">LG Electronics</span>
  </p>

<img class="hero-photo" src="{{ '/assets/img/IMG_3587.jpeg' | relative_url }}" alt="Tanmana Sadhu">

  <p>
    I'm an AI researcher working on <strong>safety and reliability</strong> in 
   large language model based autonomous agents and embodied agents at LG Electronics' Toronto AI Lab. My background spans 
    generative AI, computer vision and multimodal applications such as compositional retrieval. Recently, I have forayed into the realm of physical intelligence encompassing VLAs and World Models. More generally, I have been interested in how agents reason, plan, and stay aligned when operating in messy, open-world environments.
  </p>

  <p>
    Before LGE, my research touched on action recognition, anomaly detection and natural language understanding. I am also deeply passionate about AI for Good, and utilizing technology (or not) for solving social and environmental problems.
  </p>
</section>

<p class="section-title">Recent Works</p>

<ul class="card-list">
  <li>
    <a class="card" href="{{ '/research/' | relative_url }}">
      <p class="title">VestaBench: An Embodied Benchmark for Safe Long-Horizon Planning Under Multi-Constraint and Adversarial Settings</p>
      <p class="meta">arXiv 2024</p>
      <p class="desc">Safety reasoning for embodied AI agents that interact with their physical environments to complete tasks. VESTABENCH is a benchmark curated using VirtualHome and BEHAVIOR-100, including tasks that can be achieved safely under adversarial and multi-constraint settings, as well as adversarial instructions.</p>
    </a>
  </li>
  <li>
    <a class="card" href="{{ '/research/' | relative_url }}">
      <p class="title">ATHENA — Safe autonomous agents with verbal contrastive learning</p>
      <p class="meta">EMNLP 2024</p>
      <p class="desc">Training LLM agents to recognize and avoid unsafe actions through contrastive verbal reasoning.</p>
    </a>
  </li>
</ul>

<p class="section-title">Elsewhere</p>

<p>
  <a href="{{ site.social.scholar }}" target="_blank" rel="noopener">Google Scholar</a> ·
  <a href="mailto:{{ site.author.email }}">Email</a>
  {%- if site.social.github != "" %} ·
    <a href="https://github.com/{{ site.social.github }}" target="_blank" rel="noopener">GitHub</a>
  {%- endif -%}
  {%- if site.social.linkedin != "" %} ·
    <a href="{{ site.social.linkedin }}" target="_blank" rel="noopener">LinkedIn</a>
  {%- endif -%}
</p>
