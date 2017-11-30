---
layout: post
permalink: /blog/index.html
---
<h2>Blog Posts</h2>
<div class="column">
    <ul style="list-style: none;padding: 0;margin-left: 0;text-align: center;">
    {% for item in site.posts %}
      <li><time>{{ item.date | date_to_string }}</time> <a href="{{ item.url }}">{{ item.title }}</a> </li>
    {% endfor %}
    </ul>
</div>