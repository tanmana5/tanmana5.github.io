---
layout: default
title: Home
---

<section class="hero">
  <h1>Tanmana Sadhu</h1>
  <p class="role">
    AI Researcher · <span class="accent">LG Electronics</span>
  </p>

<img class="hero-photo" src="{{ '/assets/img/IMG_3587.jpeg' | relative_url }}" alt="Tanmana Sadhu">

  <p>
    I'm an AI researcher working on <strong>large language model agents</strong>,
    long-horizon planning, and safety in autonomous systems. My background spans
    computer vision and natural language processing — most recently I've been
    interested in how language agents reason, plan, and stay aligned when the
    stakes get higher than a single API call.
  </p>

  <p>
    Before LG, my research touched image-guided navigation, augmented reality,
    and compositional image retrieval. I like problems where the model has to
    interact with the world and recover when something goes wrong.
  </p>
</section>

<p class="section-title">Selected work</p>

<ul class="card-list">
  <li>
    <a class="card" href="{{ '/research/' | relative_url }}">
      <p class="title">ATHENA — Safe autonomous agents with verbal contrastive learning</p>
      <p class="meta">EMNLP 2024</p>
      <p class="desc">Training LLM agents to recognize and avoid unsafe actions through contrastive verbal reasoning.</p>
    </a>
  </li>
  <li>
    <a class="card" href="{{ '/research/' | relative_url }}">
      <p class="title">TravelPlanner — Can LLM agents draft long-horizon plans?</p>
      <p class="meta">arXiv 2024</p>
      <p class="desc">A close look at where today's LLM planners break down on realistic multi-day, multi-constraint itineraries.</p>
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
