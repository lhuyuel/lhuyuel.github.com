---
layout: page
title: Latest 10 Posts 
tagline: 
---
{% include JB/setup %}

<ul class="posts">

  {% for post in site.posts limit:10 %}
  <li><span class="post_date">{{ post.date | date: "%B %e, %Y" }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>

  {% endfor %}
</ul>



