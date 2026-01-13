---
layout: page
title: "Fourier Serisi"
---

Bu sayfada **Fourier Serisi** kapsamındaki tüm yazıları bulabilirsin.

<ul>
  {% for post in site.tags.fourier %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
