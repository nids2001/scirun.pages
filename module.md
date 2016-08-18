---
title: SCIRun Module Documentation
category: info
tags: module
---

<link rel="stylesheet" href="css/modest.css">

# SCIRun Modules

{% comment %}from https://gist.github.com/pepelsbey/9334494{% endcomment %}
{% capture tmp %}
{% for page in site.pages %}{% if page.category == "moduledocs" %} {{ page.module.category }} {% endif %}{% endfor %}
{% endcapture %}

{% assign categories = tmp | split: ' ' %}
{% assign tmp = categories[0] %}

{% for cat in categories %}
  {% unless tmp contains cat %}
    {% capture tmp %}{{ tmp }} {{ cat }}{% endcapture %}
  {% endunless %}
{% endfor %}

{% assign modulecategories = tmp | split: ' ' %}

{% capture modulepages %}{% for cat in modulecategories %}?{{ cat }}{% for page in site.pages %}{% if page.module.category == cat %}${{ page.title }}#{{ page.url | prepend: site.github.url }}{% endif %}{% endfor %}{% endfor %}{% endcapture %}

{% assign sortedpages = modulepages | strip | strip_newlines | split: '?' | sort %}

{% for pagestring in sortedpages %}
  {% assign pageitems = pagestring | split: '$' %}
  {% if pageitems[0] %}
## {{ pageitems[0] }}
    {% for item in pageitems %}
      {% comment %}skip category list item (index 0){% endcomment %}
      {% if forloop.first %} {% continue %} {% endif %}
      {% assign linkitem = item | split: '#' %}
      {% capture my-include %}{% include linkitem[1] %}{% endcapture %}
      **[{{ linkitem[0] }}]({{ linkitem[1] }}){:target="_blank"}**
    {% endfor %}
  {% endif %}
{% endfor %}
