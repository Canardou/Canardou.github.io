---
layout: post
permalink: /art/index.html
---
<h2>Art Stuff</h2>
<div class="column">
  <ul>
  {% for item in site.art %}
      <li>
        <a href="{{ item.url }}">{{ item.title }}</a>
      </li>
  {% endfor %}
  </ul>
</div>