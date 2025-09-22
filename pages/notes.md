---
layout: default
title: Notes
permalink: /notes/
---

<h1 style="background: #f0f0f0f0;
    padding: 10px;
    margin: 20px;
    border-radius: 10px;">🗒️ Notes</h1>

<main>
{% assign notes = site.notes | sort: "date" | reverse %}
{% for note in notes %}
  <article class="post">
    <p>{{ note.content }}</p>
 
    <span class="meta">📅 <a href="{{ note.url | relative_url }}">{{ note.date | date: "%d %B %Y" }}</a></span>

  </article>
{% endfor %}
</main>
