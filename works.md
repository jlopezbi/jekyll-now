---
layout: default
---

{% for work in site.works %}
<div class="work">
{{ work.content }}
{% endfor %}
