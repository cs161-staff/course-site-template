---
layout: page
title: Announcements
nav_exclude: true
description: A feed containing all of the class announcements.
has_right_toc: true
---

# Announcements

{% assign announcements = site.announcements | reverse %}
{% for announcement in announcements %}
{{ announcement }}
{% if forloop.last == false %}
  <hr>
{% endif %}
{% endfor %}
