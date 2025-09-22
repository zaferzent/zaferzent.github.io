---
layout: default
title: Posts
permalink: /posts/
---
<script>
document.addEventListener("DOMContentLoaded", function() {
  const posts = Array.from(document.querySelectorAll("#post-container .post"));
  const batchSize = 4; // bir seferde gösterilecek post sayısı
  let index = 0;

  // Başlangıçta tüm postları gizle
  posts.forEach(post => post.style.display = "none");

  function showNextBatch() {
    const nextPosts = posts.slice(index, index + batchSize);
    nextPosts.forEach(post => post.style.display = "block");
    index += batchSize;
    if(index >= posts.length) {
      window.removeEventListener("scroll", onScroll);
      document.getElementById("loading").style.display = "none";
    }
  }

  function onScroll() {
    const scrollY = window.scrollY + window.innerHeight;
    const threshold = document.body.offsetHeight - 200; // 200px kala yükle
    if(scrollY > threshold) {
      document.getElementById("loading").style.display = "block";
      setTimeout(() => {
        showNextBatch();
        document.getElementById("loading").style.display = "none";
      }, 200);
    }
  }

  // İlk batch göster
  showNextBatch();

  // Scroll event
  window.addEventListener("scroll", onScroll);
});
</script>

<h1 style="background: #f0f0f0f0;
    padding: 10px;
    margin: 20px;
    border-radius: 10px;">✍️ Posts</h1>

<script>
document.addEventListener("DOMContentLoaded", function() {
  const posts = Array.from(document.querySelectorAll("#post-container .post"));
  const batchSize = 5; // bir seferde gösterilecek post sayısı
  let index = 0;

  function showNextBatch() {
    const nextPosts = posts.slice(index, index + batchSize);
    nextPosts.forEach(post => post.style.display = "block");
    index += batchSize;
    
    // Eğer tüm postlar gösterildiyse butonu gizle
    if(index >= posts.length) {
      document.getElementById("loadMoreBtn").style.display = "none";
    }
  }

  // İlk batch göster
  showNextBatch();

  // Butona tıklandığında
  document.getElementById("loadMoreBtn").addEventListener("click", showNextBatch);
});
</script>



<main>
  <div id="post-container">
    {% assign all_posts = site.posts | sort: "date" | reverse %}
    {% for post in all_posts %}
      <article class="post" style="display:none;">
        <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
        <p>{{ post.excerpt | default: post.content | strip_html | truncatewords: 40 }}</p>
        <span class="meta">✍️ Blog</span>
        <span class="meta">📅 {{ post.date | date: "%d %B %Y" }}</span><span class="meta">📁 
  {% for cat in post.categories %}
     {{ cat }}{% unless forloop.last %}, {% endunless %}
  {% endfor %}
</span>
      </article>
    {% endfor %}
  </div>
  <div style="text-align:center; margin:20px;">
    <button style="    background: #fff;    padding: 10px;    border: 1px solid #ccc;   border-radius: 10px; cursor: pointer;" id="loadMoreBtn">More Posts</button>

  </div>
</main>
