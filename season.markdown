---
title: Shows
date: 2016-11-03 19:38:00 Z
---

<ul>
{% for show in site.shows %}
  <li>
    <ul>
      <li>Name: {{ show.title }}</li>
      <li>Director: {{ show.director }}</li>
    </ul>
  </li>
{% endfor %}
</ul>