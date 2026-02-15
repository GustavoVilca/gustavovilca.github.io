---
layout: page
title: "Notas"
permalink: /notas/
---


<select id="categoryFilter" style="margin-bottom:15px; padding:5px;">
  <option value="all">Todas las categorías</option>
  <option value="universidad">Universidad</option>
  <option value="analisis">Análisis</option>
  <option value="opinion">Opinión</option>
</select>

<table id="postsTable">
  <thead>
    <tr>
      <th>Título</th>
      <th>Fecha</th>
    </tr>
  </thead>
  <tbody>
  {% for post in site.posts %}
    <tr data-category="{{ post.categories | join: ' ' }}">
      <td>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </td>
      <td>
        {{ post.date | date: "%d %B %Y" }}
      </td>
    </tr>
  {% endfor %}
  </tbody>
</table>

<script>
document.getElementById("searchInput").addEventListener("keyup", function() {
  var filter = this.value.toLowerCase();
  var rows = document.querySelectorAll("#postsTable tbody tr");
  rows.forEach(function(row) {
    var text = row.innerText.toLowerCase();
    row.style.display = text.includes(filter) ? "" : "none";
  });
});
</script>
<script>
document.getElementById("categoryFilter").addEventListener("change", function() {
  var value = this.value;
  var rows = document.querySelectorAll("#postsTable tbody tr");
  rows.forEach(function(row) {
    var category = row.getAttribute("data-category");
    if (value === "all" || category.includes(value)) {
      row.style.display = "";
    } else {
      row.style.display = "none";
    }
  });
});
</script>
