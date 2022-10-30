---
published: true
layout: post
date: '2022-10-30 00:40 Europe/Istanbul'
comments: true
categories:
  - Blogger
  - Jekyll
tags:
  - jekyll
  - blogger
  - blogspot
permalink: /bloggerdan-jekylle-gecis-sureci
draft: true
title: Blogger'dan Jekyll'e Geçiş Süreci
image: assets/images/jekyll.png
---
![Jekyll]({{site.baseurl}}//assets/images/jekyll.png)

Yakın zamanda uzun ve zorlu bir süreç sonunda Blogger'dan Jekyll'e geçiş yapmıştım ve konu ile alakalı kısa bir bilgilenedirme paylaşmıştım. Bu yazımda ise nasıl geçiş yaptım, nasıl sorunlarla karşılaştım, iyi mi yaptım, kötü mü yaptım ile alakalı elim döndüğünce rehber niteliğinde bir şeyler paylaşacağım.
<br />

Jekyll Nedir ?
------
[Jekyll](https://jekyllrb.com) statik bir site oluşturucu yazılımı. Statikten kasıt bir veritabanı sistemi ve bir yönetim paneli gibi argümanların bulunmaması. İçerikler oluşturulurken markdown formatında oluşturuluyor(Markdown HTML etiketlerine göre daha kısa ve kolay bir kullanım sağlıyor) ve Jekyll bunu HTML sayfalara dönüştürek içeriğin görüntülenmesini sağlıyor. Markdown hakkında bilgi almak ve HTML'den farkı nedir öğrenmek için [Markdown](https://tr.wikipedia.org/wiki/Markdown){:class="link"} adresine bakılabilir.
<br />

Neden Jekyll'e Geçiş Yaptım ?
------
Daha önce de [Bloğumu Taşıyorum](/2022/08/blogumu-tasiyorum.html) yazısında belirttiğim gibi Blogger'ın bir türlü gerek şablon yapısı gerek diğer geliştirmeler olsun artık çok geride kalması oldu. Tabi burada en önemli sebep Google'un herhagi bir kazanç sağlamadığı bir servis için çok fazla destek veya geliştirme yapmasını beklemiyorduk. Fakat en azından biraz daha fazla özgürlük sağlayabilirdi.
<br />Ayrıca son zamanlarda artık bir değişikliğe gitmenin zamanın geldiğini iyiden iyiye düşünmeye başlamıştım ve bu süreçte Statik site oluşturuculara merakım hayli ile artmıştı. 
<br />Jekyll, Hugo, Hexo gibi statik site oluşturucularını son zamanlarda inceleme ve test etme fırsatım oldu. Bunlardan özellikle Jekyll bana daha cazip geldi.
<br />

Adım adım Jekyll'e Geçiş Rehberi ?
------
Aslında en ince ayrıntısına kadar tüm süreci yazmak isterdim fakat araya giren zaman sorunu nedeni ile yararlandığım kaynaklar ve nasıl bir yol izledim, nasıl sorunlarlarla karşı karşıya kaldım ve bunları nasıl çözüme ulaştırdım özet bir şekilde onlardan bahsedeceğim.
<br />

1 - Jekyll kurulum ve github üzerinde yayına alma
------
Jekyll'in kurulumu ve github üzerinde yayına almak için çok fazla kaynak var. Ben ingilizce veya Türkçe dilinde çokla fazla kaynak inceledim. Fakat ingilizce kaynaklarla çok fazla zaman kaybetmek istemiyorsanız youtube üzerinde bulunan ve gayet anlaşılır bir anlatıma sahip olan [Yazılım - DEV](https://www.youtube.com/channel/UCinNBqUVs98p-t-fzJ870HA/videos){:class="link"} kanalının videolarından yararlanabilirsiniz.
<br />Ek olarak kurulum ve zaferzent.github.io şeklinde yayına alma işleminden sonra iki farklı kaynaktan yararlandım bunlar :

- **[How to add custom domain to your jekyll blog - provided that you built your site using github pages
](https://medium.com/@xiang_zhou/how-to-add-custom-domain-to-your-jekyll-blog-provided-that-you-built-your-site-using-github-6e1c8bf20afe)**

- **[Managing a custom domain for your GitHub Pages site](
https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)**
<br />

2 - Blogger yazılarını Jekyll'e Uygun(markdown olarak) dışarı aktarma
------
Bu aşama için **[dev.to/rupeshtiwari/importing-wordpress-or-blogger-blogs-to-jekyll-blog-mpg](https://dev.to/rupeshtiwari/importing-wordpress-or-blogger-blogs-to-jekyll-blog-mpg)** adresindeki yazıdan yararlandım. Bu yazıda yer alan migrate.rb betiği bir nimet niteliğinde çünkü bulduğum bir çok diğer araç veya betik hep sorun çıkardı. Fakat bu betiğin bazı eksik veye hatalı yönleri bulunuyordu biraz uğraşarak bunları giderdim.<br />
Migrate.rb betiğinin düzelttiğim eksiklikleri veya sorunları : 
<br />**a - Kalıcı bağlantı sorunu**
Migrate.rb betiği ingilizce dili hesap edilerek yazıldığı için doğal olarak kalıcı bağlantılarda Türkçe karakter sorunu yaşatıyordu. Yani "Fıstıkçı Şahap" başlığına sahip bir yazımız varsa bunun bağlantısını "fstk-ahap" şeklinde eksik ve hatalı bir şekilde oluşturuyordu. Artık düzgün bir şekilde çalışıyor.
<br />**b - Eksik dışarı aktarma işlemi**
Orjinal betikte en fazla 25 yazı dışarı aktarılabiliyordu ve ben 200ün üzerinde yazıya sahiptim. Ben bunu farklı bir yöntem kullanarak düzeltme işlemi yaptım. **zaferzent.com/feeds/posts/default/-/Blogger?orderby=updated&max-results=9999** etiket besleme adresi üzerinden dışarı aktarma işlemi yaptım. Betik içerisindeki besleme adresi ve betik çalıştırılırken girilen besleme adresi aynı olmalı.
<br />Betik kullanımı dev.to adresi ile baylaştığım yazıda mevcut. Özet olarak Komut istemi üzerinden çalıştıran komuttaki besleme adresi betik içerisindeki besleme adresi aynı olacak ve ruby **migrate.rb https://www.zaferzent.com/feeds/posts/default/-/Blogger?orderby=updated&max-results=9999** olarak komut çalıştırılacak. Diğer önemli bir konu varolan blogger bloğundaki tüm yazılar etikete sahip olmalı ve etiket sayısı mümkün olduğunca az ve etiketlerde Türkçe karakter olmamalı. Çünkü her etikete ait yazıları ayrı ayrı betik dosyasına eklenerek ve komut verilerek dışarı aktarma işlemi yapılıyor.
<br />**c - Yazı tarih sorunu**
Yazının ilk yayınlanma tarihini değil de güncellenme tarihini çekiyordu bu yüzden kalıcı bağlantılar oluşturulurken hata meydana geliyordu ben bunu ilk yayınlanma tarihi olarak değiştirdim.
<br />Blogger sabit sayfalarını dışarı aktarmak için kullanılacak feed adresi **zaferzent.com/feeds/pages/default**<br />
Migrate.rb dosyasını github adresimden indirebilirsiniz : [migrate.rb](https://github.com/zaferzent/migrate.rb){:class="link"}
<br />

3 - Blogger Yorumlarını Disqus'a, Disqus'tan Jekyll'e Aktarma
------
Jekyll'de kullanılabilecek bir yorum sistemi olan Disqus hali hazırda Blogger için de kullanılabiliyor. Ben daha önceleri kurup test etme fırsatı bulmuştum. Fakat blogger yorum sistemini kullanmaya devam ettim. Jekyll'e geçiş yaptıktan sonra doğal olarak Disqus'u kullanmaya başladım. Burada önemli nokta Disqus destekli bir Jekyll temasını kullanmak. Blogger yorumlarını **[Disqus Import](https://disqus.com/admin/discussions/import/platform/blogger/)** sayfasından blogger yorumlarını disqus'a aktardım. Daha sonrasında Jekyll'e çektim. 
<br />Yorumları Disqus'a aktarmadaki önemli konu ise varolan blog adresi ve disqus'a eklenen site adresi aynı olması gerekiyor. Eğer blogadi.blogspot.com adresinden özel alan adı alınıp öyle Jekyll'e geçiş yapılacaksa önce blogspot adresi özel alan adına yönlendirilmeli ondan sonra yorumlar Disqus'a aktaralıp daha  Jekyll'e taşıma işlemini yapmak gerekiyor. Çünkü Disqus url bazlı çalışıyor.
<br />

4 - 404 hata sayfaları
------
Yaşadığım diğer sorunlardan birisi de yazı bağlantılarından dolayı 404 hata sayfası almam oldu. Bunun sorunun nedeni betik(migrate.rb) blogger'daki yazıların bağlantılarını değil de yazı başlıkları üzerinden dönüştürme yapması ve yazı başlığı ne ise ona göre yeni bir bağlantı oluşturmasıydı. Örneğin yazı başlığı "Blogger Sade Omega Teması" olan fakat kalıcı bağlantısı /blogger-omega-temasi.html olan bir yazı dönüştürme işlemi sonunda yeni bağlantıyı /blogger-sade-omega-temasi.html olarak oluşturuyor ve dolayısı ile 404 hata sayfası oluşuyordu. Ben de çözüm olarak yazı başlıklarını manuel olarak bağlantı ile aynı yaptım.
<br />

5 - Tema Uyarlama
------
Jekyll'de tema seçeneği çok fakat bir çoğu aynı yapıdalar. Ben de uygun, kullanışlı bir tema bulamayınca hali hazırda Blogger'da kullandığım temayı uyarlayıp kullanmaya başladım. Jekyll tema yapısı biraz farklı, aslında kolay bir yapısı olmasına rağmen tecrübesizlikten dolayı biraz uğraşmak zorunda kaldım.
<br />Genel olarak geçiş sürecinde not aldığım ve aklıma gelenler bunlar, eksiklikler olabilir zaman geçtikçe aklıma gelen bir şeyler olursa ekleme yapabilirim. Blogger'dan Jekyll'e geçmek isteyenler için umarım faydalı bir içerik olmuştur.
