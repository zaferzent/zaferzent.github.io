---
layout: default
title: Photos
permalink: /photos/
---

<h1 style="background: #f0f0f0f0;
    padding: 10px;
    margin: 20px;
    border-radius: 10px;">📷 Photos</h1>

<section class="photo-posts">
  <div class="photo-grid">
    {% assign latest_photos = site.photos | sort: "date" | reverse %}
    {% for photo in latest_photos %}
      <div class="photo-item">
        <a href="{{ photo.url | relative_url }}">
          {% if photo.image %}
            <img src="{{ photo.image }}" alt="{{ photo.title }}">
          {% endif %}
          <h3>{{ photo.title }}</h3>
          {% if photo.location %}
            <p>📍 {{ photo.location }}</p>
          {% endif %}
        </a>
     
       
      </div>
    {% endfor %}
  </div>
</section>
