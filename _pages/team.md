---
title: "KIZ: Team"
layout: team
excerpt: "KIZ: Team members"
sitemap: false
permalink: /team/
---

# Group Members


## Research Staff

{% for member in site.data.staff_scientific %}
<div class="card mb-3 w-100"  {% if member.alias %}id="{{ member.alias }}"{% endif %}>
  <div class="row g-0" >
    <div class="col-md-3 d-flex">
      <img src="/images/team/{{ member.photo }}" class="img-fluid rounded-start w-100 h-100 object-fit-cover" alt="...">
    </div>
    <div class="col-md-9">
      <div class="card-body">
        <h5 class="card-title">
          {{ member.name }}
          {% if member.twitter %}
          <a href="https://twitter.com/{{member.twitter}}"><i class="fa-brands fa-twitter"></i></a>
          {% endif %}
          {% if member.gscholar %}
          <a href="https://scholar.google.de/citations?user={{member.gscholar}}"><i class="fa-brands fa-google-scholar"></i></a>
          {% endif %}
          {% if member.orcid %}
          <a href="https://orcid.org/{{member.orcid}}"><i class="fa-brands fa-orcid"></i></a>
          {% endif %}
          {% if member.arxiv %}
          <a href="https://arxiv.org/a/{{member.arxiv}}.html"><img src="/images/arxiv-logo.svg" style="display: inline-block; height: 1em;"></a>
          {% endif %}
        </h5>
        <p class="card-text">{{ member.info }}</p>
        {% if member.subject %}
        <p class="card-text"><i class="fa-solid fa-graduation-cap"></i> {{ member.subject }}</p>
        {% endif %}
        <p class="card-text">
          <small class="text-body-secondary"><i class="fa-solid fa-envelope"></i> {{ member.email }}
          {% if member.pgp %}
            <br/><i class="fa-solid fa-key"></i> <a href="https://keys.openpgp.org/vks/v1/by-fingerprint/{{member.pgp}}" target="_blank">{{ member.pgp }}</a>
          {% endif %}
          </small>
        </p>
        {% if member.alias %}
          {% assign thesis_count = 0 %}
          {% for page in site.pages %}
            {% if page.url contains '/open-theses/' %}
              {% assign is_advisor = false %}
              <!-- Check if member is listed as advisor in this thesis -->
              {% if page.advisor %}
                {% if page.advisor.first %}
                  <!-- Advisor is an array -->
                  {% if page.advisor contains member.alias %}
                    {% assign is_advisor = true %}
                  {% endif %}
                {% else %}
                  <!-- Advisor is a single value -->
                  {% if page.advisor == member.alias %}
                    {% assign is_advisor = true %}
                  {% endif %}
                {% endif %}
              {% endif %}
              {% if is_advisor %}
                {% assign thesis_count = thesis_count | plus: 1 %}
              {% endif %}
            {% endif %}
          {% endfor %}
          {% if thesis_count > 0 %}
            <p class="card-text"><strong>Open thesis topics:</strong></p>
            <ul>
            {% for page in site.pages %}
              {% if page.url contains '/open-theses/' %}
                {% assign is_advisor = false %}
                <!-- Check if member is listed as advisor in this thesis -->
                {% if page.advisor %}
                  {% if page.advisor.first %}
                    <!-- Advisor is an array -->
                    {% if page.advisor contains member.alias %}
                      {% assign is_advisor = true %}
                    {% endif %}
                  {% else %}
                    <!-- Advisor is a single value -->
                    {% if page.advisor == member.alias %}
                      {% assign is_advisor = true %}
                    {% endif %}
                  {% endif %}
                {% endif %}
                {% if is_advisor %}
                  <li><a href="{{ page.url | relative_url }}">{{ page.title }}</a></li>
                {% endif %}
              {% endif %}
            {% endfor %}
            </ul>
          {% endif %}
        {% endif %}
        <!-- Display projects: combines projects from YAML data and automatically discovered from project pages -->
        {% if member.alias or member.project %}
          {% assign all_projects = "" | split: "" %}

          <!-- Step 1: Add projects from staff_scientific.yml -->
          {% if member.project %}
            <!-- Handle both single value and array -->
            {% if member.project.first %}
              {% for p in member.project %}
                {% assign all_projects = all_projects | push: p %}
              {% endfor %}
            {% else %}
              {% assign all_projects = all_projects | push: member.project %}
            {% endif %}
          {% endif %}

          <!-- Step 2: Auto-discover projects by scanning project pages for this member's alias -->
          {% if member.alias %}
            {% for page in site.pages %}
              <!-- Only process project pages under /research/ -->
              {% if page.url contains '/research/' and page.url != '/research/' %}
                {% assign is_advisor = false %}
                {% assign is_staff = false %}

                <!-- Check if member is listed as advisor in this project -->
                {% if page.advisor %}
                  {% if page.advisor.first %}
                    <!-- Advisor is an array -->
                    {% if page.advisor contains member.alias %}
                      {% assign is_advisor = true %}
                    {% endif %}
                  {% else %}
                    <!-- Advisor is a single value -->
                    {% if page.advisor == member.alias %}
                      {% assign is_advisor = true %}
                    {% endif %}
                  {% endif %}
                {% endif %}

                <!-- Check if member is listed as staff in this project -->
                {% if page.staff %}
                  {% if page.staff contains member.alias %}
                    {% assign is_staff = true %}
                  {% endif %}
                {% endif %}

                <!-- If member is involved, extract project slug from URL and add to list -->
                {% if is_advisor or is_staff %}
                  {% assign url_parts = page.url | split: "/" %}
                  {% if url_parts[2] %}
                    {% assign project_slug = url_parts[2] %}
                    <!-- Only add if not already in the list (avoid duplicates) -->
                    {% unless all_projects contains project_slug %}
                      {% assign all_projects = all_projects | push: project_slug %}
                    {% endunless %}
                  {% endif %}
                {% endif %}
              {% endif %}
            {% endfor %}
          {% endif %}

          <!-- Display all collected projects -->
          {% if all_projects.size > 0 %}
            <p class="card-text"><i class="fa-solid fa-screwdriver-wrench"></i>
              {% for p in all_projects %}
                <a href="/research/{{ p }}/">{{ p }}</a>{% if forloop.last == false %}, {% endif %}
              {% endfor %}
            </p>
          {% endif %}
        {% endif %}
      </div>
    </div>
  </div>
</div>
{% endfor %}


## Administrative Support

{% for member in site.data.staff_admin %}
<div class="card mb-3 w-100">
  <div class="row g-0">
    <div class="col-md-3 d-flex">
      <img src="/images/team/{{ member.photo }}" class="img-fluid rounded-start w-100 h-100 object-fit-cover" alt="...">
    </div>
    <div class="col-md-9">
      <div class="card-body">
        <h5 class="card-title">{{ member.name }}</h5>
        <p class="card-text">
          {{ member.info }}
          {% if member.twitter %}
          <a href="https://twitter.com/{{member.twitter}}"><i class="fa-brands fa-twitter"></i></a>
          {% endif %}
        </p>
        <p class="card-text">
          <small class="text-body-secondary"><i class="fa-solid fa-envelope"></i> {{ member.email }}
          {% if member.pgp %}
            <br/><i class="fa-solid fa-key"></i> <a href="https://keys.openpgp.org/vks/v1/by-fingerprint/{{member.pgp}}" target="_blank">{{ member.pgp }}</a>
          {% endif %}
          </small>
        </p>
      </div>
    </div>
  </div>
</div>
{% endfor %}


## Alumni

{% for member in site.data.alumni %}
<div class="card mb-3 w-100">
  <div class="row g-0">
    <div class="col-md-3 d-flex">
      <img src="/images/team/{{ member.photo }}" class="img-fluid rounded-start w-100 h-100 object-fit-cover" alt="...">
    </div>
    <div class="col-md-9">
      <div class="card-body">
        <h5 class="card-title">
          {% if member.link %}
          <a target="_blank" href="{{ member.link }}">{{ member.name }}</a>
          {% else %}
          {{ member.name }}
          {% endif %}
          {% if member.twitter %}
          <a href="https://twitter.com/{{member.twitter}}"><i class="fa-brands fa-twitter"></i></a>
          {% endif %}
          {% if member.gscholar %}
          <a href="https://scholar.google.de/citations?user={{member.gscholar}}"><i class="fa-brands fa-google-scholar"></i></a>
          {% endif %}
          {% if member.orcid %}
          <a href="https://orcid.org/{{member.orcid}}"><i class="fa-brands fa-orcid"></i></a>
          {% endif %}
          {% if member.arxiv %}
          <a href="https://arxiv.org/a/{{member.arxiv}}.html"><img src="/images/arxiv-logo.svg" style="display: inline-block; height: 1em;"></a>
          {% endif %}
        </h5>
        <p class="card-text">{{ member.info }}</p>
        <p class="card-text">
          <small class="text-body-secondary"><i class="fa-solid fa-envelope"></i> {{ member.email }}
          {% if member.pgp %}
            <br/><i class="fa-solid fa-key"></i> <a href="https://keys.openpgp.org/vks/v1/by-fingerprint/{{member.pgp}}" target="_blank">{{ member.pgp }}</a>
          {% endif %}
          </small>
        </p>
      </div>
    </div>
  </div>
</div>
{% endfor %}
