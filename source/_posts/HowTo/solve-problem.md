---
title: How can we better solve problems?
date: 2022-01-13 20:20:38
tags:
categories:
  - How-To
---

{% mermaid graph LR%}

s((start)) --> o[observe]

o -->|1st time and 1st time only| h[hypothesis]

h --> p[predict]

p --> o

o --> c[check]

c --> a{prediction agrees with observation?}

a -->|y| e((end))

a -->|n| h

{% endmermaid %}
