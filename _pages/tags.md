---
layout: single
title: "Tags"
permalink: /tags/
author_profile: true
---

<style>
  .tag-buttons {
    margin-bottom: 2rem;
  }
  .tag-buttons a {
    display: inline-block;
    margin: 0 0.4rem 0.6rem 0;
    padding: 0.4rem 0.8rem;
    background-color: #f2f2f2;
    color: #333;
    text-decoration: none;
    border-radius: 6px;
    font-size: 0.9rem;
    transition: background-color 0.2s ease;
  }
  .tag-buttons a:hover {
    background-color: #e2e2e2;
  }

  .tag-section {
    margin-bottom: 3rem;
  }

  .tag-section h2 {
    color: #2c3e50;
    border-bottom: 1px solid #ccc;
    padding-bottom: 0.3rem;
    margin-bottom: 0.8rem;
  }

  .tag-section ul {
    list-style-type: disc;
    padding-left: 1.5rem;
  }
</style>

<!-- 상단 태그 버튼 출력 -->
<div class="tag-buttons">
  {% assign sorted_tags = site.tags | sort %}
  {% for tag in sorted_tags %}
    <a href="#{{ tag[0] | slugify }}">#{{ tag[0] }}</a>
  {% endfor %}
</div>

<!-- 태그별 글 목록 -->
{% for tag in sorted_tags %}
  <div class="tag-section" id="{{ tag[0] | slugify }}">
    <h2>#{{ tag[0] }}</h2>
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
