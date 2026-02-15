---
layout: home
title: "Inicio"
---
#### ¡Bienvenidos!
Soy sociólogo y enseño "Desarrollo de Habilidades Investigativas" en la escuela de Gestión Pública y Desarrollo Social de la Universidad Nacional de Juliaca. Acompaño a jóvenes en su camino para convertirse en agentes de cambio, afianzando sus competencias de investigación para que puedan abordar los retos de la gestión pública y el desarrollo social desde una perspectiva basada en la evidencia y el razonamiento científico. Actualmente, coordino el Grupo de Investigación Sociedad, Política y Gobierno (SPG), donde promovemos estudios asociados al (1) Fortalecimiento institucional en la gestión pública y (2) al Desarrollo social local. Mis áreas de investigación general son: 1) La interacción entre educación y tecnología, con énfasis en el desarrollo de la competencia de investigación en educación superior asistida con herramientas de IA.  2) La modernización de la gestión pública centrándome en los procesos de automatización de procesos y sus efectos en la generación de valor público.  3) Los estudios urbanos situados orientados a la comprensión de la dinámica de los centros urbanos en la región Puno, en particular el área metropolitana de Juliaca. Mi trabajo parte de la convicción de que la educación, la tecnología y la gestión pública deben converger para robustecer las instituciones democráticas y mejorar la provisión de bienes y servicios públicos.
Si quieres saber más o seguir en contacto, escríbeme a: gvilca@unaj.edu.pe 

### Afiliaciones actuales

- Escuela de Gestión Pública y Desarrollo Social – Profesor Asociado 
- Grupo de Investigación Sociedad, Política y Gobierno - Investigador Titular / Coordinador 
- Waynarroque, Revista de Ciencias Sociales Aplicadas - Editor

---

Bienvenido a mi espacio académico digital.
Aquí comparto investigaciones, docencia y reflexiones públicas.

---

### Publicaciones recientes

{% for post in site.posts limit:5 %}
- **{{ post.date | date: "%d %B %Y" }}** — [{{ post.title }}]({{ post.url | relative_url }})
{% endfor %}

[Ver todos los artículos →](/blog/)
