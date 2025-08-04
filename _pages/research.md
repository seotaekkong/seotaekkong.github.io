---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
excerpt_separator: ""
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
          <p>{{ topic.description }}</p>
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
          <!-- Applications Sub-section (Collapsible) -->
          {% if topic.applications %}
            <div class="sub-section">
              <div class="subsection-header">
                <h4>Applications</h4>
                <button class="details-toggle" aria-expanded="false">Show <span class="arrow">▸</span></button>
              </div>
              <div class="collapsible-content">
                <ul class="application-list">
                  {% for app in topic.applications %}
                    <li>
                      <div class="application-header"><strong>{{ app.name }}</strong></div>
                      <p>{{ app.description }}</p>
                      <figure class="embedded-research-figure">
                        <img src="{{ app.figure | relative_url }}" alt="Illustration for {{ app.name }}">
                        <figcaption>{{ app.figcaption }}</figcaption>
                      </figure>
                    </li>
                  {% endfor %}
                </ul>
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
        <p>
          During my 12 months as an Applied Scientist Intern, I developed and validated machine learning models for key business problems. My work spanned two areas: developing Large Language Models (LLMs) to improve semantic search ranking, and architecting predictive models from user behavioral signals to solve critical data sparsity issues in product quality analysis.
        </p>
        <div class="sub-section">
          <div class="subsection-header">
            <h4>Description</h4>
            <button class="details-toggle" aria-expanded="false">Show <span class="arrow">▸</span></button>
          </div>
          <div class="collapsible-content">
            <div class="publication-cards-wrapper">
              <h4>Machine Learning Pipeline</h4>
              <p>I employ a versatile modeling strategy, utilizing both custom deep learning (PyTorch, HuggingFace) and AutoML (AutoGluon) before rigorous offline benchmarking. This end-to-end process ensures the final deliverables are not only powerful but also robustly validated against business objectives.</p>
              <figure class="embedded-research-figure">
                <img src="/images/internship-pipeline.svg" alt="Machine learning workflow" style="max-width: 100%; width: 500px; height: auto;">
                <figcaption>
                  <strong>Figure:</strong> A representative large-scale deep learning workflow. This architecture demonstrates my approach to building scalable machine learning pipelines. The process begins with distributed querying on large-scale cloud data, followed by high-performance ETL using modern data frame libraries.
                </figcaption>
              </figure>
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
        <p>
          In my three years at VUNO, I evolved from a Researcher to a Research Team Lead, solving problems that arise when developing deep learning models for medical imaging. I led research on ML methodologies that resulted in first-author publications at premier AI venues (NeurIPS, AAAI) and contributed to the analysis of models across various modalities.
        </p>
        <div class="sub-section">
          <div class="subsection-header">
            <h4>Description</h4>
            <button class="details-toggle" aria-expanded="false">Show <span class="arrow">▸</span></button>
          </div>
          <div class="collapsible-content">
            <div class="publication-cards-wrapper">
              <h4>Detecting abnormalities in Chest X-rays</h4>
              <p>Many diseases, such as tumors or infections, manifest as subtle visual patterns in chest X-ray images including localized shadows, nodules, or irregular textures. Deep learning models can be trained to recognize these abnormalities. By detecting and localizing such patterns, these models help scale diagnostic support in medical imaging. </p>
              <figure class="embedded-research-figure">
                <img src="/images/nih-nodule.png" alt="Nodule" style="max-width: 100%; width: 500px; height: auto;">
                <figcaption><strong>Figure:</strong> Example chest X-ray from the NIH ChestX-ray14 dataset, with a bounding box indicating a labeled lung nodule.</figcaption>
                <div class="figure-citation">
                  [1] Wang, X., Peng, Y., Lu, L., Lu, Z., Bagheri, M., & Summers, R. M. (2017). Chestx-ray8: Hospital-scale chest x-ray database and benchmarks on weakly-supervised classification and localization of common thorax diseases. In Proceedings of the IEEE conference on computer vision and pattern recognition.
                </div>
              </figure>
            </div>
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