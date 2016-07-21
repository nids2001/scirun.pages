---
{% assign relative-baseurl = "" %}
{% assign canon = page.url | append: "page.html" | split: "/" %}
{% for item in canon offset:2 %}
  {% assign relative-baseurl = relative-baseurl | append:"../" %}
{% endfor %}
[SCIRun Modules]({{ relative-baseurl }}module.html)
