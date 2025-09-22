---
layout: default
title: Bookmarks
permalink: /bookmarks/
---

<h1 style="background: #f0f0f0f0;
    padding: 10px;
    margin: 20px;
    border-radius: 10px;">🔖 Bookmarks</h1>

<main>
{% assign bookmarks = site.bookmarks | sort: "date" | reverse %}
{% for bookmark in bookmarks %}
  <article class="post">
    <h2><a href="{{ bookmark.url | relative_url }}">{{ bookmark.title }}</a></h2>
    <p>{{ bookmark.content }}</p>
    <span class="meta">📅 {{ bookmark.date | date: "%d %B %Y" }}</span>
    {% if bookmark.link %}
      <span class="meta"><a href="{{ bookmark.link }}" target="_blank">🔗 {{ bookmark.title }}</a></span>
    {% endif %}
  </article>
{% endfor %}
</main>
