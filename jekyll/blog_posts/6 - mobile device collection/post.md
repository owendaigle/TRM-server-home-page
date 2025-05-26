---
layout: post
title: Mobile Device Collection
post_date: 2025/02/23
update_date: 2025/05/25
topic: Collection
author: Owen Daigle

---


This is a list of many of the mobile devices I have.

This includes but is not limited to: 

- Phones
- Tablets

{% assign sorted_pages = site.pages | sort: 'device_year' | reverse %}

{% for device in sorted_pages %}
{% if device.url contains "/blog_posts/" %}
{% if device.url contains ".dev.html" %}


{% if device.specsheet_version == 1 %}

# {{ device.device_name }}

{% if device.device_GSM_LNK != null %}
I own {{device.device_quantity}} [{{ device.device_name }}(s)]({{ device.device_GSM_LNK }}) that are {{ device.device_colours}}.

{% else %}
I own {{device.device_quantity}} {{ device.device_name }}(s) that are {{ device.device_colours}}.

    
{% endif %}


{{ device.device_description }}

    {% if device.device_picture_file_name != null %}
<img src="{{ device.device_picture_file_name }}" width="40%">
    
    {% endif %}
  
<table>
    <thead>
    <tr>
        <th>Specification</th>
        <th>Value</th>
    </tr>
    </thead>
    <tbody>
    {% assign specs = "" %} 

    {% if device.device_model != null %}
        {% assign specs = specs | append: "<tr><td>Model</td><td>" | append: device.device_model | append: "</td></tr>" %}
    {% endif %}

    {% if device.device_codename != null %}
        {% assign specs = specs | append: "<tr><td>Codename</td><td>" | append: device.device_codename | append: "</td></tr>" %}
    {% endif %}

    {% if device.device_year != null %}
        {% assign specs = specs | append: "<tr><td>Year</td><td>" | append: device.device_year | append: "</td></tr>" %}
    {% endif %}

    {% if device.device_shipped_android_version != null %}
        {% assign specs = specs | append: "<tr><td>Shipped Android Version</td><td>" | append: device.device_shipped_android_version | append: "</td></tr>" %}
    {% endif %}

    {% if device.device_latest_official_android_version != null %}
        {% assign specs = specs | append: "<tr><td>Latest Android Version</td><td>" | append: device.device_latest_official_android_version | append: "</td></tr>" %}
    {% endif %}

    {% if device.device_chipset != null %}
        {% assign specs = specs | append: "<tr><td>Chipset</td><td>" | append: device.device_chipset | append: "</td></tr>" %}
    {% endif %}

    {% if device.device_memory != null %}
        {% assign specs = specs | append: "<tr><td>RAM</td><td>" | append: device.device_memory | append: "</td></tr>" %}
    {% endif %}

    {% if device.device_battery != null %}
        {% assign specs = specs | append: "<tr><td>Battery Capacity</td><td>" | append: device.device_battery | append: "</td></tr>" %}
    {% endif %}

    {% if device.device_screen_size != null %}
        {% assign specs = specs | append: "<tr><td>Screen Size</td><td>" | append: device.device_screen_size | append: "</td></tr>" %}
    {% endif %}

    {% if device.device_screen_resolution != null %}
        {% assign specs = specs | append: "<tr><td>Screen Resolution</td><td>" | append: device.device_screen_resolution | append: "</td></tr>" %}
    {% endif %}

    {% if device.device_screen_technology != null %}
        {% assign specs = specs | append: "<tr><td>Screen Technology</td><td>" | append: device.device_screen_technology | append: "</td></tr>" %}
    {% endif %}

    {% if device.device_front_camera != null %}
        {% assign specs = specs | append: "<tr><td>Front Camera</td><td>" | append: device.device_front_camera | append: "</td></tr>" %}
    {% endif %}

    {% if device.device_rear_camera_main != null %}
        {% assign specs = specs | append: "<tr><td>Main Rear Camera</td><td>" | append: device.device_rear_camera_main | append: "</td></tr>" %}
    {% endif %}

    {% if device.device_rear_camera_wide != null %}
        {% assign specs = specs | append: "<tr><td>Wide Rear Camera</td><td>" | append: device.device_rear_camera_wide | append: "</td></tr>" %}
    {% endif %}

    {% if device.device_rear_camera_other != null %}
        {% assign specs = specs | append: "<tr><td>Other Rear Camera</td><td>" | append: device.device_rear_camera_other | append: "</td></tr>" %}
    {% endif %}

    

    {{ specs }} 

    </tbody>
</table>


{% endif %}

{% endif %}
{% endif %}
{% endfor %}

