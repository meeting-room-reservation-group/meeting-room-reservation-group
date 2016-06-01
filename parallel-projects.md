---
layout: page
title: Parallel Projects
permalink: /parallel-projects/
---
Developers who follow this group and have created their own GitHub git project, that implements the _Meeting Room Reservation Services_ are shown here. This makes sharing solutions and idea easier. Or showing other framework / libraries etc.

<ul>
{% for project in site.data.parallel-projects %}
  <li>
    <a href="https://github.com/{{ project.member }}">
      {{ project.repo }}
    </a>
  </li>
{% endfor %}
</ul>

