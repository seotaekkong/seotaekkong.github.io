---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

<div class="pub-intro">
  <div class="pub-intro-text">
    This page lists <strong>selected publications</strong>. For the full list of papers and preprints, see my Google Scholar profile:
  </div>
  <a href="https://scholar.google.com/citations?user=YFmOjdQAAAAJ&hl=en"
     target="_blank" rel="noopener noreferrer"
     class="scholar-link">
    <img src="{{ '/images/google-scholar.png' | relative_url }}"
         alt="Google Scholar"
         class="scholar-logo">
  </a>
</div>


## Selected Journal Manuscripts

<div class="pub-grid">
{% for pub in site.data.publications.journals %}
  <div class="pub-card">
    <div class="pub-card-top">
    <div class="pub-title">
    {{ pub.title }}
    {% if pub.url %}
        <a class="pub-link-inline" href="{{ pub.url }}" target="_blank" rel="noopener noreferrer">[Link]</a>
    {% endif %}
    </div>

    <!-- Boldface my name.  -->
    </div>
    {% if pub.authors and pub.authors.size > 0 %}
    {% assign author_str = pub.authors | join: ", " %}
    {% assign author_str = author_str | replace: "S. T. Kong", "<strong>S. T. Kong</strong>" %}
    {% assign author_str = author_str | replace: "Seo Taek Kong", "<strong>Seo Taek Kong</strong>" %}
    <div class="pub-authors">{{ author_str }}</div>
    {% endif %}
    
    <div class="pub-meta">
      <span class="pub-venue">
        {{ pub.venue }}{% if pub.year %} ({{ pub.year }}){% endif %}
      </span>
    </div>


  </div>
{% endfor %}
</div>

## Selected Conference Papers

<div class="pub-grid">
{% for pub in site.data.publications.conferences %}
  <div class="pub-card">
    <div class="pub-card-top">
    <div class="pub-title">
    {{ pub.title }}
    {% if pub.url %}
        <a class="pub-link-inline" href="{{ pub.url }}" target="_blank" rel="noopener noreferrer">[Link]</a>
    {% endif %}
    </div>
    </div>

    {% if pub.authors and pub.authors.size > 0 %}
      <div class="pub-authors">
        {% assign author_str = pub.authors | join: ", " %}
        {{ author_str | replace: "S. T. Kong", "<strong>S. T. Kong</strong>" }}
      </div>
    {% endif %}

    <div class="pub-meta">
    <span class="pub-venue">
        {{ pub.venue }}{% if pub.year %} ({{ pub.year }}){% endif %}
    </span>
    </div>
  </div>
{% endfor %}
</div>

{% if site.data.publications.preprints and site.data.publications.preprints.size > 0 %}
## In Progress

<div class="pub-grid">
{% for pub in site.data.publications.preprints %}
  <div class="pub-card">
    <div class="pub-card-top">
    <div class="pub-title">
    {{ pub.title }}
    {% if pub.url %}
        <a class="pub-link-inline" href="{{ pub.url }}" target="_blank" rel="noopener noreferrer">[Link]</a>
    {% endif %}
    </div>
    </div>

    {% if pub.authors and pub.authors.size > 0 %}
      {% assign author_str = pub.authors | join: ", " %}
      {% assign author_str = author_str | replace: "S. T. Kong", "<strong>S. T. Kong</strong>" %}
      {% assign author_str = author_str | replace: "Seo Taek Kong", "<strong>Seo Taek Kong</strong>" %}
      <div class="pub-authors">{{ author_str }}</div>
    {% endif %}

    {%- comment -%}
    Intentionally no pub-meta/venue line here to avoid repeating "In progress"
    since the section heading already says In Progress.
    {%- endcomment -%}
  </div>
{% endfor %}
</div>
{% endif %}