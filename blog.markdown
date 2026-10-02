---
layout: single
title: Blog
permalink: /blog/
---

{% for post in site.posts %}
### [{{ post.title }}]({{ post.url | relative_url }})
<p style="color: #6B665B; font-size: 14px;">{{ post.date | date: "%B %-d, %Y" }}</p>

{{ post.excerpt }}

---
{% endfor %}