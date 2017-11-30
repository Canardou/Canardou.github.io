---
layout: post
permalink: /rpg/index.html
---
<h2>Role Playing</h2>
<div class="column">
  <ul>
  {% for item in site.rpg %}
      <li>
        <a href="{{ item.url }}">{{ item.title }}</a>
      </li>
  {% endfor %}
  </ul>
</div>