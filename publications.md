---
layout: default
title: Publications
---

For a full list of publications, please see [Google Scholar](http://scholar.google.nl/citations?user=sApPUZUAAAAJ)

## Machine Translation

My current work focuses on linguistically-informed statistical models for MT. 

<ul class="publications">
{% assign counter=0 %}
{% assign papers = (site.data.papers | where: "topic", "smt") %}
{% for paper in papers %}
 {% include paper.html paper=paper i=counter %}
  {% assign counter=counter | plus:1 %}
{% endfor %}
</ul>


## Entity Linking

I have worked on fast and accurate multilingual models for entity linking.

<ul class="publications">
{% assign papers = (site.data.papers | where: "topic", "entity") %}
{% for paper in papers %}
 {% include paper.html paper=paper i=counter %}
  {% assign counter=counter | plus:1 %}
{% endfor %}
</ul>

## Dependency Parsing

I am also interested in robust models of parsing, with a focus on dependency parsing.

<ul class="publications">
{% assign papers = (site.data.papers | where: "topic", "parsing") %}
{% for paper in papers %}
 {% include paper.html paper=paper i=counter %}
  {% assign counter=counter | plus:1 %}
{% endfor %}
</ul>
