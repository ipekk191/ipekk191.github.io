---
layout: archive
title: "Fourier Serisi"
---

{{ content }}

{% assign filtered_posts = site.posts
  | where_exp: "post", "post.hidden != true"
  | where_exp: "post", "post.tags contains 'fourier'" %}

<ul class="taxonomy__index">
  {% assign postsInYear = filtered_posts | group_by_exp: 'post', 'post.date | date: "%Y"' %}
  {% for year in postsInYear %}
    <li>
      <a href="#{{ year.name }}">
        <strong>{{ year.name }}</strong>
        <span class="taxonomy__count">{{ year.items | size }}</span>
      </a>
    </li>
  {% endfor %}
</ul>

{% assign entries_layout = page.entries_layout | default: 'list' %}
{% assign postsByYear = filtered_posts | group_by_exp: 'post', 'post.date | date: "%Y"' %}

{% for year in postsByYear %}
  <section id="{{ year.name }}" class="taxonomy__section">
    <h2 class="archive__subtitle">{{ year.name }}</h2>

    <div class="entries-{{ entries_layout }}">
      {% for post in year.items %}
        {% include archive-single.html type=entries_layout %}
      {% endfor %}
    </div>

    <a href="#page-title" class="back-to-top">
      Back to Top ↑
    </a>
  </section>
{% endfor %}
