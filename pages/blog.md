---
layout: index1
permalink: /kategori/blog
title: "Blog"
---


<section class='section blogs' id='blogs'>
  <div class='blog__grid section' id='_posts'>
    
<div class="blog">
  {% for post in site.categories['Blog'] %}
    
      <span class="post-date">{{ post.date | date: '%d.%m.%Y' }}</span>
      
          <h3><a href='{{ post.url | absolute_url }}' title='{{ post.title }}'> {{ post.title }} </a></h3>
     
   
       
    
   
        {{ post.excerpt }}
    
      
   
  {% endfor %}
</div>





  
</div> 
    
  <div class='blog__grid2 section' id='_sidebar'>
    {% include sidebar1.html %}
  </div>
  </section>

