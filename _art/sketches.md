---
layout: post
title:  "Sketches"
date: 2017-12-09
lang: eng
---
<h2>Sketches</h2>
<div class="column">
{% for image in site.static_files %}
    {% if image.path contains 'images/sketches' %}
    <p>
        <img src="{{ site.baseurl }}{{ image.path }}" alt="image" />
    </p>
    {% endif %}
{% endfor %}
</div>
