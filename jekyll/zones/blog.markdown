---
layout: base
title: Owen's Website
pgtitle: Blog
---


# This is my blog. 

I will post about basically whatever I am working on, and cool stuff that I am doing. 

{% assign sorted_pages = site.pages | sort: 'order' %}

{% for page in sorted_pages %}
{% if page.url contains "/blog_posts/" %}
{% if page.url contains "post.html" %}
[{{ page.title }}]({{ page.url }})
{% endif %}
{% endif %}
{% endfor %}