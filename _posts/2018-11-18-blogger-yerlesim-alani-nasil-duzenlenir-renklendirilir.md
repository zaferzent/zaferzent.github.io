---           
layout: post
title: Blogger yerleşim alanı nasıl düzenlenir, renklendirilir
date: 2018-11-18 10:36:00 UTC
updated: 2022-08-25 19:59:25 UTC
comments: false
categories: Blogger
---
![Blogger yerleşim alanı nasıl düzenlenir, renklendirilir ?](https://lh3.googleusercontent.com/-18vzi7zVy0s/W_FAf7CV_fI/AAAAAAAAGvE/Ob9TAczImuUO5G4osCzVOluD69mnQReHwCEwYBhgL/s1600/blogger-paneli-yerlesim-alani-duzenleme-renklendirme.png)
Son zamanlarda Blogger'da yer alan bileşenlerin eklendiği Yerleşim alanı neden bozuluyor, CSS ile nasıl düzenlenir veya renklendirilir gibi sorular geliyor. Blogger Paneli > Yerleşim alanı gerek şablonlardan, gerek kullanılan kodlardan dolayı bozulma meydana gelebiliyor. Bu bozulmayı düzenlemek veya Yerleşim alanına daha farklı görünüm kazandırmak için aşağıdaki kodlar kullanılabilir. Kodlar ```<head>...</head>``` arasına eklenmelidir.

```<b:template-skin><![CDATA[
body#layout{width:900px; background:transparent; border:none}
body#layout #header{float:left; width:99%; background:#5A7EA2}
body#layout #content{float:left; width:58%; background:#7EC1EC}
body#layout #sidebar{float:left; width:40%; background:gray}
body#layout #footer{float:left; width:99%; background:orange}
body#layout .add_widget{background:#fff; border:none}
body#layout div.section{border:none}
body#layout .editlink{background: #bbb;color: #fff !important;padding: 3px;cursor:pointer;}
]]></b:template-skin>```

Uyarı : Eğer kodlar tam olarak sonuç vermiyorsa, css kodlarında yer alan body#layout dan sonra gelen id seçicileri (#header, #content, #sidebar gibi) kullanınan temaya göre değişkenlik gösterebilir.<br />Bu id ler şablon kodlarında yer alan, alttaki kodda görüleceği gibi section idlerini belirtmektedir. 

Örneğin ;
```<b:section id='sidebar'>``` ID seçicisini tespit etmenin diğer bir kolay yolu ise Yerleşim alanında herhangi bir alan üzerinde sağ tık yapıp Öğeyi İncele veya Öğeyi Denetle yapılarak görülebilir.

![Blogger yerleşim alanı div id seçici](https://lh3.googleusercontent.com/-BqOrZ2snVco/W_FAB1jNGWI/AAAAAAAAGu8/Smn9tuDagu4GDnlJm1lq3rkWqfB2de6VgCEwYBhgL/s1600/blogger-yerlesim-alani-div-id-secici-tespit-etme.png)