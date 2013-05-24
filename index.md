---
layout: page
title: Yue Hu
tagline: 
---
{% include JB/setup %}
<h3>Latest 10 Posts </h3>
<ul class="posts">

  {% for post in site.posts limit:10 %}
  <li><span class="post_date">{{ post.date | date: "%B %e, %Y" }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>

  {% endfor %}
</ul>



