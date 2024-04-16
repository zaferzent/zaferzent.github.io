---           
layout: post
title: Blogger anonim yorum yazarlarının avatarı nasıl değiştirilir
date: 2021-10-30 09:48:00 UTC
updated: 2022-08-26 17:11:59 UTC
comments: false
categories: Blogger
permalink: /blogger-anonim-yorum-yazarlarinin-avatari-nasil-degistirilir
---
![Blogger anonim yorum yazarlarının avatarı nasıl değiştirilir ?](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiOonOI9uM-1tDaDdyPASd_Xbk4nliwmFN3IRSDvf-Rn4k-IW5KAMfnNIMkZCd3nq0BiBmToLsrDcZe35Udvmjhy1qNs-tZmD1VJkTA94OKHiQ80wk1fIM-5vhJiQpYSTXwlYGsNvruN1iI0L6yJeKXenUHb8NtaccJrlIkg7_VBhpCsGA6M5G0yKYK/s1600/blogger-anonim-yorum-yazarlarinin-avatari-nasil-degistirilir.webp "Blogger anonim yorum yazarlarının avatarı nasıl değiştirilir ?") Blogspot/Blogger'da anonim yorum yazarlarının avatarları eskiden standart bir blogger logosu olarak görüntüleniyordu, fakat daha sonraları boş bir avatar olarak görünmeye başladı. Ben bunu daha önceleri de kullanmış olduğum ve bu kısa yazıda paylaştığım basit bir javascript kodu ile düzeltiyordum.  

Peki **blogger anonim yorum yazarlarının avatarı nasıl değiştirilir ?**  

/body> bitiş etiketinin hemen üzerine aşağıdaki kodlar eklenerek anonim yorum yazarlarının boş görüntülenen avatarı değiştirilmiş olacaktır. İsteğe göre user.png avatarı değiştirilebilir.  

<pre style="background:#eee"><code>&lt;script type=&quot;text/javascript&quot;&gt;  
  (function() {  
    var avatars = document.getElementsByClassName(&quot;avatar-image-container&quot;);  
    for (i=0; i &lt; avatars.length; i++) {  
      var image = avatars\[i\].firstChild;  
      if (image.src === 'https://resources.blogblog.com/img/blank.gif' || image.src === 'http://resources.blogblog.com/img/blank.gif') {  
        image.src = 'https://2.bp.blogspot.com/-sotlqCwyIRA/V1fnW27MZfI/AAAAAAAAx9A/a45uloW8Y2IH256dKnpZGIwNlJ1TeBuQgCLcB/s1600/user.png';  
        image.style.height='36px';  
        image.style.width='36px';  
      }  
    }  
  })();  
&lt;/script&gt;</code></pre>

Uyarı : Şablonunuzda jquery kütüphanesi dahil edilmiş olmalıdır.  

Bloger yorum avatarları hakındaki işinize yarayabilecek **[Blogger yorum yazarlarının avatar boyutu nasıl değiştirilir ?](https://www.zaferzent.com/2017/05/blogger-yorum-yazarlarinin-avatar-boyutu-nasil-degistirilir.html "Blogger yorum yazarlarının avatar boyutu nasıl değiştirilir ?")** ve **[Blogger çok yazarlı bloglarda yazar adı ve fotoğrafı nasıl gösterilir ?](https://www.zaferzent.com/2019/05/blogger-cok-yazarli-bloglarda-yazar-adi-ve-fotografi-nasil-gosterilir.html "Blogger çok yazarlı bloglarda yazar adı ve fotoğrafı nasıl gösterilir ?")** başlıklı yazılarıma da göz atabilirsiniz.
