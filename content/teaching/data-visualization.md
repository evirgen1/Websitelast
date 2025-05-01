---
title: "Data Visualization for Public Policy"
course_number: "POLICY 3100"
semester: "Spring 2024"
level: "Undergraduate"
role: "Instructor"
date: 2024-01-15
draft: false
featured: true
tags: ["data-visualization", "public-policy", "R"]
summary: "Undergraduate course on creating effective data visualizations for policy communication"
syllabus: "/teaching/data-visualization/syllabus.pdf"
course_site: "https://dataviz.university.edu"
course_image: "/teaching/data-visualization/course-image.jpg"
---

# Data Visualization for Public Policy (POLICY 3100)

**Instructor:** Your Name  
**Email:** your.email@university.edu  
**Office Hours:** Tuesdays 1-3pm, Thursdays 2-4pm  
**Location:** Social Sciences Building, Room 201  
**Time:** Mondays and Wednesdays, 11:00am-12:15pm

## Course Description

This course teaches students how to create effective, truthful, and compelling data visualizations specifically for public policy contexts. Students will learn both the theory behind good visualization and practical skills using R and ggplot2. The course emphasizes how to communicate complex policy data to different audiences, including policymakers, the general public, and technical experts.

## Learning Objectives

By the end of this course, students will be able to:

- Apply principles of visual perception and cognition to create effective visualizations
- Use R and ggplot2 to create a wide range of visualization types
- Select appropriate visualization types based on data structure and communication goals
- Create accessible visualizations that account for various audience needs
- Critique and improve existing policy visualizations
- Develop interactive visualizations for web and presentation use

## Course Materials

- [Download Syllabus (PDF)](/teaching/data-visualization/syllabus.pdf)
- [Course Website](https://dataviz.university.edu)
- [Required Textbook: Fundamentals of Data Visualization](https://clauswilke.com/dataviz/)
- [R and ggplot2 References](https://ggplot2.tidyverse.org/)

## Schedule

| Week | Topic | Materials | Assignments |
|------|-------|-----------|------------|
| 1 | Introduction and Visual Perception | [Slides](/teaching/data-visualization/week1-slides.pdf), [R Setup Guide](/teaching/data-visualization/setup.pdf) | Visual Critique Exercise |
| 2 | Data Structures and Grammar of Graphics | [Slides](/teaching/data-visualization/week2-slides.pdf), [R Code](/teaching/data-visualization/week2-code.R) | Exercise 1: Basic Plots |
| 3 | Visualization Types: Amounts and Proportions | [Slides](/teaching/data-visualization/week3-slides.pdf), [Data](/teaching/data-visualization/week3-data.csv) | Exercise 2: Bar Charts and Pie Charts |
| 4 | Visualization Types: Trends and Time Series | [Slides](/teaching/data-visualization/week4-slides.pdf), [Data](/teaching/data-visualization/week4-data.csv) | Exercise 3: Line Charts |
| 5 | Visualization Types: Distributions | [Slides](/teaching/data-visualization/week5-slides.pdf), [Code](/teaching/data-visualization/week5-code.R) | Exercise 4: Histograms and Density Plots |
| 6 | Visualization Types: Relationships | [Slides](/teaching/data-visualization/week6-slides.pdf) | Mini-Project 1 Due |
| 7 | Visualization Types: Spatial Data | [Slides](/teaching/data-visualization/week7-slides.pdf), [Shapefiles](/teaching/data-visualization/week7-maps.zip) | Exercise 5: Maps |
| 8 | Color Theory and Application | [Slides](/teaching/data-visualization/week8-slides.pdf), [Color Schemes](/teaching/data-visualization/colorschemes.R) | Exercise 6: Color in Visualization |
| 9 | Text, Annotations, and Storytelling | [Slides](/teaching/data-visualization/week9-slides.pdf) | Storyboard for Final Project |
| 10 | Accessibility in Data Visualization | [Slides](/teaching/data-visualization/week10-slides.pdf) | Exercise 7: Accessible Design |
| 11 | Interactive Visualizations with Shiny | [Slides](/teaching/data-visualization/week11-slides.pdf), [Code](/teaching/data-visualization/shiny-demo.zip) | Mini-Project 2 Due |
| 12 | Dashboard Design | [Slides](/teaching/data-visualization/week12-slides.pdf) | Exercise 8: Simple Dashboard |
| 13 | Visualization Ethics and Misleading Graphics | [Slides](/teaching/data-visualization/week13-slides.pdf) | Critique Assignment |
| 14 | Advanced Techniques and Project Work | [Slides](/teaching/data-visualization/week14-slides.pdf) | Project Draft for Peer Review |
| 15 | Student Project Presentations | | Final Project Due |

## Assessment

- **Exercises (30%)**: Eight hands-on visualization exercises
- **Mini-Projects (20%)**: Two small-scale visualization projects
- **Class Participation (15%)**: In-class activities and discussions
- **Final Project (35%)**: Comprehensive data visualization project on a policy topic of your choice

## Example Code

```R
# Creating a policy-relevant visualization in R
library(ggplot2)
library(dplyr)
library(scales)

# Load policy data (income inequality by state)
inequality_data <- read.csv("state_inequality.csv")

# Create visualization
ggplot(inequality_data, aes(x = reorder(state, gini_index), y = gini_index, fill = region)) +
  geom_bar(stat = "identity") +
  coord_flip() +
  scale_fill_viridis_d() +
  labs(
    title = "Income Inequality by State",
    subtitle = "Measured by Gini Index, 2023",
    x = NULL,
    y = "Gini Index (Higher = More Inequality)",
    fill = "Region",
    caption = "Source: U.S. Census Bureau, American Community Survey"
  ) +
  theme_minimal() +
  theme(
    plot.title = element_text(face = "bold", size = 16),
    plot.subtitle = element_text(size = 12),
    axis.text.y = element_text(size = 9)
  )
```

## Technology Requirements

- Laptop with R and RStudio installed (installation instructions provided)
- No prior programming experience required
- Recommended: GitHub account for sharing code and collaborating on projects

## Additional Resources

- [R for Data Science (free online book)](https://r4ds.had.co.nz/)
- [Data Visualization Society Resources](https://www.datavisualizationsociety.com/resources)
- [PolicyViz Blog and Podcast](https://policyviz.com/)
- [Course GitHub Repository](https://github.com/yourusername/dataviz-course) 