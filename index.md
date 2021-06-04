---
title: Instruções Hospedadas Online
permalink: index.html
layout: home
---

# Diretório de Conteúdo

Hiperlinks para cada um dos tutoriais. Os instrutores podem optar por usar o passo a passo como uma demonstração ou um laboratório do aluno. 

## Passo a passo

{% atribuir wts = site.pages | em que _exp:"page", "page.url contém '/Instructions/Walkthroughs'" %}
| Módulo | Passo a passo |
| --- | --- | 
{% para atividade no wts %}| {{ activity.wts.module }} | [{{ activity.wts.title }}{% se activity.wts.type %} – {{ activity.wts.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

