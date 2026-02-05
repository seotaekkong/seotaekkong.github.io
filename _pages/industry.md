---
layout: archive
title: "Industry Experience"
permalink: /industry/
author_profile: true
---

<div class="exp-grid">
  {% for c in site.data.industry.companies %}
    <section class="exp-card">
      <header class="exp-header">
        <div class="exp-companyline">
          <img class="exp-logo"
               src="{{ '/images/' | append: c.logo | relative_url }}"
               alt="{{ c.name }} logo">
          <div class="exp-company">{{ c.name }}</div>
        </div>
        <div class="exp-role">{{ c.role }}</div>
      </header>

      <div class="exp-rows">
        {% for s in c.segments %}
          <div class="exp-rowitem">
            <div class="exp-left">{{ s.label }}</div>
            <div class="exp-right">{{ s.dates }}</div>
          </div>
        {% endfor %}
      </div>

      <div class="exp-tags">
        {% for t in c.tech %}
          <span class="exp-tag">{{ t }}</span>
        {% endfor %}
      </div>
    </section>
  {% endfor %}
</div>