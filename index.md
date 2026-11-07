---
layout: page
title: "Inicio"
---
<div class="home-intro">

<div class="home-photo">
  <img src="{{ '/assets/perfil.png' | relative_url }}" alt="Gustavo Vilca">
</div>

  
  <div class="home-text">
  <h4>¡Bienvenidos!</h4>
  <p>
Soy sociólogo y docente de la Escuela Profesional de Gestión Pública y Desarrollo Social de la Universidad Nacional de Juliaca (UNAJ). Mi labor académica está orientada a acompañar la formación de jóvenes comprometidos con la transformación de su entorno, fortaleciendo sus competencias profesionales, humanas e investigativas para abordar los desafíos de la gestión pública y los asuntos de gobierno desde la integridad, el pensamiento crítico y el razonamiento científico. Actualmente coordino el Grupo de Investigación Sociedad, Política y Gobierno (SPG), desde el cual promovemos la generación de conocimiento en dos líneas de investigación: fortalecimiento institucional de la gestión pública y desarrollo social local. Mis intereses académicos y de investigación se articulan en tres campos principales: (1) Educación y tecnología: estudio de la interacción entre los procesos educativos y las tecnologías emergentes, con especial interés en el desarrollo de competencias investigativas en la educación superior y el uso de herramientas de inteligencia artificial como apoyo al aprendizaje y la investigación. (2) Modernización de la gestión pública: análisis de la transformación digital y la automatización de procesos administrativos, con énfasis en sus implicaciones para el desempeño institucional y la generación de valor público. (3) Estudios urbanos: investigación de las dinámicas sociales, territoriales e institucionales de las ciudades de la región Puno, con especial atención al área metropolitana de Juliaca y sus desafíos de desarrollo urbano. Mi trabajo se sustenta en la convicción de que la educación, la tecnología y la gestión pública pueden converger para fortalecer las instituciones democráticas, mejorar la provisión de bienes y servicios públicos y contribuir al bienestar de la sociedad..
  </p>
  <p>
Si quieres saber más o seguir en contacto, escríbeme a: gvilca@unaj.edu.pe
  </p>
  </div>
</div>


#### Afiliaciones actuales

- Escuela de Gestión Pública y Desarrollo Social – Profesor Asociado 
- Grupo de Investigación Sociedad, Política y Gobierno - Investigador Titular / Coordinador 

#### Apuntes recientes 
Aquí comparto notas de análisis y reflexión sobre investigaciones, docencia y asuntos de gobierno.

{% for post in site.posts limit:3 %}
- **{{ post.date | date: "%d %B %Y" }}** — [{{ post.title }}]({{ post.url | relative_url }})
{% endfor %}

[Ver todos los artículos →](/blog/)
