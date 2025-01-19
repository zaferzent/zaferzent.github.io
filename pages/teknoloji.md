---
layout: index1
permalink: /kategori/teknoloji
title: "Teknoloji"
---


<section class='section blogs' id='blogs'>
  <div class='blog__grid section' id='_posts'>
    
{% include breadcrumbs.html %}

  {% for post in site.categories['Teknoloji'] %}
    <div class="blog">
      <span class="post-date">{{ post.date | date: '%d.%m.%Y' }}</span>
      
          <h3><a href="{{ post.url | absolute_url }}" title="{{ post.title }}"> {{ post.title }} </a></h3>
     
   
       
    
   
        {{ post.excerpt }}
    
   </div>   
   
  {% endfor %}






  
</div> 
    
  <div class='blog__grid2 section' id='_sidebar'>
    {% include sidebar1.html %}
  </div>
  </section>

