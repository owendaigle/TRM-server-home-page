---
layout: post
title: Computer Collection
post_date: 2025/02/17
update_date: 2025/05/25
topic: Collection
author: Owen Daigle

---

This is a list of many of the computers I have as well as their purpose, and why I have them.

I am always tinkering with some computer or another, so odds are this list will never be fully up to date for some reason or another. 

{% assign sorted_pages = site.pages | sort: 'priority' | reverse %}

{% for computer in sorted_pages %}
{% if computer.url contains "/blog_posts/" %}
{% if computer.url contains ".pc.html" %}


{% if computer.specsheet_version == 1 %}

# {{ computer.device_name }}

{% if computer.device_picture_file_name != null %}
<img src="{{ computer.device_picture_file_name }}" width="50%">
{% endif %}

{{ computer.device_description }}

<table>
    <thead>
    <tr>
        <th>Specification</th>
        <th>Value</th>
    </tr>
    </thead>
    <tbody>
    {% assign specs = "" %} 

    {% if computer.device_operating_system != null %}
        {% assign specs = specs | append: "<tr><td>OS</td><td>" | append: computer.device_operating_system | append: "</td></tr>" %}
    {% endif %}

    {% if computer.device_model != null %}
        {% assign specs = specs | append: "<tr><td>Device Model</td><td>" | append: computer.device_model | append: "</td></tr>" %}
    {% endif %}

    {% if computer.device_cpu != null %}
        {% assign specs = specs | append: "<tr><td>CPU</td><td>" | append: computer.device_cpu | append: "</td></tr>" %}
    {% endif %}

    {% if computer.device_cpu_cooler != null %}
        {% assign specs = specs | append: "<tr><td>CPU Cooler</td><td>" | append: computer.device_cpu_cooler | append: "</td></tr>" %}
    {% endif %}

    {% if computer.device_ram_capacity != null %}
        {% assign specs = specs | append: "<tr><td>RAM Capacity</td><td>" | append: computer.device_ram_capacity | append: "</td></tr>" %}
    {% endif %}

    {% if computer.device_ram_speed != null %}
        {% assign specs = specs | append: "<tr><td>RAM Speed</td><td>" | append: computer.device_ram_speed | append: "</td></tr>" %}
    {% endif %}

    {% if computer.device_motherboard != null %}
        {% assign specs = specs | append: "<tr><td>Motherboard</td><td>" | append: computer.device_motherboard | append: "</td></tr>" %}
    {% endif %}

    {% if computer.device_psu != null %}
        {% assign specs = specs | append: "<tr><td>Power Supply</td><td>" | append: computer.device_psu | append: "</td></tr>" %}
    {% endif %}

    {% if computer.device_case != null %}
        {% assign specs = specs | append: "<tr><td>Computer Case</td><td>" | append: computer.device_case | append: "</td></tr>" %}
    {% endif %}

    {% if computer.device_gpu1 != null %}
        {% assign specs = specs | append: "<tr><td>Primary GPU</td><td>" | append: computer.device_gpu1 | append: "</td></tr>" %}
    {% endif %}

    {% if computer.device_gpu2 != null %}
        {% assign specs = specs | append: "<tr><td>Secondary GPU</td><td>" | append: computer.device_gpu2 | append: "</td></tr>" %}
    {% endif %}

    {% if computer.device_main_storage != null %}
        {% assign specs = specs | append: "<tr><td>Primary Storage</td><td>" | append: computer.device_main_storage | append: "</td></tr>" %}
    {% endif %}

    {% if computer.device_secondary_storage != null %}
        {% assign specs = specs | append: "<tr><td>Secondary Storage</td><td>" | append: computer.device_secondary_storage | append: "</td></tr>" %}
    {% endif %}

    {% if computer.device_odd != null %}
        {% assign specs = specs | append: "<tr><td>Optical Disk Drive</td><td>" | append: computer.device_odd | append: "</td></tr>" %}
    {% endif %}

    {% if computer.device_primary_display != null %}
        {% assign specs = specs | append: "<tr><td>Primary Display</td><td>" | append: computer.device_primary_display | append: "</td></tr>" %}
    {% endif %}

    {% if computer.device_secondary_display != null %}
        {% assign specs = specs | append: "<tr><td>Secondary Display</td><td>" | append: computer.device_secondary_display | append: "</td></tr>" %}
    {% endif %}

    {{ specs }} 

    </tbody>
</table>

{% endif %}

{% endif %}
{% endif %}
{% endfor %}

