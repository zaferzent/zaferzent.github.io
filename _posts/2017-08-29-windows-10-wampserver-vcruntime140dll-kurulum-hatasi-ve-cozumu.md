---           
layout: post
title: Windows 10 WampServer VCRUNTIME140.dll Kurulum Hatası ve Çözümü
date: 2017-08-29 21:26:00 UTC
updated: 2022-08-25 21:31:53 UTC
comments: false
categories: Teknoloji
tags:
  - windows
  - kod
---
![Windows 10 WampServer VCRUNTIME140.dll Kurulum Hatası ve Çözümü](https://4.bp.blogspot.com/-b6Atl1Dhocw/WaXJ1lO9AHI/AAAAAAAAGVU/VrV7mREKZzkoNiYmJkAgImqS7r0O3uE0QCLcBGAs/s1600/windows10-wamserver-vcruntimedll-kurulum-hatasi-ve-cozumu.png)
WampServer ile ilgili kurulum hatasına geçmeden önce hakkında bilgi sahibi olmayanlar için özetle WampServer yazılımının ne işe yaradığından bahsetmekte fayda var. WampServer PHP geliştiriciler, kodlayanlar, severler  için hazırlanmış içerisinde MySQL, Apache ve PHP paketlerini barındıran PHP alt yapılı projeleri hazırlayıp test etmeye yarayan bir yazılım. 

WampServer'ı işletim sistemi türüne göre 32bit veya 64 bit indirip kurmak için [WampServer](http://www.wampserver.com/en/){:class="link"}

Not : Kurulum hatası almadan önce hazırlamış olduğum bu yazıya bakmakta fayda var.

**WampServer kurulumunda VCRUNTIME140.dll hatası neden oluşur ve nasıl çözülür ?**

WampServer kurulumunda VCRUNTIME140.dll hatası sadece Windows 10'a özgü olmayıp diğer Windows sürümlerinde de karşılaşılan bir sorun. Fakat diğer Windows sürümlerinde bazı paketlere ihtiyaç duyulmadığından veya WampServer'ın 32bit sürümü kurulduğundan Windows 10'a nazaran daha az meydana geliyor. Sorunun temelinde ise **Microsoft Visual C++** paketlerinin eksik yüklenmesinde yatıyor.  En azından ben hepsini yükleyerek sorunu o şekilde gideriyorum. 

Özetle sorunu yaşamamak veya yaşanan bu sorunu çözmek için alttaki resimde olduğu gibi 2008,2010,2012,2013,2015'in hem 32bit hem de 64bit sürümleri yüklenmeli.

![Microsoft Visual C++](https://3.bp.blogspot.com/-J-DNIX-bdx8/WaXUurJaAHI/AAAAAAAAGVk/cVHaaLX5pOkx6XfLbxFewvt_89r5qpv8wCLcBGAs/s1600/microsoft-visual-c-plus-plus-paketler.png)

Bütün sürümlere ait indirme bağlantılarını Microsoft'un indirme sayfalarında liste halinde bulamadığımdan google'da aratarak hepsini bir araya toplayıp yazıya ekledim. WampServer hatalı bir şekilde yüklendi ve WampServer ikonu turuncu renkte kalıyorsa yüklemeyi kaldırıp Microsoft Visual C++ paketlerinin tümünü yükledikten sonra WampServer'ı tekrar yüklemek gerekiyor.

**Microsoft Visual C++ indirme bağlantıları**

Microsoft Visual C++ 2008 Redistributable Package x86
(https://www.microsoft.com/en-us/download/details.aspx?id=29){:class="link"}

Microsoft Visual C++ 2008 Redistributable Package x64 
(https://www.microsoft.com/en-us/download/details.aspx?id=15336){:class="link"}

Microsoft Visual C++ 2010 Redistributable Package (x86) 
(https://www.microsoft.com/en-us/download/details.aspx?id=5555){:class="link"}

Microsoft Visual C++ 2010 Redistributable Package (x64)
(https://www.microsoft.com/en-us/download/details.aspx?id=14632){:class="link"}

Visual C++ Redistributable for Visual Studio 2012 Update 4 x86-x64
(https://www.microsoft.com/en-us/download/details.aspx?id=30679){:class="link"}

Visual C++ Redistributable Packages for Visual Studio 2013 x86-x64
(https://www.microsoft.com/en-us/download/details.aspx?id=40784){:class="link"}

Visual C++ Redistributable Packages for Visual Studio 2015 x86-x64
(https://www.microsoft.com/tr-TR/download/details.aspx?id=48145){:class="link"}


* 2012, 2013 ve 2015 bağlantılarında hem x86 hem de x64 bulunmakta olup iki farklı sürümlerini de indirmek gerekiyor.<br /><br />