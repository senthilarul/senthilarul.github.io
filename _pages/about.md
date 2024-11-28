---
layout: about
title: about
permalink: /
subtitle: Ph.D. Candidate at University of Maryland College Park <br> <b>Robotics | Motion Planning | Planning under Uncertainty | Reinforcement Learning </b> <br><br>

profile: 
  align: right 
  image: DSC00719.JPG
  image_circular: false # crops the image to make it circular
  more_info: >
    <br><p></p><p></p><p>Email: sarul1@umd.edu</p>
    <p><center><a href="https://senthilarul.github.io/assets/pdf/Arul_CV_Github.pdf">Curriculum Vitae</a></center></p>

news: false # includes a list of news items
latest_posts: true # includes a list of the newest posts
selected_papers: false # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page
---
I am a Ph.D. candidate in <a href="https://ece.umd.edu">Electrical and Computer Engineering</a> at the University of Maryland, College Park, specializing in multi-agent navigation within complex environments under the guidance of <a href="https://scholar.google.com/citations?user=X08l_4IAAAAJ&hl=en">Prof. Dinesh Manocha</a>. My research integrates robotics, motion planning, and reinforcement learning to advance AI technology. Specifically, I specialize in cooperative navigation and motion planning under uncertainty, exploring innovative solutions for real-world applications. In addition, I completed two internships at <a href="https://amazon.jobs/en/teams/lab126/">Amazon Lab126</a>, specifically with the <a href="https://www.amazon.jobs/content/en/teams/devices-services/consumer-robotics">Consumer Robotics group</a>.

I hold a bachelor's degree in Instrumentation and Control Engineering from the National Institute of Technology, Tiruchirappalli. I interned for a summer at McMaster University, Canada, with <a href="https://www.eng.mcmaster.ca/mech/faculty/dr-gary-m-bone/">Prof. Gray Bone</a>, where I was <br> involved in the development of an autonomous collaborative robotic arm.
I am <br> proficient in C++, Python, and TensorFlow, with a strong publication
record in <br> top-tier robotics and AI conferences.

---

<br> Research Directions <\br>


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
    <div class="row row-cols-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
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
    <div class="row row-cols-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
