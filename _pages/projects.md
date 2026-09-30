---
layout: page
title: projects
permalink: /projects/
description: Research code and computational projects. More on <a href="https://github.com/DilanKaraguler">GitHub</a>.
nav: true
nav_order: 3
horizontal: false
---

<!-- Project cards come from the files in _projects/ -->
{% assign sorted_projects = site.projects | sort: "importance" %}

<div class="projects">
  <div class="row row-cols-1 row-cols-md-3">
  {% for project in sorted_projects %}
    {% include projects.liquid %}
  {% endfor %}
  </div>
</div>
