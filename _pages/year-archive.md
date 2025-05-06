---
title: "Posts"
layout: single
permalink: /year-archive/
author_profile: true
---

<style>
  .archive-section { margin-bottom: 2rem; }
  .archive-section h2, .archive-section h3 {
    margin-bottom: 0.3rem;
    color: #2c3e50;
  }
  .archive-section ul {
    padding-left: 1.5rem;
    margin-bottom: 1.5rem;
  }
</style>

{% assign posts_by_year = site.posts | group_by_exp:"post", "post.date | date: '%Y'" %}
{% for year in posts_by_year %}
  <div class="archive-section">
    <h2>{{ year.name }}</h2>

    {% assign posts_by_month = year.items | group_by_exp:"post", "post.date | date: '%B'" %}
    {% for month in posts_by_month %}
      <h3>{{ month.name }}</h3>
      <ul>
        {% for post in month.items %}
          <li>
            <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
            <small>({{ post.date | date: "%Y-%m-%d" }})</small>
          </li>
        {% endfor %}
      </ul>
    {% endfor %}
  </div>
{% endfor %}
