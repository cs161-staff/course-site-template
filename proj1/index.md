---
layout: project
project_index: 0 # utilize the index from _data/projects.yml (if not yet released, a warning with populate that the spec is unreleased)
title: Project 1
nav_order: 5
nav_exclude: false # set to false when project released
has_children: true
---

# Project 1

You can access attributes from `_data/proj1_assignment.yml` to add to these assignments. For instance, you can produce {{ site.data.proj1_assignment.example_string_attribute }}, or use it for [links]({{ site.data.proj1_assignment.example_link_attribute }})!

You can also add images like below!
![Stars to orbit!]({{ "/assets/projects/proj1/orbot.jpg" | relative_url }})
