---
layout: page
title:  while( attempt() != succeed );
tagline: 
---
{% include JB/setup %}
<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-41433712-1', 'github.com');
  ga('send', 'pageview');

</script>

<h3>Latest Posts </h3>
<ul class="posts">

  {% for post in site.posts limit:25 %}
  <li><span class="post_date">{{ post.date | date: "%B %e, %Y" }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>

  {% endfor %}
</ul>



