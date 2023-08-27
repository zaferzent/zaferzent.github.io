---
layout: index1
permalink: /kategori/blogger
title: "Blogger"
---


<section class='section blogs' id='blogs'>




  


<div class="posts">
  {% for post in site.categories['Blogger'] %}
    <article class="post">
      <h1>
          <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
      </h1>
      <div>
        <p class="post_date">{{ post.date | date: "%B %e, %Y" }}</p>
      </div>
      <div class="entry">
        {{ post.excerpt }}
      </div>
      <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">
          Read More
      </a>
    </article>
  {% endfor %}
</div>



 
  <div class='blog__grid2 section' id='_sidebar'>
    {% include sidebar1.html %}
  </div>

</section>
