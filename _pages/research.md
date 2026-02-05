---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

<div class="container research-container">
  <!-- New, Refined Hero Section -->
  <div class="research-hero">
    <div class="hero-content">
      <h1>Investigating the Foundations of Learning Algorithms</h1>
      <p class="hero-subtitle">
        My research is centered on understanding the fundamental limits and capabilities of machine learning algorithms.
      </p>
      <a href="https://scholar.google.com/citations?user=YFmOjdQAAAAJ&hl=en" class="btn-hero-scholar" target="_blank" rel="noopener noreferrer">
        <i class="fas fa-graduation-cap"></i> View All Publications
      </a>
    </div>
  </div>

  <!-- SECTION 1: CORE RESEARCH TOPICS -->
  <div class="research-section">
    <h2>Core Research Topics</h2>
    <div class="research-topics-wrapper">
      {% for topic in site.data.research.research_topics %}
        <div class="industry-card">
          <h4>{{ topic.title }}</h4>
          <!-- <p>{{ topic.description }}</p> -->
          <!-- Relevant Publications Sub-section (Collapsible) -->
          {% assign pub_list = site.data.research[topic.publication_key] %}
          {% if pub_list %}
            <div class="sub-section">
              <div class="subsection-header">
                <h4>Relevant Publications</h4>
                <button class="details-toggle" aria-expanded="false">Show <span class="arrow">▸</span></button>
              </div>
              <div class="collapsible-content">
                <div class="publication-cards-wrapper">
                {% for pub in pub_list %}
                  <div class="pub-card">
                    <div class="pub-header">
                      <div class="pub-info">
                        <h4 class="pub-title">
                          {% if pub.url %}
                            <a href="{{ pub.url }}" target="_blank" rel="noopener noreferrer">{{ pub.title }}</a>
                          {% else %}
                            {{ pub.title }}
                          {% endif %}
                        </h4>
                        <!-- START: ROBUST AUTHOR LIST LOGIC (HANDLES BOTH FORMATS) -->
                        {% if pub.authors %}
                          <p class="pub-authors">
                            {% for author in pub.authors %}
                              {% if author.name %}
                                <!-- If author is an object, use author.name -->
                                {{ author.name }}{% if author.equal_contribution %}*{% endif %}
                              {% else %}
                                <!-- If author is just a string, print it directly -->
                                {{ author }}
                              {% endif %}
                              {%- unless forloop.last %}, {% endunless -%}
                            {% endfor %}
                          </p>
                        {% endif %}
                        <!-- END: ROBUST AUTHOR LIST LOGIC -->
                        <p class="pub-venue">{{ pub.venue }}</p>
                      </div>
                      {% if pub.status == "Published" %}
                        <span class="pub-status status-published">{{ pub.status }}</span>
                      {% else %}
                        <span class="pub-status status-inprogress">{{ pub.status }}</span>
                      {% endif %}
                    </div>
                    <p class="pub-contribution">{{ pub.contribution }}</p>
                    <!-- START: CONTRIBUTION NOTE LOGIC -->
                    {%- assign has_equal_contribution = false -%}
                    {%- for author in pub.authors -%}
                      {%- if author.equal_contribution -%}
                        {%- assign has_equal_contribution = true -%}
                      {%- endif -%}
                    {%- endfor -%}
                    {% if has_equal_contribution %}
                      <p class="pub-contribution-note">*Denotes equal contribution.</p>
                    {% endif %}
                    <!-- END: CONTRIBUTION NOTE LOGIC -->
                  </div>
                {% endfor %}
                </div>
              </div>
            </div>
          {% endif %}
        </div>
      {% endfor %}
    </div>
  </div>

  <!-- SECTION 2: INDUSTRY & APPLIED RESEARCH -->
  <div class="research-section">
    <h2>Industry & Applied Research</h2>
    <div class="industry-experience-wrapper">
      <!-- Amazon Experience Card -->
      <div class="industry-card">
        <h4>Amazon<img src="/images/amazon-logo-squid-ink-smile-orange.png" alt="Amazon logo" class="company-logo"></h4>
        <ul class="industry-bullets">
          <li><strong>Search Relevance (Palo Alto, CA):</strong> Fine-tuned a listwise LLM for search reranking using PyTorch + HuggingFace on AWS SageMaker (multi-GPU).</li>
          <li><strong>Impact:</strong> Significantly improved ranking in nDCG@1.</li>
          <li><strong>Product Quality (Seattle, WA):</strong> Developed a predictive GBDT/NN ensemble model for pre-purchase customer satisfaction using Scala Spark, Polars, and AutoGluon.</li>
          <li><strong>Impact:</strong> Generated dense defect probability scores to address log sparsity, enabling downstream applications in search ranking and fault attribution.</li>
        </ul>        
        <div class="sub-section">
          <div class="subsection-header">
            <h4>Description</h4>
            <button class="details-toggle" aria-expanded="false">Show <span class="arrow">▸</span></button>
          </div>
          </div>
        </div>
        <div class="industry-tags">
          <span class="tech-tag">Large Language Models (LLMs)</span>
          <span class="tech-tag">Semantic Search</span>
          <span class="tech-tag">Predictive Modeling</span>
        </div>
      </div>
      <!-- VUNO Experience Card -->
      <div class="industry-card">
        <h4>VUNO Inc.<img src="/images/vuno.jpeg" alt="VUNO logo" class="company-logo"></h4>
        <div class="sub-section">
          <div class="subsection-header">
            <ul class="industry-bullets">
              <li>Developed deep learning architectures for Chest X-ray and other medical imaging analysis using PyTorch.</li>
              <li>Designed an active learning algorithm that significantly reduced labeling costs (published at NeurIPS 2022).</li>
              <li>Implemented out-of-distribution (OOD) detection modules for production diagnostic software to prevent silent failures on anomalous data (published at AAAI).</li>
            </ul>          
          </div>
        </div>
        <!-- VUNO Publications -->
        <div class="sub-section">
          <div class="subsection-header">
            <h4>Relevant Publications</h4>
            <button class="details-toggle" aria-expanded="false">Show <span class="arrow">▸</span></button>
          </div>
          <div class="collapsible-content">
            <div class="publication-cards-wrapper">
              {% for pub in site.data.research.vuno_publications %}
                <div class="pub-card">
                  <div class="pub-header">
                    <div class="pub-info">
                      <h4 class="pub-title">
                        {% if pub.url %}
                          <a href="{{ pub.url }}" target="_blank" rel="noopener noreferrer">{{ pub.title }}</a>
                        {% else %}
                          {{ pub.title }}
                        {% endif %}
                      </h4>
                      <!-- START: ROBUST AUTHOR LIST LOGIC (HANDLES BOTH FORMATS) -->
                      {% if pub.authors %}
                        <p class="pub-authors">
                          {% for author in pub.authors %}
                            {% if author.name %}
                              <!-- If author is an object, use author.name -->
                              {{ author.name }}{% if author.equal_contribution %}*{% endif %}
                            {% else %}
                              <!-- If author is just a string, print it directly -->
                              {{ author }}
                            {% endif %}
                            {%- unless forloop.last %}, {% endunless -%}
                          {% endfor %}
                        </p>
                      {% endif %}
                      <!-- END: ROBUST AUTHOR LIST LOGIC -->
                      <p class="pub-venue">{{ pub.venue }}</p>
                    </div>
                    {% if pub.status == "Published" %}
                      <span class="pub-status status-published">{{ pub.status }}</span>
                    {% else %}
                      <span class="pub-status status-inprogress">{{ pub.status }}</span>
                    {% endif %}
                  </div>
                  <p class="pub-contribution">{{ pub.contribution }}</p>
                  <!-- START: CONTRIBUTION NOTE LOGIC (for VUNO pubs) -->
                  {%- assign has_equal_contribution = false -%}
                  {%- for author in pub.authors -%}
                    {%- if author.equal_contribution -%}
                      {%- assign has_equal_contribution = true -%}
                    {%- endif -%}
                  {%- endfor -%}
                  {% if has_equal_contribution %}
                    <p class="pub-contribution-note">*Denotes equal contribution.</p>
                  {% endif %}
                  <!-- END: CONTRIBUTION NOTE LOGIC -->
                </div>
              {% endfor %}
            </div>
          </div>
        </div>
        <div class="industry-tags">
          <span class="tech-tag">Medical AI</span>
          <span class="tech-tag">Computer Vision</span>
        </div>
      </div>
    </div>
  </div>
</div>