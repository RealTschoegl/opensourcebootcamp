---
layout: default
title: Mini-Lessons
---

## Mini-Lessons

These mini-lesson are to be included in regular lessons when educationally appropriate or time permits.  They can also be taught on their own as extra modules for those students who want extra content.  Alternatively, students can teach  the content of a lesson to their fellow students in a presentation.

 ==============================

<div id="home">
  <ul class="posts">
    {% for post in site.posts reversed %}
	    {% if post.categories contains 'mini-lesson' %}
	      <li> &raquo; <a href="{{ site.baseurl}}{{ post.url }}">{{ post.title }}</a></li>
	    {% endif %}
    {% endfor %}
  </ul>
</div>