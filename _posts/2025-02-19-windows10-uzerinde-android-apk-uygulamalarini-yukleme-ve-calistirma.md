---
layout: post
date: '2025-02-19 00:47 Europe/Istanbul'
categories:
  - Teknoloji
tags:
  - windows
  - android
  - google
permalink: /windows10-uzerinde-android-apk-uygulamalarini-yukleme-ve-calistirma
image: assets/images/windows10-uzerinde-android-uygulamalari-calistirma.jpg
title: Windows 10 Üzerinde Android(APK) Uygulamalarını Yükleme ve Çalıştırma
---
![windows 10 üzerinde android apk uygulamalarını yükleme ve çalıştırma](/assets/images/windows10-uzerinde-android-uygulamalari-calistirma.jpg)
Yakın zamana kadar yaşadığım sorunlar nedeniyle  Windows 11'den **Windows 10**'a geri dönüş yapmıştım. Windows 11 üzerinde birkaç aktif kullandığım **Android** uygulaması vardı. Windows 10 üzerinde de bu uygulamaları kullanmaya devam edeyim derken, daha önceleri sanal olarak Hackintosh'a kadar kurup kullanmış birisi olarak bu işlemin Windows 10'da neden bu kadar uğraştırıcı olduğunu anlam veremedim. Android uygulamalarını kullanmak için halihazırda Emulator programları var fakat ben pek tercih etmediğimden o yöntemi kullanmak istemedim.

Windows 11'de **Microsoft Store** üzerinden **WSATools** kurularak aslında bu işlem kısa sürede yapılabiliyordu, belki başka bir işlem de vardır fakat ben yaptığımı hatırlamıyorun. Windows 10'da mağazada WSATools için minimum sistem gereksinimleri karşılamıyor diye uyarı veriyor ve uygulama kurulumuna izin vermiyor. Ben de biraz araştırma yaparak bunun çözümünü toplayıp, derleyip özet olarak paylaşmak istedim. Çok ayrıntıya girmiyorum, pek anladığınız konular değilse program kurulumları için Youtube üzerinden yardım alabilirsiniz.

Neyse gelelim konumuza. Şimdi Windows 10 üzerinde Android uygulamalarını kurup kullanabilmek için iki program yüklemek gerekiyor.

Bunlardan birincisi WSA Tools - **Windows Subsystem for Android Tools** (**Android için Windows Alt Sistemi**) programı. Bu program sayesinde Android uygulamalarını Windows 10 üzerinde çalıştırabiliyoruz. Ayrıca **Google Play**'de bu program ile
birlikte yüklü geldiği için direkt olarak Google Play üzerinde de Android uygulamaları yüklenebiliyor.

**WSA Tools - Windows Subsystem for Android Tools (Android için Windows Alt Sistemi) İndirme ve Yükleme**

Bu programı yüklemek için gerekli adres : [WSA Tools](https://github.com/MustardChef/WSABuilds)

Bu adreste resimde görülen (Download Latest Stable Builds - Windows 10 x64) olana tıklıyoruz.

![wsa tools indirme](/assets/images/wsa-tools-indirme.png)

Açılan sayfada ise en altta bulunan Assets kısmından ben ikinci olanı indirdim ve yükledim. Tercih kullanıcıya bağlı fakat benim yüklediğim bu sürüm içerisinde Google Play uygulaması da hazır olarak geliyor.

![wsa tools indirme 2](/assets/images/wsa-tools-indirme-2-asama.png)

Zip dosya türünde indirilen WSA Tools programı zipten çıkartıp run.bat dosyası çalıştırılarak kurulumu yapıyoruz.

![wsa tools yükleme](/assets/images/wsa-tools-yukleme.png)

Windows 10 üzerinde Google Play Görünümü

![windows 10 google play](/assets/images/windows10-google-play.png)

**İkinci olarak kuracağımız program : ADB(Android Debug Bridge) Installer - (Android Hata Ayıklama Köprüsü Kurulumu)**

Bu programın bize sunduğu güzellik ise indirdiğimiz **Android** uygulama uzantısı olan **.apk** dosyalarını kurmamızı sağlıyor.

Bu programı indirmek için kullanacağımız adres : [ADB Installer](https://xiaomitools.com/adb-installer/) Benim bu yazıyı hazırladığım sıralarda ben son sürüm olan **ADB Installer v1.5.6**'yı yükledim.

![adb installer indirme](/assets/images/adb-installer-indirme.png)

Buradan indirilen zip formatlı dosyayı yine zipten çıkartarak **15 Second ADB Installer v1.5.6.exe** tıklatarak açılan yükleme ekranında Y/N şeklinde sorulan soruların hepsine Y yazıp enter geçişi yaparak kurulumu tamamlıyoruz.

![adb installer yükleme](/assets/images/adb-installer-yukleme.png)

ADB yi aktif etme ve APK dosya kurulumu :

Öncelikle başlatta **Windows Alt Sistemini** arayıp bularak çalıştırın. Açılan ekranda alttaki resimde görebileceğiniz gibi **Geliştirici Modunu**'nu aktif ediyoruz.

![wsa tools geliştirici modu aktif etme](/assets/images/wsa-tools-gelistirici-modu-aktif-etme.png)

Windows Komut istemini açıp **adb connect 127.0.0.1:58526** komutunu girerek adb'yi çalıştırıyoruz.

APK dosya kurulumu için apk dosyasını hangi dizine indirdiyseniz o dizine girerek(örneğin İndirilenler klasöründeyse cd Downloads) 

**adb install androiduygulama.apk** komutunu çalıştırarak apk kurulumu tamamlıyoruz.

Aşağıdaki resimde benim örnek kurulumum görebilirsiniz.

![adb ile apk kurulum](/assets/images/adb-ile-apk-kurulum.png)

Son olarak başlatta yüklemiş olduğunuz Android uygulamasını aratıp çalıştırarak sonucu görüyoruz.

