---
layout: default
title: Projects
---

## Projects

These are the projects that students will be working towards completing in their lessons. Each lesson has as its aim the completion of a specific part/task of a larger project.  For each lesson the student will work with their assigned pair except for the final project, in which they will be able to select their own team.

 ==============================

<div id="home">
  <ul class="posts">
    {% for post in site.posts reversed %}
	    {% if post.categories contains 'project' %}
	      <li> &raquo; <a href="{{ site.baseurl}}{{ post.url }}">{{ post.title }}</a></li>
	    {% endif %}
    {% endfor %}
  </ul>
</div>