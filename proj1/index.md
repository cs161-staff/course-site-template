---
layout: page
title: Project 1
nav_order: 5
nav_exclude: true # set to false when project released
hide_content: false # set to false when project released
---

{% if site.data.proj1_assignment.unreleased_warning %}
  <p class="warning">
    This spec is in an unreleased state. This warning message will go away once it's been fully updated for the current
    semester.
  </p>
{% endif %}

# Project 1

You can access attributes from `_data/proj1_assignment.yml` to add to these assignments. For instance, you can produce {{ site.data.proj1_assignment.example_string_attribute }}, or use it for [links]({{ site.data.proj1_assignment.example_link_attribute }})!

You can also add images like below!
![Stars to orbit!]({{ "/assets/projects/proj1/orbot.jpg" | relative_url }})
