# _pages/tags-custom.md
---
title: "All Tags"
layout: collection
permalink: /tags/
---

{% capture tags %}
  {% for tag in site.tags %}
    <a href="#{{ tag[0] | slugify }}"><h2>#{{ tag[0] }}</h2></a>
  {% endfor %}
{% endcapture %}

{{ tags }}

---

{% for tag in site.tags %}
  <h2 id="{{ tag[0] | slugify }}">#{{ tag[0] }}</h2>
  <ul>
    {% for post in tag[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
