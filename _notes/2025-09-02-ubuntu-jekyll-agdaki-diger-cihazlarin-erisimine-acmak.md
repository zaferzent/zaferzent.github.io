---
title: Ubuntu'da yerel cihaz ip'si öğrenme ve jekyll'i ağdaki diğer cihazların erişimine açmak
date: 2025-09-02 00:21
layout: note
type: note
tags: Ubuntu
punlished: false
---
`hostname -I` ile o anki bilgisayarın yerel ip adresini öğreniyoruz. Dah sonra `bundle exec jekyll serve --host=0.0.0.0 --port=4000` komutunu girerek mevcut ağdaki diğer cihazlardan tarayıcıya ip adresi girilerek jekyll blogumuzu canlı test edebiliyoruz. Örneğin benim şuan ki bilgisayarımın Ip'si 192.168.1.109:4000 adresini tarayıcıya girerek jekyll'e erişebiliyorum.
