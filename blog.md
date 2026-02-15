---
layout: page
title: "Blog"
permalink: /blog/
---
{% for post in site.posts limit:10 %}
### [{{ post.title }}]({{ post.url | relative_url }})
**{{ post.date | date: "%d %B %Y" }}**
{{ post.excerpt }}
---

{% endfor %}
