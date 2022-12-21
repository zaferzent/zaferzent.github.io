---
published: true
layout: post
date: '2022-12-22 00:40 Europe/Istanbul'
comments: true
categories:
  - Jekyll
tags:
  - jekyll
permalink: /jekyll-yazilarin-rss-beslemesinde-goruntulenmemesi-sorunu
image: assets/images/jekyll-meta-data.jpeg
title: Jekyll Yazıların RSS Beslemesinde Görüntülenmemesi Sorunu
---
![Jekyll RSS Feed]({{site.baseurl}}/assets/images/jekyll-rss-feed.png)Bugün rss beslemesi ile alakalı bir işlem yaparken son yayımladığım iki yazının RSS beslemesinde görüntülenmediğini farkettim. Üzerinde uzun bir düşündüm, uğraştım, araştırdım. Aklıma ilk gelen kodlarla uğraşırken bir hata yapmış olabileceğimdi, ama kodlarla alakalı da bir sorun yoktu. Belki geç görüntülenir diye düşündüm, ama son yazıyı geçtim neden 2 ay önce yayımlanmış bir yazı RSS beslemesine düşmedi. 

Biraz daha araştırma yapmaya karar vedim, yine ve yine Türkçe kaynaklarda bir çözüm bulamadım. Yabancı kaynaklara bakarken yine imdadıma Stackoverflow yetişti. Tabi **[Stackoverflow](https://stackoverflow.com/posts/30625045/revisions)**'da paylaşılan çözüm birebir benim yaşadığım sorun ile alakalı değildi fakat ben uygulayarak işe yaradığını görmüş oldum.

Tek sorun yazı meta data kısmında bir hata yaparak yazıyı taslak olarak bırakmamdan kaynaklıymış. Tabi yazı `_drafts` değil de `_posts` klasöründe olduğundan yazı blogda yayımlanmış fakat RSS beslemesinde yayımlanmamıştı. 

Hem not olarak kalması açısından hem de bu tip sorun yaşayanlara yardımcı olması açısından bu basit ama önemli bir sorunu paylaşmak istedim.

Alttaki resimde görüleceği gibi benim kaldırmayı unuttuğum `draft:true` kısmını kaldırmak gerekiyor. Aksi takdirde yazı blogda yayımlanmış olsa bile RSS beslemesine düşmeyecektir.

![Jekyll Meta Data]({{site.baseurl}}/assets/images/jekyll-meta-data.jpeg)
