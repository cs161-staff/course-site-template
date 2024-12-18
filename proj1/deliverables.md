---
layout: project
project_index: 0
title: Deliverables
nav_order: 100
parent: Project 1
has_right_toc: true
---

# Deliverables

Your submission for this project involves a checkpoint autograder submission (for Q1-4), a final autograder submission (for all questions), and a final write-up. If you worked with a partner, remember to add your partner to all of your Gradescope submissions!

---

## Deadlines

| Task                                  | Due                                               | Points |
| ------------------------------------- |---------------------------------------------------| ------ |
| Final Code Submission (all questions) | {{ site.data.proj1_assignment.due_date            | date: "%A, %B %-d, %Y" }}            | 50     |
| Final Write-up                         | {{ site.data.proj1_assignment.due_date            | date: "%A, %B %-d, %Y" }}            | 30     |

All assignments are due at 11:59 PM. This project is worth a total of 100 points.

---

{% comment %}
The following utilizes `_data/projects.yml` to see whether the assignment should be released (and thus, whether the assignment should be clickable to students).
{% endcomment %}

## Autograder Submission

{% if site.data.projects.projects[0].released %}

**Deliverable**: Please submit your final autograder .zip file to the [Autograder]({{ site.data.proj1_assignment.gradescope.autograder }}) assignment.

{% else %}

**Deliverable**: Please submit your final autograder .zip file to the Autograder assignment, which will be released on Gradescope.

{% endif %}

Generate your final autograder .zip file using the above Local Setup or Instructional Machine Setup methods.

## Write-up Submission

{% if site.data.projects.projects[0].released %}

**Deliverable**: Please submit your write-up to the [Write-up]({{ site.data.proj1_assignment.gradescope.writeup }}) assignment.

{% else %}

**Deliverable**: Please submit your write-up to the Write-up assignment, which will be released on Gradescope.

{% endif %}

If you wish, you may submit feedback at the end of your write-up, with any feedback you may have about this project. What was the hardest part of this project in terms of understanding? In terms of effort? (We also, as always, welcome feedback about other aspects of the class.) Your comments will not in any way affect your grade.

---
