---
layout: default
title: Blog
permalink: /blog/
description: "Notes by Tanmana Sadhu on LLM agents, planning, safety, and papers worth reading."
---

# Blog

Short notes on papers, experiments, and things I'm thinking about. Not every post
is polished — some are just thinking out loud.

{% if site.posts.size > 0 %}
<ul class="post-list">
  {% for post in site.posts %}
  <li>
    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
    <p class="post-meta">
      <time datetime="{{ post.date | date_to_xmlschema }}">
        {{ post.date | date: "%B %-d, %Y" }}
      </time>
      {% if post.excerpt_short %} · {{ post.excerpt_short }}{% endif %}
    </p>
  </li>
  {% endfor %}
</ul>
{% else %}
<div class="empty">
  No posts yet — first one coming soon.
</div>
{% endif %}
