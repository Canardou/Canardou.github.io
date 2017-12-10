---
layout: post
permalink: /boardgame/index.html
---
<h2>Boardgame</h2>
<div class="column">
  <ul>
  {% for item in site.boardgame %}
      <li>
        <a href="{{ item.url }}">{{ item.title }}</a>
      </li>
  {% endfor %}
  </ul>
</div>