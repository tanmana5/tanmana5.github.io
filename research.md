---
layout: default
title: Research
permalink: /research/
description: "Selected publications and research interests of Tanmana Sadhu — LLM agents, planning, safety and alignment, and vision–language grounding."
---

# Research

I work on agents that have to plan, act, and stay safe in environments more
complex than single-turn chat. Below are selected publications. The full list lives on
[Google Scholar]({{ site.social.scholar }}).

<p class="section-title">Publications</p>

<ul class="pub-list">
  {% for pub in site.data.publications %}
  <li class="pub-item">
    <p class="pub-title">{{ pub.title }}</p>
    <p class="pub-authors">{{ pub.authors }}</p>
    <p class="pub-venue">{{ pub.venue }}, {{ pub.year }}{% if pub.citations %} · {{ pub.citations }} citations{% endif %}</p>
    {% if pub.links %}
    <p class="pub-links">
      {% if pub.links.paper %}<a href="{{ pub.links.paper }}" target="_blank" rel="noopener">Paper</a>{% endif %}
      {% if pub.links.arxiv %}<a href="{{ pub.links.arxiv }}" target="_blank" rel="noopener">arXiv</a>{% endif %}
      {% if pub.links.code  %}<a href="{{ pub.links.code  }}" target="_blank" rel="noopener">Code</a>{% endif %}
      {% if pub.links.slides %}<a href="{{ pub.links.slides }}" target="_blank" rel="noopener">Slides</a>{% endif %}
    </p>
    {% endif %}
  </li>
  {% endfor %}
</ul>

<p class="section-title">Research areas</p>

- **Safe Robotic Manipulation** — how to build in behavioral safety for robot manipulation tasks, such as collision avoidance.
- **LLM agents & planning** — how language models reason over long horizons, recover from failure, and interact with tools and environments.
- **Safety & alignment for agents** — verbal contrastive learning, refusal behavior, and detecting unsafe action sequences before they execute.
- **Vision–language grounding** — earlier work on compositional image retrieval and image-guided navigation.

<p class="section-title">Collaborations & talks</p>

<div class="empty">
  Add invited talks, reviewing, or collaboration highlights here as they happen.
</div>
