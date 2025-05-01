---
title: "Data and Society"
course_number: "DIDA 325"
semester: "Fall 2024"
level: "Undergraduate"
role: "Teaching Assistant"
summary: "This course offers experience in discovering, manipulating, analyzing, and visualizing data drawn from various real-world professional, social, and cultural contexts."
draft: false
date: 2024-12-15
layout: "single"
---

## Course Description

This course offers experience in discovering, manipulating, analyzing, and visualizing data drawn from various real-world professional, social, and cultural contexts. Students will gain enhanced data literacy, an immersion into critical data studies, an understanding of the processes behind data-driven decision-making, and the ability to interpret claims based on data and its visualization. They will also explore the problems inherent in data-driven approaches, such as missing data, algorithmic bias, and privacy and surveillance concerns, with a special focus on those communities that are often marginalized or disadvantaged by data-driven decisions.

{{- $yearCourses := where $pastCourses (lambda (c) (eq (index (split c.Params.semester " ") 1) (printf "%d" $year))) }}

{{- range $pastCourses }}
  {{- $parts := split .Params.semester " " }}
  {{- if and (eq (len $parts) 2) (eq (index $parts 1) (printf "%d" $year)) }}
    <!-- Render course card here -->
  {{- end }}
{{- end }}

