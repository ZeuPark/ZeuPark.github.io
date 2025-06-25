---
layout: home
author_profile: true
paginate: true
---

{% if paginator.total_pages > 1 %}
  <nav class="pagination" role="navigation">
    {% if paginator.previous_page %}
      <a class="pagination__prev" href="{{ paginator.previous_page_path | relative_url }}">&laquo; Previous</a>
    {% endif %}
    {% if paginator.next_page %}
      <a class="pagination__next" href="{{ paginator.next_page_path | relative_url }}">Next &raquo;</a>
    {% endif %}
  </nav>
{% endif %}
