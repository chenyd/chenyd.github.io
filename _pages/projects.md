---
layout: page
title: Research
permalink: /research/
description: 
nav: true
nav_order: 3
display_categories: 
horizontal: false
---

My research lies in the following directions:

### Diffusion model and Reinforcement Learning
Diffusion models have demonstrated remarkable success in sample generation, particularly for complex, high-dimensional distributions. Reinforcement learning, in contrast, provides a principled framework for sequential decision making under uncertainty. Integrating these two paradigms has the potential to advance both fields:
- <a href='https://arxiv.org/abs/2505.03194'>ICML 2025</a>: we establish convergence guarantees for consistency models, relax standard assumptions on data distributions, and analyze multistep sampling techniques.
- <a href='https://arxiv.org/abs/2410.13855'>ICLR 2025</a>: a stable and efficient imitation learning method via diffusing the states and applying score matching
- <a href='https://arxiv.org/abs/2505.21666'>preprint </a>: diffusion model reward maximization by reduction to supervised learning.
- <a href='https://arxiv.org/abs/2505.22866'> preprint</a>: a one-stage training procedure for expressive policies with test-time scaling.

### Incentive Mechanism for Data Sharing
High-quality data is costly to collect but crucial for machine learning. While agents can reduce cost and improve the model accuracy through data sharing, a naive pool protocol may lead to free-riding. In the following line of work, we design mechanisms that incentive truthful data sharing: 
- <a href='https://arxiv.org/abs/2306.06351'>NeurIPS 2023 </a>: mechanism design for the normal mean estimation problem that incentivizes agents to collect sufficient data and report truthfully.
- <a href='https://arxiv.org/abs/2407.15881'>ICML 2025 </a>: mechanisms for heterogeneous cost functions, addressing new fundamental challenges.
- <a href='https://arxiv.org/abs/2506.07272'>preprint </a>: mechanism without strong assumptions on data distributions with both theoretical justification and empirical demonstration on language and image data.

### Robust Decision Making
Data corruption introduce threat to sequential decision making. The adversary may manipulate the dataset to mislead the learning agent into making a suboptimal decisions. Our goal is to design reinforcement learning algorithms that are robust against data corruption:
- <a href='https://arxiv.org/abs/2102.05800'>ICML 2021 </a>: robust policy gradient algorithm for online RL and the informational-theoretical limits.
- <a href='https://arxiv.org/abs/2106.06630'>AISTATS 2022 </a>: robust algorithms for  offline RL.
- <a href='https://arxiv.org/abs/2206.00165'>AISTATS 2023</a>: robust RL in the distributed setting, where each data source may provide different number of data points. A portion of the data sources can be arbitrarily corrupted. We design novel robust mean estimation algorithm and apply it to RL.
- <a href='https://ojs.aaai.org/index.php/AAAI/article/view/29022'>AAAI 2024</a>: exactly optimal policy recovery is possible by a refined instance-dependent analysis with the presence of data corruption and heavy-tailed reward distributions.

<!-- pages/projects.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
