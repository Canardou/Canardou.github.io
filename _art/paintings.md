---
layout: carousel
title:  "Paintings"
date: 2017-12-09
lang: eng
---
<h2>Paintings</h2>
<div id="slider" class="flexslider">
    <ul class="slides"> 
{% for image in site.static_files %}{% if image.path contains 'images/paintings' %}
    <li>
        <img src="{{ site.baseurl }}{{ image.path }}" alt="image" />
    </li>
{% endif %}{% endfor %}
    </ul>
</div>

<div id="carousel" class="flexslider">
    <ul class="slides"> 
{% for image in site.static_files %}{% if image.path contains 'images/paintings' %}
    <li>
        <img src="{{ site.baseurl }}{{ image.path }}" alt="image" />
    </li>
{% endif %}{% endfor %}
    </ul>
</div>