---
title: "Research"
layout: page
sitemap: false
permalink: /research/
---

{% assign current_projects = "" | split: "" %}
{% assign past_projects = "" | split: "" %}
{% for page in site.pages %}
  {% if page.url contains '/research/' and page.url != '/research/' and page.name and page.start %}
    {% if page.end %}
      {% assign past_projects = past_projects | push: page %}
    {% else %}
      {% assign current_projects = current_projects | push: page %}
    {% endif %}
  {% endif %}
{% endfor %}

## Current Projects

{% assign sorted_current = current_projects | sort: "start" | reverse %}
{% for p in sorted_current %}
<div class="card mb-3">
  <div class="row g-0">
    <div class="col-md-4 d-flex">
      <img src="{{p.image}}" class="img-fluid rounded-start h-100 object-fit-cover">
  	</div>
   	<div class="col-md-8">
      <div class="card-body">
        <h3 class="card-title">{{p.title}} (since {{p.start}})</h3>
        <p class="card-text">{{p.description}}</p>
        <p><small><a href="{{p.permalink}}">Learn more...</a></small></p>
      </div>
    </div>
  </div>
</div>
{% endfor %}


## Finished Projects

{% assign sorted_past = past_projects | sort: "start" | reverse %}
{% for p in sorted_past %}
<div class="card mb-3">
  <div class="row g-0">
    <div class="col-md-4 d-flex">
      <img src="{{p.image}}" class="img-fluid rounded-start h-100 object-fit-cover">
    </div>
    <div class="col-md-8">
      <div class="card-body">
        <h3 class="card-title">{{p.name}} ({{p.start}} &mdash; {{p.end}})</h3>
        <p class="card-text">{{p.description}}</p>
        <p><small><a href="{{p.permalink}}">Learn more...</a></small></p>
      </div>
    </div>
  </div>
</div>
{% endfor %}
