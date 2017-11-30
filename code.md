---
layout: post
permalink: /code/index.html
---
<h2>Coding</h2>
<div class="column">
  <ul>
  {% for item in site.code %}
      <li>
        <a href="{{ item.url }}">{{ item.title }}</a>
      </li>
  {% endfor %}
  </ul>
</div>