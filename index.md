---
title: Instruções Hospedadas Online
permalink: index.html
layout: home
---

# Diretório de Conteúdo

Hiperlinks para cada um dos tutoriais. Os instrutores podem optar por usar o passo a passo como uma demonstração ou um laboratório do aluno. 

## Passo a passo

{% assign wts = site.pages | where_exp:"page", "page.url contains '/Instructions/Walkthroughs'" %}
| Módulo | Passo a passo |
| --- | --- | 
{% for activity in wts %}| {{ activity.wts.module }} | [{{ activity.wts.title }}{% if activity.wts.type %} - {{ activity.wts.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

