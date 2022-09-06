---           
layout: post
title: Blogger Yazı ve Sayfa Bağlantıları Nasıl Otomatik Kısaltılır
date: 2022-03-07 23:58:00 UTC
updated: 2022-08-26 17:11:37 UTC
comments: false
categories: Blogger
---
![Blogger Yazı ve Sayfa Bağlantıları nasıl Otomatik Kısaltılır ?](https://blogger.googleusercontent.com/img/a/AVvXsEi6WAUAt096eBhP-7txiBMiYoqd4hIzY-Opy6Ttes7vK0QpAxG5jhQxzyHOQP2lKtssU2-orJBERr-rflGVkb6JRHRorbpAMslBGxtZnqGb9F1ZMSW_h9_Iw2zMmAgnYwliZd6U-oj6AOryPLs8_jakmwvsVVTkH7HDj2kUGczJTp491YH-JLwlDomA "Blogger Yazı ve Sayfa Bağlantıları nasıl Otomatik Kısaltılır ?")  
Kenny Cruz arkadaşımızın yapmış olduğu bir BloggerJS javascript eklentisiyle birlikte blogger yazı ve sayfa bağlantılarını kısaltıp sadeleştirebiliyoruz. Daha önce görüp test ettiğim bu eklenti o zamanlar görmüş olduğum bazı eksik veya hatalardan ötürü kullanmaktan ve paylaşmaktan vazgeçmiştim. Fakat bugün tespit ettiğim eksik ve hataları çözüme kavuşturarak paylaşmak istedim. Eklentinin amacı gerek yazı bağlantılarındaki tarih kısmı olsun gerek sayfa bağlantılarındaki /p/ kısmı gibi fazlalıkları olsun bunları kaldırmaya ve daha sade bir görüntü oluşturmamıza olanak sağlıyor. Örneğin yazı bağlantıları **/2021/10/test-yazisi.html** yerine **/test-yazisi** sayfa bağlantıları ise /p/iletisim.html yerine /iletisim biçimine dönüşüyor.  

\\
Bu eklentinin güzelliği kadar bir de eksikliği bulunmakta, bu da bu işlemin sadece blog içinde işe yarıyor oluşu. Sadeleştirilen bağlantılar bir nevi sadece görüntü amaçlı, tam anlamıyla bir blogger kalıcı bağlantı özelliği değil maalesef. Bu eksikliğe gelecek olursam kısaltılan bağlantılar dış siteler veya herhangi bir yerde paylaşıldığında anında yazıya geçiş yapmıyor, önce 404 hata sayfasını gösteriyor, ardından yazıya geçiş yapıyor ve sosyal medya paylaşım önizlemelerinde o yazıya ait bilgiler(yazı resmi ve kısa açıklama) görüntülenmiyor. Bunun da seo açısından olumsuz bir durum oluşturacağını düşünüyordum.  

\\
Bu gece uğraşırken biraz da şans eseri diyeyim bu 404 hata sayfası ve paylaşım önizlemeleri göstermeme sorununu bir nevi çözdüm. Tabi seo açısından olumsuz bir durum olur mu orasını bilemiyorum, en azından dışardan bağlantıya tıklandığında 404 hata sayfasını göstermemesini ve sosyal medyada paylaşımında yazı önizlemelerinin ortaya çıktığını farkettim. Bu çözüme ulaşma sebebim ise eklentiyi test ederken menüdeki sayfa bağlantılarına tıklayınca farkettim. Bazı bağlantılarına tıkladığımda 404 sayfasını göstermediğini gördüm. Sonra aklıma eskiden yapmış olduğum bazı 301 yönlendirmeleri geldi ve o yüzden sorun oluşmadığını tespit etmiş oldum. Örneğin ben daha önce /p/blogger-kod-donusturucu.html bağlantısını menülerde kısa şekilde kullanmak için /blogger-kod-donusturucu şeklinde oluşturup bu oluşturduğum kısa bağlantıyı orijinal bağlantıya yönlendirme yapmışım ve bu sayede bu bağlantıya tıklayınca 404 hata sayfasını göstermeden direkt sayfayı açıyor ve sosyal medyada kısa bağlantıyı paylaştığımda bu sayfaya ait önizleme sorunsuz bir şekilde çıkıyor.  

\\
Eklentiyi temaya ekledikten sonra tabi ki tüm yazı ve sayfaların kısaltılan bağlantıları örijinal bağlantılara yönlendirilmek gerekiyor. Bu 301 yönlendirmesini(kalıcı bağlantı yönlendirmesi) Blogger'da Ayarlar > Hatalar ve yönlendirmeler > Özel yönlendirmeler kısmından yapıyoruz. Tüm içeriklerin gerekli yönlendirmeleri yapıldıktan sonra kısaltılan bağlantı istenilen yerde paylaşılabilir ve sorunsuz bir şekilde çalıştığı görülebilir.  

\\
**Uyarı** : Bazı kaynaklarda bu bağlantı kısaltma işlemi yapıldıktan sonra arama motoru sıralamalarında değişlik olacağı ve ziyaretçi kaybı olacağı belirtilmiş. O yüzden bunu göz önünde bulundurarak bu işlemi uygulamalısınız.  

\\
Eklenti kodları (Eklenti adresi : [https://github.com/jokenox/bloggerjs](https://github.com/jokenox/bloggerjs).)  
Aşağıdaki kodları <head> başlangıç etiketi sonrasına ekliyoruz.  
<pre style="background:#eee"><code>&lt;script type='text/javascript'&gt;
var config={postsDatePrefix:!1,accessOnly:!1,useApiV3:!1,apiKey:&quot;YOUR-API-KEY-HERE&quot;}
var postsOrPages=[&quot;pages&quot;,&quot;posts&quot;],blogId=&quot;&lt;data:blog.blogId/&gt;&quot;,urlTotal,fetchIndex=1,ampChar=&quot;&amp;amp;&quot;[0],secondRequest=!0,feedPriority=0,nextPageToken;function urlVal(){var url=window.location.pathname;var length=url.length;var urlEnd=url.substring(length-5);if(urlEnd===&quot;.html&quot;)return 0;else if(length&gt;1)return 1;else return 2}
function urlMod(){var url=window.location.pathname;if(url.substring(1,2)===&quot;p&quot;){url=url.substring(url.indexOf(&quot;/&quot;,1)+1);url=url.substr(0,url.indexOf(&quot;.html&quot;));history.replaceState(null,null,&quot;../&quot;+url)}else{if(!config.postsDatePrefix)url=url.substring(url.indexOf(&quot;/&quot;,7)+1);else url=url.substring(1);url=url.substr(0,url.indexOf(&quot;.html&quot;));history.replaceState(null,null,&quot;../../&quot;+url)}}
function urlSearch(url,database){var pathname=url+&quot;.html&quot;;database.forEach(function(element){var search=element.search(pathname);if(search!==-1)window.location=element})}
function urlManager(){var validation=urlVal();if(validation===0){if(!config.accessOnly)urlMod()}else if(validation===1){fetchData(postsOrPages[feedPriority],1)}else if(validation===2){if(!config.accessOnly)history.replaceState(null,null,&quot;/&quot;)}}
function fetchData(postsOrPages,index){var script=document.createElement(&quot;script&quot;);if(config.useApiV3){var jsonUrl=&quot;https://www.googleapis.com/blogger/v3/blogs/&quot;+blogId+&quot;/&quot;+postsOrPages+&quot;?key=&quot;+config.apiKey+&quot;#maxResults=500#fields=nextPageToken%2Citems(url)#callback=parseData&quot;;if(nextPageToken)jsonUrl+=&quot;#pageToken=&quot;+nextPageToken;nextPageToken=undefined}else{var jsonUrl=window.location.protocol+&quot;//&quot;+window.location.hostname+&quot;/feeds/&quot;+postsOrPages+&quot;/summary?start-index=&quot;+index+&quot;#max-results=150#orderby=published#alt=json-in-script#callback=parseData&quot;}
jsonUrl=jsonUrl.replace(/#/g,ampChar);script.type=&quot;text/javascript&quot;;script.src=jsonUrl;document.getElementsByTagName(&quot;head&quot;)[0].appendChild(script)}
function parseData(json){var database=[];if(!config.useApiV3){if(!urlTotal){urlTotal=parseInt(json.feed.openSearch$totalResults.$t)}
try{json.feed.entry.forEach(function(element,index){var entry=json.feed.entry[index];entry.link.forEach(function(element,index){if(entry.link[index].rel===&quot;alternate&quot;)database.push(entry.link[index].href)})})}catch(e){}}else{try{json.items.forEach(function(element,index){database.push(element.url)})}catch(e){}
nextPageToken=json.nextPageToken}
urlSearch(window.location.pathname,database);if(urlTotal&gt;150){fetchIndex+=150;urlTotal-=150;fetchData(postsOrPages[feedPriority],fetchIndex)}else if(nextPageToken){fetchData(postsOrPages[feedPriority])}else if(secondRequest){nextPageToken=undefined;urlTotal=0;fetchIndex=1;secondRequest=!1;if(feedPriority===0){feedPriority=1;fetchData(&quot;posts&quot;,1)}else if(feedPriority===1){feedPriority=0;fetchData(&quot;pages&quot;,1)}}}
function bloggerJS(priority){if(priority)feedPriority=priority;urlManager()}
bloggerJS()
&lt;/script&gt;</code></pre>

Örneğin resimdeki gibi kısaltılmış bağlantı üste orijinal bağlantı da alt satıra eklenip son adımda Kaydet'e tıklayarak işlemi bitirmek gerekiyor. Kaydet'e tıklanmazsa yönlendirme işlemi tamamlanmayacaktır.  
![Blogger bağlantı yönlendirme](https://blogger.googleusercontent.com/img/a/AVvXsEjyupXEabRZEpsNr9md5Yu146526kkJg5idOo45UXkGuBi0_v2RoKcllLTLiEgAB2-eDMgWb--OZ3AgRFPXnBSS4Yv3gkfce0_I4AFOFniXtzZ5CBYkaFiHVGMTY9DR_4q3bEFxYZurykdmpwwI1Irzu51e9lJ3FFo4C6HGw7PGptyuG_2Huaz3FEV8)