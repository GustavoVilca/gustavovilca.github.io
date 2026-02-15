---
layout: page
title: "Blog"
permalink: /blog/
---

<ul>
  {% for post in site.posts limit:10 %}
    <li>
      <span>{{ post.date | date: "%Y-%m-%d" }}</span>
      — <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

<p><a href="{{ '/feed.xml' | relative_url }}">RSS</a></p>
