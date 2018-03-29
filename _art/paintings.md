---
layout: post
title:  "Paintings"
date: 2017-12-09
lang: eng
---
<h2>Paintings</h2>
<div class="column">
{% for image in site.static_files %}
    {% if image.path contains 'images/paintings' %}
    <p>
        <img src="{{ site.baseurl }}{{ image.path }}" alt="image" />
    </p>
    {% endif %}
{% endfor %}
</div>
