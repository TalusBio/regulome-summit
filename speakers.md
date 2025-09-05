---
layout: page
title: Speakers
---

# Speakers

{% assign speakers = site.data.speakers | sort: "order" %}
{% for s in speakers %}
<details class="speaker" id="{{ s.id }}">
  <summary>
    <img src="{{ '/assets/images/speakers/' | append: s.img | relative_url }}" alt="{{ s.name }} headshot" width="64" height="64" style="border-radius:50%;object-fit:cover;">
    <div class="meta">
      <strong>{{ s.name }}</strong>
      {{ s.role }}, {{ s.org }}
      <div class="hint">Click for bio</div>
    </div>
  </summary>
  <div style="margin:0.75rem 0 1.25rem 90px;">
    <p>{{ s.bio }}</p>
  </div>
</details>
{% endfor %}




**... and more to be announced!**  

