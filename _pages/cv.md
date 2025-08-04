---
layout: default
title: "Curriculum Vitae"
permalink: /cv/
---

<div class="container">

  <!-- Education Section -->
  <section class="section">
    <h2>{{ site.data.data.education.title }}</h2>
    {% for item in site.data.data.education.items %}
    <div class="item">
      <h3>{{ item.degree }}</h3>
      <h4>{{ item.university }}</h4>
      <p class="time">{{ item.time }}</p>
      {% if item.details %}
      <div class="education-details">
        {% for detail in item.details %}
          <span class="detail-tag">{{ detail }}</span>
        {% endfor %}
      </div>
      {% endif %}
    </div>
    {% endfor %}
  </section>

  <!-- Work Experience Section -->
  <section class="section">
    <h2>{{ site.data.data.experience.title }}</h2>
    {% for item in site.data.data.experience.items %}
    <div class="item">
      <div class="item-header">
    <div>
      <h3>{{ item.position }}</h3>
      <h4>{{ item.company }}</h4>
      <p class="item-meta">
        {% if item.team %}{{ item.team }}{% endif %}
        {% if item.team and item.location %} <span class="separator">|</span> {% endif %}
        {% if item.location %}{{ item.location }}{% endif %}
        {% if item.location and item.time %} <span class="separator">|</span> {% endif %}
        {% if item.time %}{{ item.time }}{% endif %}
      </p>
    </div>
        <button class="details-toggle" aria-expanded="false" aria-controls="details-{{ forloop.index }}">
          Details <span class="arrow">▸</span>
        </button>
      </div>
      <div id="details-{{ forloop.index }}" class="collapsible-details">
        <div class="accomplishments">
          {% for acc in item.details %}
            <div class="accomplishment-item">
              <p class="headline"><strong>{{ acc.headline }}</strong></p>
              <p class="description">{{ acc.description }}</p>
              {% if acc.tech %}
                <div class="tech-stack">
                  {% for tech_item in acc.tech %}
                    <span class="tech-tag">{{ tech_item }}</span>
                  {% endfor %}
                </div>
              {% endif %}
            </div>
          {% endfor %}
        </div>
      </div>
    </div>
    {% endfor %}
  </section>


{% if site.data.data.skills %}
<section class="section">
  <h2>{{ site.data.data.skills.title }}</h2>
  <div class="skills-grid">
    {% for category in site.data.data.skills.categories %}
    <div class="skill-category">
      <h3>{{ category.name }}</h3>
      <div class="skill-tags">
        {% for item in category.items %}
        <span class="skill-tag">{{ item }}</span>
        {% endfor %}
      </div>
    </div>
    {% endfor %}
  </div>
</section>
{% endif %}

  <!-- Theoretical Foundations Section -->
  <section class="section">
    <h2>{{ site.data.data.foundations.title }}</h2>
    <div class="foundations-container">
      {% for item in site.data.data.foundations.items %}
      <span class="tag">{{ item }}</span>
      {% endfor %}
    </div>
  </section>

</div>
