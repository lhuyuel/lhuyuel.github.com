---
layout: page
title: <h4>while( attempt() != succeed );</h4>
tagline: 
---
{% include JB/setup %}

<ul class="posts">
<h2 >Latest 10 Posts </h2>
  {% for post in site.posts limit:10 %}
  <li><span class="post_date">{{ post.date | date: "%B %e, %Y" }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>

  {% endfor %}
</ul>



