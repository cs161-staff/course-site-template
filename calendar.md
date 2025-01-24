---
title: Calendar
layout: page
nav_order: 1
---

<h1>Calendar</h1>

{% assign button_groups = site.data.calendar.categories | map: "name" | uniq %}

{%- if site.under_construction -%}
<p class="warning">
This site is under construction. All dates and policies are tentative until this message goes away.
</p>
{%- endif -%}

{%- if site.discussions_under_construction -%}
<p class="warning">
This schedule is tentative; additional times may be added later. The existing times shouldn’t change though (pending a couple of room bookings).
</p>
{%- endif -%}

{%- if site.outdated -%}
<p class="warning">
This website contains materials from a past semester. Information, assignments, and announcements may no longer be relevant. Please refer to the <a href="https://template.cs161.org">current semester's site</a> for up-to-date content.
</p>
{%- endif -%}

If you would like to view this calendar ouside of the course website, please click "Open in Google Calendar" below. If you would like to add an accessible version of this calendar to your personal Google Calendar, please click "Add to your personal calendar" below.

[Open in Google Calendar]({{ site.data.calendar.google_calendar_embed_link }}){: .btn .btn-outline .fs-3 } [Add to your personal calendar]({{ site.data.calendar.google_calendar_add_link }}){: .btn .btn-outline .fs-3 }

{% include calendar.html %}

<div id="calendarContainer">
  <div id="calendarControls" class="btn-toolbar justify-content-between" role="toolbar" aria-label="Calendar control toolbar">
    Use the following toggles to customize your calendar view. If you'd like to hide a category of events, click on the respective button to do so. The calendar will immediately update to reflect your selection. To re-enable that category, click again.
    <span style="display: block; height: 1rem;"></span>
    <div class="input-group mb-3" role="group" aria-label="Calendar category toggles" style="text-align: center;">
      {% for group in button_groups %}
        <button class="btn btn-outline-primary" data-action="toggle-category-{{ group | downcase | replace: " ", "-" }}" aria-label="Toggle {{ group }}" >{{ group }}</button>
      {% endfor %}
    </div>
  </div>
</div>

<script>
  document.addEventListener("DOMContentLoaded", function() {
    initCalendar();
  });
</script>
