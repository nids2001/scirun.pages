---
title: SCIRun Module Documentation
category: info
tags: module
---

<link rel="stylesheet" href="css/modest.css">

<script type="text/javascript">
<!--
    function toggle_visibility(id) {
       var e = document.getElementsByName(id)[0];
       if(e.style.display == 'block')
          e.style.display = 'none';
       else
          e.style.display = 'block';
    }
//-->
</script>

# SCIRun Modules

{% comment %}from https://gist.github.com/pepelsbey/9334494{% endcomment %}
{% capture tmp %}
  {% for page in site.pages %}
    {% if page.category == "moduledocs" %}
      {{ page.module.category }}
    {% endif %}
  {% endfor %}
{% endcapture %}

{% assign categories = tmp | split: ' ' %}
{% assign tmp = categories[0] %}

{% for cat in categories %}
  {% unless tmp contains cat %}
    {% capture tmp %}{{ tmp }} {{ cat }}{% endcapture %}
  {% endunless %}
{% endfor %}

{% assign modulecategories = tmp | split: ' ' %}

{% capture modulepages %}
  {% for cat in modulecategories %}
    ?{{ cat }}
    {% for page in site.pages %}
      {% if page.module.category == cat %}
        ${{ page.title }}#{{ page.url }}
      {% endif %}
    {% endfor %}
  {% endfor %}
{% endcapture %}

{% assign sortedpages = modulepages | strip | strip_newlines | split: '?' | sort %}

{% for pagestring in sortedpages %}
  {% assign pageitems = pagestring | split: '$' %}
  {% if pageitems[0] %}
## {{ pageitems[0] }}
    {% for item in pageitems %}
      {% comment %}skip category list item (index 0){% endcomment %}
      {% if forloop.first %} {% continue %} {% endif %}
      {% assign linkitem = item | split: '#' %}
**{{ linkitem[0] }}**
      <br><a href="#" onclick="toggle_visibility('{{ linkitem[0] }}');"> {{ linkitem[0] }} </a>
      {% capture mdpath %}SCIRunModules/{{linkitem[0]}}.md{% endcapture %}
      {% capture my-include %}{% include_relative {{mdpath}} %}{% endcapture %}

      {{ my-include }}

    {% endfor %}
  {% endif %}
{% endfor %}
