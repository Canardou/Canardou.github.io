---
layout: post
permalink: /projects/index.html
---
<h2>Projects</h2>
<div class="column">
  <ul>
  {% for item in site.projects %}
      <li>
        <a href="{{ item.url }}">{{ item.title }}</a>
      </li>
  {% endfor %}
  </ul>
</div>