---
layout: page
title: projects
permalink: /projects/
description: A collection of projects I've built over the years, spanning my academic studies, research and personal interests.
nav: true
nav_order: 3
---

<style>
.proj-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(250px, 1fr)); gap: 1.5rem; margin-top: 1.5rem; }
.proj-card { position: relative; display: flex; flex-direction: column; height: 100%; overflow: hidden; }
.proj-card figure { margin: 0; }
.proj-card .card-img-top { display: block; width: 100%; height: 175px; object-fit: cover; object-position: center top; }
.proj-body { display: flex; flex-direction: column; flex: 1; padding: 1.25rem 1.25rem 1rem; }
.proj-title { margin: 0.25rem 0 0.9rem; font-size: 1.7rem; line-height: 1.2; }
.proj-title a { color: var(--global-text-color); text-decoration: none; }
.proj-title a:hover { color: var(--global-theme-color); }
.proj-title a::after { content: ""; position: absolute; inset: 0; z-index: 1; }
.proj-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; margin-bottom: 0.9rem; }
.proj-tag { padding: 0.2rem 0.7rem; border-radius: 999px; font-size: 0.78rem; background: rgba(0, 0, 0, 0.05); color: #4f7cac; }
html[data-theme="dark"] .proj-tag { background: rgba(255, 255, 255, 0.1); color: #8db4e2; }
.proj-desc { margin: 0 0 1rem; }
.proj-gh { position: relative; z-index: 2; margin-top: auto; font-size: 1.1rem; color: var(--global-theme-color); }
.proj-gh:hover { color: var(--global-hover-color); }
</style>

{% assign sorted_projects = site.projects | sort: "importance" -%}
<div class="projects proj-grid">
{%- for project in sorted_projects %}
<div class="proj-card card hoverable">
{%- if project.img %}
{% include figure.liquid loading="eager" path=project.img sizes="250px" alt="project thumbnail" class="card-img-top" %}
{%- endif %}
<div class="proj-body">
<h2 class="proj-title"><a href="{% if project.redirect %}{{ project.redirect }}{% else %}{{ project.url | relative_url }}{% endif %}">{{ project.title }}</a></h2>
{%- if project.tags and project.tags.size > 0 %}
<div class="proj-tags">{% for tag in project.tags %}<span class="proj-tag">{{ tag }}</span>{% endfor %}</div>
{%- endif %}
<p class="proj-desc">{{ project.description }}</p>
{%- if project.github %}
<a class="proj-gh" href="{{ project.github }}" target="_blank" rel="noopener" title="Code repository" aria-label="Code repository"><i class="fa-brands fa-github"></i></a>
{%- endif %}
</div>
</div>
{%- endfor %}
</div>
