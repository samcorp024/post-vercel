---
layout: default
permalink: /categories/
---

<h1>Categories</h1>

<div class="categories-container">
  {% for category in site.data.categories %}
    {% assign category_name = category[0] | slugify %}
    <div class="category-card">
      <img src="{{ category[1].image }}" alt="{{ category_name | capitalize }} category image">
      <h2><a href="/jekyll/categories/{{ category_name }}/">{{ category_name | capitalize }}</a></h2>
      <p>{{ category[1].description }}</p>
    </div>
  {% endfor %}
</div>




<!-- ---
layout: default
permalink: /categories/
---

<h1>Categories</h1>

<div class="categories-container">
  {% for category in site.categories %}
    {% assign category_name = category[0] | slugify %}
    <div class="category-card">
      <img src="{{ site.data.categories[category_name].image }}" alt="{{ category[0] | capitalize }} category image">
      <h2><a href="/jekyll/categories/{{ category_name }}/">{{ category[0] | capitalize }}</a></h2>
      <p>{{ site.data.categories[category_name].description }}</p>
    </div>
  {% endfor %}
</div> -->
