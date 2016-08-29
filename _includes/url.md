{% if page.url contains '/modules.html' %}
---
[Top](#top)
{% else %}
{{ page.url | inspect }}
{% endif %}
