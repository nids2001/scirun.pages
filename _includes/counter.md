<script type= "text/javascript">
</script>

### Contents
{% assign num = 1 %}
{% assign chapters = page | split '## ' %}
{% for ch in chapters %}
  <a href='#'>{{ num++ }} {{ ch[0]}}</a>\n
  {% assign submodules = ch | split '### %}
  {% assign snum = 0 %}
  {% for sm in submodules %}
    <a href='#'>{{num}}.{{ snum++ }} {{ sm[0]}}</a>\n
  {% endfor%}
{% endfor %}
