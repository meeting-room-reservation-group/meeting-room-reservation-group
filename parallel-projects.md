---
layout: page
title: Parallel Projects
permalink: /parallel-projects/
---
Developers who follow this group and have created their own GitHub git project, that implements the _Meeting Room Reservation System_ are shown here. This makes sharing solutions and idea easier. Or showing other framework / libraries etc.

<table>
  <tr>
    <th>User</th>
    <th>Repository</th>
  </tr>
{% for project in site.data.projects %}
  <tr>
    <td>
      <a href="https://github.com/{{ project.member }}">
        {{ project.member }}
      </a>
    </td>
    <td>
      <a href="https://github.com/{{ project.member }}/{{ project.repo }}">
        {{ project.repo }}
      </a>
    </td>
  </tr>
{% endfor %}
</table>

