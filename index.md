---
title: تمارين لغة الذكاء الاصطناعي في Azure
permalink: index.html
layout: home
---

# تمارين لغة الذكاء الاصطناعي في Azure

تم تصميم التمارين التالية لدعم الوحدات النمطية في Microsoft Learn [لتطوير حلول اللغة الطبيعية](https://learn.microsoft.com/training/paths/develop-language-solutions-azure-ai/).


{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Exercises'" %} {% for activity in labs %} {% unless activity.url contains 'ai-foundry' %}
- [{{ activity.lab.title }}]({{ site.github.url }}{{ activity.url }}) {% endfor %}
