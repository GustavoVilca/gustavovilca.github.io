---
layout: page
title: "Ideas"
permalink: /ideas/
---
<table class="tabla-notas">

  <style>
  .notes-layout{display:flex; gap:32px; align-items:flex-start;}
  .notes-main{flex:1; min-width:0;}
  .notes-side{width:220px;}
  .notes-controls{display:flex; gap:12px; align-items:center; margin:16px 0;}
  .notes-controls input{padding:6px 10px; width:260px; max-width:100%;}
  .notes-controls select{padding:6px 10px;}
  table.notes-table{width:100%; border-collapse:collapse; margin-top:8px;}
  table.notes-table th, table.notes-table td{padding:10px 8px; border-bottom:1px solid #e6e6e6; vertical-align:top;}
  table.notes-table th{text-align:left;}
  .cat-title{font-weight:600; margin-top:8px; margin-bottom:8px;}
  .cat-list{list-style:none; padding:0; margin:0;}
  .cat-list li{margin:6px 0;}
  .cat-list a{cursor:pointer; text-decoration:none;}
  .cat-list a.active{font-weight:700; text-decoration:underline;}
  .muted{opacity:.75;}
  .count{opacity:.75;}
  @media (max-width: 820px){
    .notes-layout{flex-direction:column;}
    .notes-side{width:100%;}
  }
</style>

<div class="notes-layout">

  <div class="notes-main">

    <p class="muted">Notas breves: investigación + opinión pública.</p>

    <div class="notes-controls">
      <select id="sortSelect" aria-label="Ordenar por">
        <option value="newest">Ordenar: más recientes</option>
        <option value="oldest">Ordenar: más antiguos</option>
        <option value="title">Ordenar: título (A–Z)</option>
      </select>

      <input id="searchInput" type="text" placeholder="Filtrar..." aria-label="Filtrar" />
    </div>

    <table class="notes-table" id="notesTable">
      <thead>
        <tr>
          <th style="width:75%;">Título</th>
          <th style="width:25%;">Fecha</th>
        </tr>
      </thead>
      <tbody id="notesBody">
        {% assign notes = site.posts %}
        {% for post in notes %}
        <tr class="note-row"
            data-title="{{ post.title | escape }}"
            data-date="{{ post.date | date: '%Y-%m-%d' }}"
            data-datepretty="{{ post.date | date: '%d %B %Y' }}"
            data-categories="{{ post.categories | join: ' ' | downcase }}">
          <td>
            <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
          </td>
          <td class="muted">{{ post.date | date: "%d %B %Y" }}</td>
        </tr>
        {% endfor %}
      </tbody>
    </table>

  </div>

  <aside class="notes-side">
    <div class="cat-title">Categorías</div>
    <ul class="cat-list" id="catList">
      <li><a class="cat-link active" data-cat="all">Todas <span class="count" id="countAll"></span></a></li>

      {%- comment -%}
      Genera lista de categorías única con conteos
      {%- endcomment -%}
      {% assign cats = "" | split: "" %}
      {% for post in site.posts %}
        {% for c in post.categories %}
          {% assign cdown = c | downcase %}
          {% unless cats contains cdown %}
            {% assign cats = cats | push: cdown %}
          {% endunless %}
        {% endfor %}
      {% endfor %}
      {% assign cats = cats | sort %}

      {% for c in cats %}
        <li><a class="cat-link" data-cat="{{ c }}">{{ c }} <span class="count" data-count-for="{{ c }}"></span></a></li>
      {% endfor %}
    </ul>
  </aside>

</div>

<script>
  const rows = Array.from(document.querySelectorAll(".note-row"));
  const searchInput = document.getElementById("searchInput");
  const sortSelect = document.getElementById("sortSelect");
  const catLinks = Array.from(document.querySelectorAll(".cat-link"));
  const countAll = document.getElementById("countAll");

  let activeCat = "all";

  function matches(row){
    const q = (searchInput.value || "").toLowerCase().trim();
    const title = row.dataset.title.toLowerCase();
    const datePretty = row.dataset.datepretty.toLowerCase();
    const cats = (row.dataset.categories || "");
    const okText = !q || (title.includes(q) || datePretty.includes(q) || cats.includes(q));
    const okCat = (activeCat === "all") || cats.includes(activeCat);
    return okText && okCat;
  }

  function applyFilter(){
    rows.forEach(r => r.style.display = matches(r) ? "" : "none");
  }

  function applySort(){
    const tbody = document.getElementById("notesBody");
    const mode = sortSelect.value;

    const sorted = rows.slice().sort((a,b) => {
      if(mode === "title"){
        return a.dataset.title.localeCompare(b.dataset.title, "es");
      }
      // ordenar por fecha: data-date = YYYY-MM-DD
      if(mode === "oldest"){
        return a.dataset.date.localeCompare(b.dataset.date);
      }
      // newest
      return b.dataset.date.localeCompare(a.dataset.date);
    });

    sorted.forEach(r => tbody.appendChild(r));
  }

  function updateCounts(){
    // cuenta total
    countAll.textContent = `(${rows.length})`;

    // cuenta por categoría
    const counts = {};
    rows.forEach(r => {
      const cats = (r.dataset.categories || "").split(/\s+/).filter(Boolean);
      cats.forEach(c => counts[c] = (counts[c] || 0) + 1);
    });

    document.querySelectorAll("[data-count-for]").forEach(span => {
      const c = span.getAttribute("data-count-for");
      span.textContent = `(${counts[c] || 0})`;
    });
  }

  function setActiveCat(cat){
    activeCat = cat;
    catLinks.forEach(a => a.classList.toggle("active", a.dataset.cat === cat));
    applyFilter();
  }

  // eventos
  searchInput.addEventListener("input", applyFilter);
  sortSelect.addEventListener("change", () => { applySort(); applyFilter(); });

  catLinks.forEach(a => {
    a.addEventListener("click", () => setActiveCat(a.dataset.cat));
  });

  // inicial
  updateCounts();
  applySort();
  applyFilter();
</script>
