---
layout: archive
permalink: /service/
title: "Academic Service"
author_profile: true
excerpt_separator: ""
---

<div class="service-container">
  {% for category in site.data.service.categories %}
    <div class="service-category">
      <h2>{{ category.name }}</h2>
      
      <div class="service-items-wrapper">
        {% for item in category.items %}
          
          {% if item.event %}
            <!-- Case 1: This is an Organizational Role -->
            <div class="service-item-card">
              <div class="item-main">{{ item.role }}</div>
              <div class="item-context">{{ item.event }}, {{ item.year }}</div>
            </div>

        {% elsif item.course %}
            <!-- Case 2: This is a Teaching Assistantship -->
            <div class="service-item-card">
            <div class="item-main">{{ item.course }}</div>
            <div class="item-context">{{ item.role }} – {{ item.semester }}</div>
            </div>

          {% else %}
            <!-- Case 3: This must be a simple Reviewer -->
            <span class="service-tag">{{ item.name }}</span>
          {% endif %}

        {% endfor %}
      </div>
    </div>
  {% endfor %}
</div>