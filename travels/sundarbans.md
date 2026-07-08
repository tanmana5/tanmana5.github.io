---
layout: default
title: Sundarbans
permalink: /travels/sundarbans/
description: "Photographs from a trip to the Sundarbans, home of the swamp tigers."
---

# Sundarbans

Photographs from a trip through the mangrove waterways of the Sundarbans, home
of the swamp tigers. See the accompanying essay: [Swamp Tigers and Salinity in
the Sundarbans](https://www.linkedin.com/pulse/swamp-tigers-salinity-sunderbans-tanmana-sadhu-dfp3c/).

{% if site.data.gallery_sundarbans and site.data.gallery_sundarbans.size > 0 %}
<ul class="gallery-grid">
  {% for img in site.data.gallery_sundarbans %}
  <li>
    <figure>
      <img src="{{ '/assets/img/sundarbans/' | append: img.file | relative_url }}"
           alt="{{ img.caption | default: 'Photograph from the Sundarbans' }}"
           loading="lazy">
      {% if img.caption %}<figcaption>{{ img.caption }}</figcaption>{% endif %}
    </figure>
  </li>
  {% endfor %}
</ul>
{% else %}
<div class="empty">
  Photographs coming soon.
</div>
{% endif %}

<p class="gallery-copyright">All photographs © 2026 Tanmana Sadhu. Please do not reproduce without permission.</p>
