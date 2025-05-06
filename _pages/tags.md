---
layout: single
title: "Tags"
permalink: /tags/
author_profile: true
---

<style>
  .tag-section { margin-bottom: 2rem; }
  .tag-section h2 { margin-bottom: 0.5rem; color: #2c3e50; }
  .tag-section ul { padding-left: 1.2rem; }
</style>

{% assign sorted_tags = site.tags | sort %}
{% for tag in sorted_tags %}
  <div class="tag-section">
    <h2 id="{{ tag[0] | slugify }}">#{{ tag[0] }}</h2>
    <ul>
      {% for post in tag[1] %}
        <li>
          <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
          <small>({{ post.date | date: "%Y-%m-%d" }})</small>
        </li>
      {% endfor %}
    </ul>
  </div>
{% endfor %}
