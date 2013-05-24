---
layout: page
title: Power Leveling
tagline: 
---
{% include JB/setup %}
<h2>Latest 10 Posts </h2>
<ul class="posts">

  {% for post in site.posts limit:10 %}
  <li><span class="post_date">{{ post.date | date: "%B %e, %Y" }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>

  {% endfor %}
</ul>



