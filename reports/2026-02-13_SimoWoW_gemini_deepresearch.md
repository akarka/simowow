# **Dünya çapında World of Warcraft Simülasyon Ekosistemi: SimoWoW Mobil Lonca Yönetimi İçin Mimari, Teknolojik ve Fonksiyonel Analiz Raporu**

Modern devasa çevrimiçi çok oyunculu rol yapma oyunları (MMORPG) içerisinde World of Warcraft (WoW), yalnızca oyuncu sayısıyla değil, aynı zamanda oyun mekaniklerinin karmaşıklığı ve bu mekanikleri optimize etmek için geliştirilen topluluk tabanlı hesaplama araçlarıyla da benzersiz bir konuma sahiptir. SimoWoW projesi kapsamında geliştirilecek mobil lonca yönetimi platformu, bu karmaşık veri yapılarını ve simülasyon çıktılarını son kullanıcıya mobil cihazlar üzerinden sunmayı amaçlamaktadır. Bu rapor, WoW simülasyon dünyasının temel taşları olan SimulationCraft, Raidbots ve Wowsims platformlarını mimari, teknolojik ve fonksiyonel açılardan analiz ederek, projenin başarısı için kritik olan hesaplama yöntemleri ve kullanıcı akışlarını detaylandırmaktadır.

## **Simülasyonun Evrimi: Formülasyondan Dinamik Modellemeye**

Oyunun ilk yıllarında karakter optimizasyonu, genellikle statik formüller ve "kapalı form" yaklaşımları üzerinden yürütülmekteydi. Bu yöntemlerde, bir yeteneğin ortalama hasarı, belirli bir zaman dilimindeki tetiklenme olasılıkları ile çarpılarak sabit bir değer elde edilmekteydi.1 Ancak, sınıflar arası sinerjilerin artması, rastgele tetiklenen (proc-based) mekaniklerin karmaşıklaşması ve oyuncu seçimlerine dayalı dinamik rotasyonların devreye girmesi, bu basit hesap makinelerinin doğruluğunu ciddi şekilde aşındırmıştır.2 Bu noktada devreye giren simülasyon araçları, problemi matematiksel bir ortalama olarak değil, binlerce kez tekrarlanan sanal bir dövüş süreci olarak ele almaktadır.2

SimulationCraft (SimC) ve Wowsims gibi araçlar, Monte Carlo yöntemlerini kullanarak dövüşün her saniyesini olay bazlı bir yapıda simüle eder.2 Bu yaklaşım, sadece "ortalama" hasarı değil, aynı zamanda hasar dalgalanmalarını (variance), şans faktörünün etkisini ve en kötü durum senaryolarını da ortaya koymaktadır.5 SimoWoW projesi için bu ayrım hayati önem taşımaktadır; çünkü lonca yöneticileri için bir oyuncunun sadece teorik potansiyeli değil, aynı zamanda bu potansiyele ne kadar tutarlı bir şekilde ulaşabildiği bilgisi de stratejik bir değer taşır.

## **SimulationCraft: Motorun Mimarisi ve C++ Temelleri**

SimulationCraft, WoW topluluğu tarafından geliştirilen, açık kaynaklı ve C++ dilinde yazılmış çok oyunculu, olay güdümlü bir simülatördür.1 Motorun temel amacı, doğruluk açığını kapatırken, eşya seçimi ve stat ağırlıklarının hesaplanması için yeterli performans düzeyini korumaktır.2

### **Katmanlı Mimari ve Sınıf Yapısı**

SimC'nin mimarisi, dövüşün her bir bileşenini nesne yönelimli programlama prensipleriyle modelleyen katmanlı bir yapıya sahiptir.7 Bu yapı, yeni genişleme paketleri ve sınıf değişiklikleri geldiğinde motorun hızla güncellenmesine olanak tanır.

* **Simülasyon Katmanı (sim\_t):** Bu katman, programın en üst seviyesidir ve tüm simülasyon sürecini yönetir. Kullanıcıdan gelen seçenekleri ayrıştırır, oyuncuları ve düşmanları oluşturur, zaman tekerleğini (timing wheel) kontrol eder ve dövüşün başlangıç/bitiş anlarını yönetir.7  
* **Oyuncu Katmanı (player\_t):** Her bir karakteri temsil eden bu katman; yetenekler, eşyalar, bufflar, kaynaklar (mana, enerji, öfke) ve istatistikler hakkındaki tüm bilgileri barındırır.7 Oyuncunun dövüş içindeki tüm durumu bu nesne üzerinden takip edilir.  
* **Eylem Katmanı (action\_t):** Tüm yeteneklerin ve büyülerin temelini oluşturur. Hasar katsayıları, bekleme süreleri (cooldown), kaynak maliyetleri ve çarpma anı (impact) gibi specification verilerini içerir.7

### **Olay Güdümlü Simülasyon ve Zaman Tekerleği**

SimC, zamanı sürekli bir akış olarak değil, kesikli olaylar zinciri olarak işler.8 "Olay güdümlü" (event-driven) yapıda zaman, bir olaydan diğerine sıçrayarak ilerler. Örneğin, bir büyü yapıldığında, motor bir sonraki saniyeyi beklemek yerine, büyü etkisinin gerçekleşeceği milisaniyeye doğrudan atlar.8 Bu durum, hesaplama yükünü dramatik şekilde azaltarak saniyeler içinde binlerce dövüşün simüle edilmesini sağlar.5

| Mimari Bileşen | Fonksiyonel Görev | Teknolojik Karşılık |
| :---- | :---- | :---- |
| Timing Wheel | Olayların kronolojik yönetimi.7 | Priority Queue Veri Yapısı. |
| APL Parser | Rotasyon mantığının işlenmesi.10 | Özel Betik Dili (DSL). |
| Data Extractor | Oyun dosyalarından veri çekimi.11 | Python (dbc\_extract.py). |
| Reporter | Sonuçların görselleştirilmesi.5 | HTML/JSON Çıktı Üreteci. |

### **Eylem Öncelik Listesi (APL) ve Karar Mekanizması**

SimulationCraft'ın beyni olarak kabul edilen APL, bir karakterin dövüş sırasında hangi yeteneği ne zaman kullanacağını belirleyen karmaşık bir öncelik listesidir.10 APL, statik bir rotasyon değildir; her an değişebilen koşullara (hedef sağlığı, buff süreleri, kaynak miktarı) göre dinamik olarak karar verir.10

Motor, her Global Cooldown (GCD) sona erdiğinde veya oyuncu boşta kaldığında APL'yi yukarıdan aşağıya doğru tarar.10 İlk uygun eylem (koşulları sağlanan ve bekleme süresi dolmuş olan) seçilir ve işlenir.10 SimoWoW projesi kapsamında, bu mantığın mobil arayüzde nasıl temsil edileceği, oyuncuların kendi rotasyonlarını "basitleştirilmiş" bir şekilde görmeleri açısından kritiktir.

## **Raidbots: Bulut Tabanlı SaaS Altyapısı ve Ölçeklenebilirlik**

Raidbots, SimulationCraft motorunu temel alan ancak onu modern bir web hizmeti (SaaS) olarak sunan bir platformdur.14 SimC'nin yerel bilgisayarlarda çalıştırılmasından kaynaklanan yüksek işlemci ihtiyacı ve karmaşık yapılandırma sorunlarını bulut bilişim ile çözer.14

### **Flightmaster ve İş Yükü Dağıtımı**

Raidbots mimarisinin kalbinde "Flightmaster" adlı bir orkestrasyon servisi bulunur.16 Simülasyonlar, özellikle binlerce eşya kombinasyonunun test edildiği "Top Gear" modunda, devasa hesaplama gücü gerektirir.9 Flightmaster, bu büyük işleri küçük parçalara (chunks) böler ve bunları Google Cloud Platform (GCP) üzerindeki geçici (preemptible/spot) sunucu filolarına dağıtır.15

Bu parçalı yapı, simülasyonun bir kısmında hata oluşsa bile tüm sürecin baştan başlamasını engeller; sadece hatalı parça tekrar çalıştırılır.16 Bu teknoloji, SimoWoW'un mobil kullanıcılarına sunacağı "Hızlı Simülasyon" özelliklerinde örnek alınması gereken bir ölçekleme modelidir.

### **Warchief: Filo ve Kuyruk Yönetimi**

Raidbots'un arka planında çalışan "Warchief" sunucusu, tüm sistemin operasyonel sağlığından sorumludur.15 Warchief'in görevleri arasında iş kuyruğunu izlemek, ihtiyaca göre yeni işçi (worker) sunucuları başlatmak veya boşta kalanları kapatmak, kullanıcı aboneliklerini senkronize etmek ve metrikleri raporlamak yer alır.15

| Servis Adı | Teknoloji | Görevi |
| :---- | :---- | :---- |
| Frontend | React / Redux.15 | Kullanıcı arayüzü ve state yönetimi. |
| API Server | Node.js.15 | İşlerin kuyruğa alınması ve API yönetimi. |
| Worker | SimC (C++).15 | Fiili simülasyon hesaplaması. |
| Flightmaster | Node.js (900 LoC).16 | Büyük işlerin parçalanması ve birleştirilmesi. |
| Data Store | Google Datastore / Redis.15 | Kullanıcı verileri ve geçici kuyruk depolama. |

Raidbots, kullanıcıdan gelen verileri (SimC eklenti dizisi) işleyerek SimulationCraft'a girdi sağlar.9 Yerel SimC'den farklı olarak, Raidbots bazı verileri (örneğin Legion dönemindeki Crucible özellikleri) önbelleğe alabilir ve bu sayede daha doğru sonuçlar üretebilir.18

## **Wowsims: WebAssembly ve İstemci Tarafı Devrimi**

Wowsims, WoW Classic topluluğu için geliştirilmiş, modern bir teknoloji yığını kullanan açık kaynaklı bir platformdur.19 SimC ve Raidbots'tan farklı olarak Wowsims, simülasyon motorunu doğrudan kullanıcının tarayıcısında çalıştırabilmek için Go dilini ve WebAssembly (WASM) teknolojisini kullanır.20

### **WASM ve Tarayıcı Tabanlı Hesaplama**

Wowsims'in simülasyon motoru Go dilinde yazılmıştır.20 Bu motor, .wasm formatına derlenerek tarayıcı üzerinde yerel hıza yakın bir performansla çalıştırılır.21 Bu yaklaşım, sunucu maliyetlerini minimize ederken, kullanıcının kendi donanım gücünü simülasyon için kullanmasını sağlar.21 SimoWoW'un mobil stratejisinde, özellikle modern akıllı telefonların güçlü tarayıcı motorları düşünüldüğünde, WASM tabanlı bir çözüm sunucu maliyetlerini düşürmek için bir alternatif olabilir.

### **Google Protocol Buffers (Protobuf) Entegrasyonu**

Wowsims, kullanıcı arayüzü (TypeScript) ve simülasyon motoru (Go) arasındaki veri iletişimini sağlamak için Protobuf kullanır.21 .proto dosyalarında tanımlanan veri yapıları, her iki dil için de otomatik kod üretimi sağlar; bu da tip güvenliğini garanti eder ve veri aktarımı sırasında oluşabilecek hataları en aza indirir.21

* **sim/wasm/main.go:** Tarayıcı tarafındaki JavaScript ile Go motoru arasındaki köprüdür.21  
* **sim/core/sim.go:** Ana olay döngüsünü ve simülasyonun çalışma mantığını barındırır.21  
* **sim/core/agent.go:** Oyuncuyu (karakteri) kontrol eden "Agent" arayüzünü tanımlar.21

## **RNG Modelleme ve Hesaplama Metotları**

Simülasyonların kalbi, rastgele sayı üretimi (RNG) ve bu sayıların oyun mekaniklerine doğru şekilde uygulanmasıdır.23 WoW'da kritik vuruşlar, eşya tetiklenmeleri ve hasar aralıkları tamamen bu matematiksel modellere dayanır.

### **Monte Carlo Simülasyonu ve İstatistiksel Güven**

WoW simülasyonları, binlerce dövüşün ortalamasını alarak sonuca ulaşır. Bu süreçte her bir dövüşe "iterasyon" denir.5 İterasyon sayısı arttıkça, elde edilen sonucun standart hatası azalır.3

Hesaplama şu temel formüle dayanır:

![][image1]  
Burada ![][image2] iterasyon sayısını, ![][image3] ise her bir iterasyondaki hasar çıktısını temsil eder.3 Çoğu simülatör, varsayılan olarak 10.000 iterasyon kullanarak yaklaşık %0.1 ile %0.3 arasında bir hata payı ile sonuç üretir.5

### **Lehmer Rastgele Sayı Üreticisi (PRNG)**

Bilgisayar ortamında gerçek anlamda rastgele sayı üretmek zordur; bu nedenle "psödo-rastgele" (PRNG) algoritmalar kullanılır.23 SimulationCraft ve türevi sistemler genellikle Lehmer algoritmasını veya türevlerini (Linear Congruential Generator \- LCG) kullanır.23

![][image4]

* **Modül (![][image5]):** Genellikle ![][image6] gibi büyük bir asal sayıdır.23  
* **Çarpan (![][image7]):** Dikkatle seçilmiş bir sabittir (örneğin 16807).23  
* **Tohum (seed):** Aynı tohum değeri, her zaman aynı rastgele diziyi üretir; bu durum dövüşlerin tekrarlanabilirliği ve hata ayıklama süreçleri için kritiktir.23

RNG'nin kalitesi, dövüş sonuçlarının yapay desenler oluşturmamasını sağlar. Eğer PRNG algoritması zayıfsa, belirli yeteneklerin "şanssız" bir şekilde üst üste gelmemesi gereken durumlar oluşabilir ve bu da simülasyonun doğruluğunu bozar.23

## **Fonksiyonel Analiz ve Kullanıcı Akışları**

Bir simülasyon platformunun başarısı, sadece hesaplama gücüne değil, aynı zamanda bu veriyi oyuncuya nasıl sunduğuna ve veri giriş sürecinin basitliğine bağlıdır.9

### **Veri Girişi ve Entegrasyon Süreci**

WoW simülatörleri, karakter verilerini oyun içinden çekmek için "/simc" komutunu kullanan özel eklentiler (add-on) kullanır.5 Kullanıcı akışı şu adımlardan oluşur:

1. **Export:** Oyuncu oyun içinde /simc yazar ve oluşan metin dizisini kopyalar.5  
2. **Import:** Kopyalanan dizi, web arayüzüne (Raidbots/Wowsims) yapıştırılır.9  
3. **Configuration:** Dövüş tipi (Patchwerk, Dungeon Slice), süresi ve iterasyon sayısı seçilir.9  
4. **Simulation:** "Simulate" butonuna basılarak iş kuyruğa gönderilir.5  
5. **Report:** Birkaç saniye içinde HTML tabanlı, grafiklerle desteklenmiş detaylı bir rapor sunulur.5

### **Dövüş Modelleri (Fight Styles)**

Simülasyonlar, farklı oyun senaryolarını temsil etmek için çeşitli dövüş modelleri sunar.12

* **Patchwerk:** Tek hedefli, hareket içermeyen, ideal dövüş senaryosudur. İstatistik ağırlıklarını bulmak için en uygun modeldir.2  
* **Dungeon Slice:** Mythic+ zindanlarını simüle etmek için geliştirilmiştir; tek hedef ve AoE (alan hasarı) arasında geçişler yapar.12  
* **Hectic Add Cleave:** Hareket ve sık sık ortaya çıkan yardımcı düşmanların (adds) olduğu karmaşık senaryoları modeller.13

| Mod Türü | Kullanım Amacı | Doğruluk Odağı |
| :---- | :---- | :---- |
| Quick Sim | Mevcut karakterin potansiyel hasarını görmek.12 | Hızlı referans. |
| Top Gear | Çantadaki eşyaların en iyi kombinasyonunu bulmak.9 | Maksimum optimizasyon. |
| Droptimizer | Hangi zindan veya raidden en büyük yükseltmenin geleceğini bulmak.9 | Gelecek planlama. |
| Stat Weights | Pawn eklentisi için istatistik değerlerini üretmek.5 | Eşya kıyaslama. |

## **Ask Mr. Robot (AMR) ve Makine Öğrenmesi Yaklaşımı**

AMR, geleneksel olay bazlı simülasyonların yanı sıra, veri analitiği ve makine öğrenmesi (ML) yöntemlerini kullanan alternatif bir motora sahiptir.30

### **Regresyon Analizi ve Karar Ağaçları**

SimC, stat ağırlıklarını belirlemek için sadece iki veri noktasına (stat ekleyip/çıkararak oluşan fark) bakarken, AMR binlerce veri noktası oluşturur.31 Bu veri noktaları üzerinde "çok boyutlu regresyon analizi" ve "karar ağaçları" kullanarak, statlar arası etkileşimleri çok daha geniş bir çerçevede değerlendirir.31

AMR'nin felsefesi, "roboti/kusursuz" bir simülasyon yerine, yetenekli bir insanın yapabileceği hamleleri temel alan daha gerçekçi bir model oluşturmaktır.34 Bu durum, oyuncuların gerçek oyun performansına daha yakın sonuçlar elde etmesini sağlar.34

## **Veri Madenciliği: DBC ve CASC Dosyalarının İşlenmesi**

Simülasyon motorlarının güncel kalabilmesi için WoW oyun dosyalarından büyü, eşya ve özellik verilerini otomatik olarak çekebilmesi gerekir.11

1. **CASC Sistemi:** WoW, verilerini Content Addressable Storage Container formatında saklar.35  
2. **DBC/DB2 Dosyaları:** Oyunun veritabanı dosyalarıdır; büyülerin katsayıları, eşya id'leri ve stat dönüşüm oranlarını içerir.11  
3. **Extraction Pipeline:** SimC, Python scriptleri (casc\_extract.py, dbc\_extract.py) kullanarak bu dosyaları ayrıştırır ve motorun anlayabileceği JSON formatına dönüştürür.35

Bu veri çekme süreci, özellikle "Hotfix" denilen anlık güncellemelerin yakalanması için DBCache.bin dosyalarının taranmasını da kapsar.11 SimoWoW projesi, kendi veritabanını güncel tutmak için bu madencilik araçlarını entegre etmek veya bu araçların çıktılarını (JSON) düzenli olarak tüketmek zorundadır.

## **SimoWoW İçin Mimari ve Teknolojik Çıkarımlar**

SimoWoW projesi kapsamında bir mobil lonca yönetimi platformu geliştirilirken, yukarıdaki teknik analizler ışığında şu stratejik yaklaşımlar benimsenmelidir:

### **Mobil Mimari ve Hesaplama Yükü Dağıtımı**

Mobil cihazların işlemci ve pil kapasiteleri, SimulationCraft gibi ağır hesaplama gerektiren C++ motorlarını yerel olarak çalıştırmak için uygun değildir.38 Bu nedenle, Raidbots'un uyguladığı "iş yükü parçalama" ve bulut tabanlı hesaplama modeli temel alınmalıdır.15

* **Arka Uç (Backend):** AWS Lambda veya Google Cloud Functions gibi "sunucusuz" (serverless) yapılar, her bir simülasyon isteği için tetiklenebilir. Bu, lonca üyelerinin aynı anda simülasyon başlattığı yoğun zamanlarda sistemin ölçeklenmesini sağlar.39  
* **Hekili/MaxDPS Entegrasyonu:** Mobil uygulama üzerinden oyunculara rotasyon tavsiyeleri sunulurken, Hekili gibi oyun içi rotasyon asistanlarının mantığı (APL bazlı) mobil arayüze uyarlanabilir.30

### **Lonca Yönetimi ve Kolektif Veri Analizi**

SimoWoW, sadece bireysel simülasyonlar değil, "Raid Sim" özelliklerini de barındırmalıdır.20

* **Lonca İçi Stat Karşılaştırması:** Lonca liderleri, tüm üyelerin stat ağırlıklarını ve simülasyon çıktılarını tek bir tabloda görerek, loot (eşya) dağıtımını "en yüksek lonca içi DPS artışı" (Upgrade Finder mantığı) üzerinden yapabilir.9  
* **Mobil Bildirim Sistemi:** Bir lonca üyesi önemli bir eşya düşürdüğünde veya simülasyon sonucunu güncellediğinde, lonca yöneticisine bildirim gönderen bir "Warchief" benzeri izleme servisi kurgulanabilir.15

### **Kullanıcı Deneyimi ve Mobil Akış**

Mobil ortamda uzun metin dizilerini kopyalayıp yapıştırmak zordur.43 SimoWoW, Wowsims'in "Exporter" mantığını geliştirerek, eklenti verilerini bir API üzerinden doğrudan mobil uygulamaya aktaracak bir "Push" mekanizması kurmalıdır.19

| Proje Katmanı | Teknoloji Önerisi | Referans Alınan Model |
| :---- | :---- | :---- |
| Simülasyon Motoru | Go \+ WASM (Tarayıcı içi).21 | Wowsims |
| Hesaplama Sunucuları | Python/Node.js \+ GCP Instances.15 | Raidbots |
| Mobil Veri İletişimi | Protobuf (Tip güvenliği için).21 | Wowsims |
| Yönetim Paneli | Spring Boot \+ WeChat Applet Yapısı.43 | Lonca Yönetim Sistemleri |
| Veritabanı | MySQL / Redis (Kuyruk yönetimi için).17 | Raidbots / SimoWoW |

## **Sonuç: Stratejik Yol Haritası**

SimoWoW mobil lonca yönetimi projesi, WoW ekosistemindeki devasa hesaplama gücünü ve teorik birikimi, lonca yöneticileri ve oyuncular için erişilebilir bir mobil platforma dönüştürme potansiyeline sahiptir. SimulationCraft'ın olay güdümlü motoru, Raidbots'un ölçeklenebilir bulut mimarisi ve Wowsims'in modern WebAssembly yaklaşımı, projenin teknolojik omurgasını oluşturmalıdır.

RNG modellemesinde istatistiksel güvenin korunması, kullanıcı akışında mobil sınırlamaların (veri girişi gibi) aşılması ve lonca bazlı metriklerin (kolektif hasar artışı gibi) ön plana çıkarılması, projenin fark yaratacağı alanlardır. Sonuç olarak SimoWoW, sadece bir raporlama aracı değil, WoW loncaları için veri güdümlü bir karar destek sistemi olarak konumlandırılmalıdır.

#### **Alıntılanan çalışmalar**

1. simulationcraft/simc: Simulationcraft engine/GUI \- GitHub, erişim tarihi Şubat 13, 2026, [https://github.com/simulationcraft/simc](https://github.com/simulationcraft/simc)  
2. SimulationCraft \- Welcome, erişim tarihi Şubat 13, 2026, [https://www.simulationcraft.org/](https://www.simulationcraft.org/)  
3. Methods of Monte Carlo Simulation \- Uni Ulm, erişim tarihi Şubat 13, 2026, [https://www.uni-ulm.de/fileadmin/website\_uni\_ulm/mawi.inst.110/lehre/ws13/Methods\_of\_Monte\_Carlo\_Simulation/MC\_all.pdf](https://www.uni-ulm.de/fileadmin/website_uni_ulm/mawi.inst.110/lehre/ws13/Methods_of_Monte_Carlo_Simulation/MC_all.pdf)  
4. Detailed Tutorial on In-Depth Simulationcraft Usage : r/CompetitiveWoW \- Reddit, erişim tarihi Şubat 13, 2026, [https://www.reddit.com/r/CompetitiveWoW/comments/2ro1nf/detailed\_tutorial\_on\_indepth\_simulationcraft\_usage/](https://www.reddit.com/r/CompetitiveWoW/comments/2ro1nf/detailed_tutorial_on_indepth_simulationcraft_usage/)  
5. StartersGuide.wiki \- simulationcraft \- Google Code, erişim tarihi Şubat 13, 2026, [https://code.google.com/archive/p/simulationcraft/wikis/StartersGuide.wiki](https://code.google.com/archive/p/simulationcraft/wikis/StartersGuide.wiki)  
6. How accurate is SimCraft? : r/wow \- Reddit, erişim tarihi Şubat 13, 2026, [https://www.reddit.com/r/wow/comments/5kscy3/how\_accurate\_is\_simcraft/](https://www.reddit.com/r/wow/comments/5kscy3/how_accurate_is_simcraft/)  
7. DevelopersDocumentation · simulationcraft/simc Wiki · GitHub, erişim tarihi Şubat 13, 2026, [https://github.com/simulationcraft/simc/wiki/DevelopersDocumentation](https://github.com/simulationcraft/simc/wiki/DevelopersDocumentation)  
8. Event-driven simulation class \- c++ \- Stack Overflow, erişim tarihi Şubat 13, 2026, [https://stackoverflow.com/questions/369948/event-driven-simulation-class](https://stackoverflow.com/questions/369948/event-driven-simulation-class)  
9. SimulationCraft and Raidbots Guide 11.0.2 \- World of Warcraft \- Maxroll, erişim tarihi Şubat 13, 2026, [https://maxroll.gg/wow/resources/simulationcraft-and-raidbots-guide](https://maxroll.gg/wow/resources/simulationcraft-and-raidbots-guide)  
10. ActionLists · simulationcraft/simc Wiki \- GitHub, erişim tarihi Şubat 13, 2026, [https://github.com/simulationcraft/simc/wiki/ActionLists](https://github.com/simulationcraft/simc/wiki/ActionLists)  
11. GameClientData · simulationcraft/simc Wiki \- GitHub, erişim tarihi Şubat 13, 2026, [https://github.com/simulationcraft/simc/wiki/GameClientData](https://github.com/simulationcraft/simc/wiki/GameClientData)  
12. Simulationcraft-101 \- Peak of Serenity, erişim tarihi Şubat 13, 2026, [https://www.peakofserenity.com/tww/windwalker/pve-guide/sim101/](https://www.peakofserenity.com/tww/windwalker/pve-guide/sim101/)  
13. WoW SimulationCraft Full Guide \- Overgear, erişim tarihi Şubat 13, 2026, [https://overgear.com/guides/wow/simulationcraft-guide/](https://overgear.com/guides/wow/simulationcraft-guide/)  
14. How To Sim With Raidbots Guide | Forget The Boring Simcraft \- Epiccarry, erişim tarihi Şubat 13, 2026, [https://epiccarry.com/blogs/raidbots-sim-guide/](https://epiccarry.com/blogs/raidbots-sim-guide/)  
15. Raidbots Technical Architecture. There's been an interest from several… | by Seriallos \- Medium, erişim tarihi Şubat 13, 2026, [https://medium.com/raidbots/raidbots-technical-architecture-303349d82784](https://medium.com/raidbots/raidbots-technical-architecture-303349d82784)  
16. Raidbots Tech: Flightmaster \- Medium, erişim tarihi Şubat 13, 2026, [https://medium.com/raidbots/raidbots-tech-flightmaster-440692101355](https://medium.com/raidbots/raidbots-tech-flightmaster-440692101355)  
17. Raidbots Tech: The Main Queue \- Medium, erişim tarihi Şubat 13, 2026, [https://medium.com/raidbots/raidbots-tech-the-main-queue-bd56ad8393fa](https://medium.com/raidbots/raidbots-tech-the-main-queue-bd56ad8393fa)  
18. Why do I get different DPS from Raidbots / local SimC ... \- Medium, erişim tarihi Şubat 13, 2026, [https://medium.com/raidbots/why-do-i-get-different-dps-from-raidbots-local-simc-wowprogress-fe33781cb8a5](https://medium.com/raidbots/why-do-i-get-different-dps-from-raidbots-local-simc-wowprogress-fe33781cb8a5)  
19. WoWSims \- Classic WoW Simulations, erişim tarihi Şubat 13, 2026, [https://wowsims.github.io/](https://wowsims.github.io/)  
20. wowsims/mop: World of Warcraft Mop Classic simulations. \- GitHub, erişim tarihi Şubat 13, 2026, [https://github.com/wowsims/mop](https://github.com/wowsims/mop)  
21. cata/README.md at master · wowsims/cata · GitHub, erişim tarihi Şubat 13, 2026, [https://github.com/wowsims/cata/blob/master/README.md](https://github.com/wowsims/cata/blob/master/README.md)  
22. wowsims \- GitHub, erişim tarihi Şubat 13, 2026, [https://github.com/wowsims](https://github.com/wowsims)  
23. Random numbers, Monte Carlo methods, erişim tarihi Şubat 13, 2026, [https://www2.mpia-hd.mpg.de/\~klahr/Lecture\_09\_randomnumbers.pdf](https://www2.mpia-hd.mpg.de/~klahr/Lecture_09_randomnumbers.pdf)  
24. Generating Random Numbers \- Monte Carlo Methods in Practice, erişim tarihi Şubat 13, 2026, [https://www.scratchapixel.com/lessons/mathematics-physics-for-computer-graphics/monte-carlo-methods-in-practice/generating-random-numbers.html](https://www.scratchapixel.com/lessons/mathematics-physics-for-computer-graphics/monte-carlo-methods-in-practice/generating-random-numbers.html)  
25. Random Number Generation and Monte Carlo Simulation \- Professor Hui Chen, erişim tarihi Şubat 13, 2026, [https://huichen-cs.github.io/course/CSCI570/2015Spring/lecture04\_mc.pdf](https://huichen-cs.github.io/course/CSCI570/2015Spring/lecture04_mc.pdf)  
26. How to Use Pawn and Simulationcraft : r/wow \- Reddit, erişim tarihi Şubat 13, 2026, [https://www.reddit.com/r/wow/comments/5qjull/how\_to\_use\_pawn\_and\_simulationcraft/](https://www.reddit.com/r/wow/comments/5qjull/how_to_use_pawn_and_simulationcraft/)  
27. Addon Help \- Ask Mr. Robot, erişim tarihi Şubat 13, 2026, [https://blog.askmrrobot.com/addon/](https://blog.askmrrobot.com/addon/)  
28. How Accurate are Raidbots Sims? : r/wow \- Reddit, erişim tarihi Şubat 13, 2026, [https://www.reddit.com/r/wow/comments/1bn2etr/how\_accurate\_are\_raidbots\_sims/](https://www.reddit.com/r/wow/comments/1bn2etr/how_accurate_are_raidbots_sims/)  
29. Simming Your Windwalker | Peak of Serenity, erişim tarihi Şubat 13, 2026, [https://www.peakofserenity.com/2020/05/07/simming-your-windwalker/](https://www.peakofserenity.com/2020/05/07/simming-your-windwalker/)  
30. Is Ask Mr Robot legit and reliable and easy to use? \- Blizzard Forums, erişim tarihi Şubat 13, 2026, [https://us.forums.blizzard.com/en/wow/t/is-ask-mr-robot-legit-and-reliable-and-easy-to-use/2080662](https://us.forums.blizzard.com/en/wow/t/is-ask-mr-robot-legit-and-reliable-and-easy-to-use/2080662)  
31. What do you think about the new AMR feature, Machine Learning? : r/wow \- Reddit, erişim tarihi Şubat 13, 2026, [https://www.reddit.com/r/wow/comments/5jlcck/what\_do\_you\_think\_about\_the\_new\_amr\_feature/](https://www.reddit.com/r/wow/comments/5jlcck/what_do_you_think_about_the_new_amr_feature/)  
32. Need Help About Stat Weights for Ask Mr Robot (MM) \- Hunter \- Icy Veins, erişim tarihi Şubat 13, 2026, [https://www.icy-veins.com/forums/topic/31417-need-help-about-stat-weights-for-ask-mr-robot-mm/](https://www.icy-veins.com/forums/topic/31417-need-help-about-stat-weights-for-ask-mr-robot-mm/)  
33. Question about Sim: is better Mr Robot or Simulationcraft? : r/wow \- Reddit, erişim tarihi Şubat 13, 2026, [https://www.reddit.com/r/wow/comments/5qc2ux/question\_about\_sim\_is\_better\_mr\_robot\_or/](https://www.reddit.com/r/wow/comments/5qc2ux/question_about_sim_is_better_mr_robot_or/)  
34. AMR versus Raidbots/SimC differences? \- Simple Q & A \- Ask Mr. Robot, erişim tarihi Şubat 13, 2026, [https://forums.askmrrobot.com/t/amr-versus-raidbots-simc-differences/4459](https://forums.askmrrobot.com/t/amr-versus-raidbots-simc-differences/4459)  
35. Using CASC Extract and DBC Extract · simulationcraft/simc Wiki \- GitHub, erişim tarihi Şubat 13, 2026, [https://github.com/simulationcraft/simc/wiki/Using-CASC-Extract-and-DBC-Extract](https://github.com/simulationcraft/simc/wiki/Using-CASC-Extract-and-DBC-Extract)  
36. Data mining, how it works? \- General Discussion \- World of Warcraft Forums, erişim tarihi Şubat 13, 2026, [https://us.forums.blizzard.com/en/wow/t/data-mining-how-it-works/329251](https://us.forums.blizzard.com/en/wow/t/data-mining-how-it-works/329251)  
37. DBC \- wowdev, erişim tarihi Şubat 13, 2026, [https://wowdev.wiki/DBC](https://wowdev.wiki/DBC)  
38. Architecture and Infrastructure Aspects of Mobile Game Testing \- SmartBear, erişim tarihi Şubat 13, 2026, [https://smartbear.com/blog/architecture-and-infrastructure-of-mobile-testing/](https://smartbear.com/blog/architecture-and-infrastructure-of-mobile-testing/)  
39. AWS re:Invent 2025: My Serverless & Agentic AI Takeaways \- Ran The Builder, erişim tarihi Şubat 13, 2026, [https://www.ranthebuilder.cloud/post/aws-re-invent-2025-my-serverless-agentic-ai-takeaways](https://www.ranthebuilder.cloud/post/aws-re-invent-2025-my-serverless-agentic-ai-takeaways)  
40. AWS Lambda: Getting Started with Serverless, erişim tarihi Şubat 13, 2026, [https://serverless-architecture.io/blog/aws-lambda-getting-starting-with-serverless/](https://serverless-architecture.io/blog/aws-lambda-getting-starting-with-serverless/)  
41. Creating event-driven architectures with Lambda \- AWS Documentation, erişim tarihi Şubat 13, 2026, [https://docs.aws.amazon.com/lambda/latest/dg/concepts-event-driven-architectures.html](https://docs.aws.amazon.com/lambda/latest/dg/concepts-event-driven-architectures.html)  
42. About Hekili : r/wow \- Reddit, erişim tarihi Şubat 13, 2026, [https://www.reddit.com/r/wow/comments/1alqtvf/about\_hekili/](https://www.reddit.com/r/wow/comments/1alqtvf/about_hekili/)  
43. (PDF) Design and Implementation of Game Guild System based on Spring Boot and WeChat Applet \- ResearchGate, erişim tarihi Şubat 13, 2026, [https://www.researchgate.net/publication/369878097\_Design\_and\_Implementation\_of\_Game\_Guild\_System\_based\_on\_Spring\_Boot\_and\_WeChat\_Applet](https://www.researchgate.net/publication/369878097_Design_and_Implementation_of_Game_Guild_System_based_on_Spring_Boot_and_WeChat_Applet)

[image1]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAmwAAAA4CAYAAABAFaTtAAAFOUlEQVR4Xu3dX6hlVR0H8BUkZBo5NBSDyEwpDFHpQCQJDkTUQw0I4r9m6lGMoBeFHDHRSfEpCLSosIepQMR6UJ+UUXBAkGYIjWAwBBEjCuqphwKFrPVln92su+455565987cc+98PvDlnL3Wvfte9tOP9W+XAgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADvS0zVv1ny0Zn/NiZpfr/gJAAC21Odrbql5anJ9U9MHAMASuLtmV83vJp+5BgBgiXxv8vmtmkM1h5s+AAA2ye01+/rGBV3XfD9Ts7u5BgBgg75W86Waf5VhLRoAAEtKwQYAsOQUbAAAS07BBgCwhg/0DRfYIgXbJ2reqvlvzV9q/jwlf5/0t3k/vwwAsJ2lWPtNzSs1e7u+C2WRgi0uKUMRljcbLPq/nq75bN8IALCd5FiMFEJfqHmg67tQ/l2Gv7+IFGAp2p7oO2a4tOYnZX2jiB/qGxaU55lXZQEAF5k/lLPTfHl/5ma4ppy973/K5t33fBufw/V9xwyXl/nF16maH9Z8pml7ufke6c8zyt/Na7Byv39MrpPex8ri/x8AsIOkMDgf78qcVnAss0yHZlo0//cHu75z9amae8pwz3EULlOos6ZRsyYuo3bxXNsxxat9AwCws2WU6G9lKDBm+XiZPpI0r6gZ77vdfLUMBVte/L4RXynDAb6to2X6c4y8s/SGMhR4B7q+3qNl/rMHAHaYjKylAJjlt5PPrJ/KLspxFChrqT45+T7NWvddZi+VoWjL53rcVvN2zfGaxydte2re+f9PrJaCOaNsd/QdU2QjxaJr8wCAHeBkmT+6lpGy1lU13558zpLfOVlW3vf+mj+VYf3Vh8tQyGQH6bIa15Ud7DsWlOK2lSIrR4TM8mAZCrYX+o7q2rJyc0OKv2821wDADpdpy8v6xkb6fl/zy7J6R+TV3fUohdq0+75Rhp2V8ZFydrRuM4yL9BfJIn5Whp99rO9YUHaotuYVbHmu95VhWvTdri++012nYMv6OADgIrFWAdOO5Bwpw0jQ3pqHyjBNOk2mQvv7froMh9SmaIt+fVfr1jnZzCJvnntrXuwbz0EO422liP1r1xZZK/fk5HummDMy1041/6DmF8115F7znh8AsEO8VvNeGQqrFAyZptwMue84kjUWIjGOCOXIj6zxyhTpsjpU1l74P08K0379XkbRjjfXOZ5jfE4nJm2vN22HJ21fLKsLxxTR/VQ1AMCGjQVbCpc/1tzZ9C2bHO2xEdkQkF2ivW/U7Oob13BsklbOawMA2DQp0O4qw4aD0c9rrmyuN1vWz2UBf3v0xfM1X26up8nO14xm9Wv1Zsm05P7m+nM1z9Y807T1xl23i8pO1Uea6/xvma4FANjWssD/u2XlyNSPm+/TZD1eXks1a11eb19ZPe25iNw/05zrkSJ3PX8TAGCpZMpxdxkW7meDQ9aTxVrHYGTUatH3dGb36z/LcNAtAADnqC3MckRGzjVLATdv7Vh2arbHfiwaAADW4UfN9xRrKdpubNp6GS37fhmmQ88l6z2fDQDgovfT5nuOzjhdc6ppAwBgC+VQ3a93bVnLNr7PEwCALZTjMsa1Ze2hsjkGY60NBwAAbBN5Z2fOjJvlSM2ZmqN9BwAA5182H+SdnWsd7fGromADANgSN5fhbQg5W+3hmpNdxl2hCjYAgC10bPJ5Rc2eLtlxGgo2AIAtkoIs7+w82Hc0DpThPaV5L2qKOgAALrCsYwMAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADYAf4HV5vdrA2QrZwAAAAASUVORK5CYII=>

[image2]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABIAAAAYCAYAAAD3Va0xAAABGUlEQVR4Xu2TsWoCQRCGR7BRQRECYmkpCBZiIdgkWATsbJPeRhDyBNfaaKGVVlY2Yi15Ap/AvICdiI1NLEz+310ve3vkvKu9Dz5YdpbZmbk9kZioPMM9/NGuYcqIZ+GnEacrmDHOuCTgFJ7hN2x4w1c6cCneS3zk4Rz2Rd04EZXc5AO+WXs+qnAEi/AL7mDJiCfhTJ8LhDd19doRVVXPjYo8iaqYlQcyhDW9rsAj3MCc3mvCsV7/y20+vJWwjQW8wFe9x2pDz8ccLhMwERPyK0Wezw22xNbY4ouEmA+rYO91OwDeRQ19CwdWzIc9H5OCqKfAZHfnw7L53NN2QOPAAyxb+y4teJK/f4e/RdtzQsGnwH8vcD4xD8kvcTMzNIxbkGYAAAAASUVORK5CYII=>

[image3]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAYCAYAAAC8/X7cAAAC50lEQVR4Xu2WS8hNURTH//LIM3knr5SUCCVKGBCKIjFRzAxQ9HkkZXQLZSJ5PyJRUpgoz4hPisKQiCSFGcoMif//rrNzzrr7nO+c6yrq+9W/e+9eZ9+99l5rr3WATv5/ulP9/WAL6UoNoLp4Qxn6UAup8Yj/gRw/Ts3whhaidbdSm5PvpRlD3af2UO+pBVkzulGHqXVuPDCX+kL9TOkN7DB6U1ec7QE1qD6zEUX5LLXCG4qowTawG7bAyozVNtSOjtNH8zT/FiyigSEwp9fAHOyISdRDapQ3xFDOPaZOUoOpKbBcDPSiblAbUmN5DKOeU59hTgg5fBDVTlQRPw872A6ZQH2ktnhDwjTqFey5MtRgUdBncF6br5TTZBXsYHXAUXpSw2EP/oCFX7/7ph8ia2Hp1c+N56GTVwReUPuobajuvFAmvKWme0NgFnWCekJ9pc4lv/2EM4nKovBfgkXhNMrlfAwdpjaw3Bs8ci4vVIpGO+xyV6ENtgHlsTbUDGHt7W48g9JC6aETiy1U6k8c86l71AdkL3MMVbX1yaen1OGNpN5RO7whoeoG1OQuUgORvcx5KM8PofHeibC2qmMus6nv1BJvSKiyATXDy8mnCJdZZVXltSql1laFUQfVScQIF7LwFGBO36SmpsZCLY81RlWlZdQ1ZOekCf0pr7zXOUA9gzWwPPTMVVjZ9ciRybCFFjubUInWBi4gW43UUxbBUreWGk+j9H4Nu1NR1OpvI/8CB5ZST9G4yV2w/hHebz7Bml5gf8omfaNOUT2oodRoWASUxjE0rsMd4Q2BcIGVRkWMhTWlvIWaZSbsnSlWgUQNkTKskG+CTVQOagNFZU5ozk5YtWimo+ah1NQFVep5H/Smeoea48broXsJy9kj1FEUp09A0bpLTfSGP2Av7D1pIxoPZjV1DJEurgfVOB7BJueFL4ZqvC5jlTlFyBc1Uu/8OOo6fpfjljIP9prwt9CG1HkV8U7+OX4BmkSLAPPduV0AAAAASUVORK5CYII=>

[image4]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAmwAAAAiCAYAAADiWIUQAAAD3ElEQVR4Xu3dS4gUVxTG8SMxYNQQk4gPDIiCCUJCFgFFEMxCRBcxCwUFQdz4Ap8JIZAsxY0mqAFBfGJAVFAU1KAi2jtFVwZfKMIogisRRN0Ejefj3pq6c5ke6bYYm67/Dz769qkau6Zmc7j3VmsGAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAEDX+SQvdICReQEAAKCOhnp25sUKvPIczIttOGmd2UwCAAAMmrOeNXmxApodq6Jhm+G5nRcBAADq5J5nal6sQFUN26eea3kRAAB0vw2epZ5bnr8tNC1f9Tnj/fjX87PnsmderE30rPD85dnjOef5Mx6rQtpUbfQ89Wz2LLbwmQssfP4vFu6bDLHQRH3v2eoZF+taurzqWWLhOps1bPs9WzzLLJyrz5nlWedZ65nfe2bwq+fjrAYAALrcl54RngsW9nD96PkgOf5DMm6maKiq0rByr9Zez+g4VhMl+ryZFpqnL2JNpifjVmkWTM1Q6jvPyjge7zmUHGt4hnnOWHl98p+Fa3uR1JrNsOl+69/9zTMl1mZb2aRNsNAwpvT3mJzVAABADagBeJwXo7xhyJsiNRsPstq7ep2MNXulWayUrknNTG51XmhBs4ataFjVWKVNV8Mz1nPf+j7B+b/np/haaNawSdH06VV0DUVDpuZtbhwXdD3fZjUAANDF1AjtsrAM1xNr2zzD41izPmrIUquy99LIC4lvPAsHyEflqb2eJeOXnkUWliOPWNhj9iQeW+6ZE8daVtwex+3QbJdm81Jva9j0M4et7yyfllG/tvIaZaCGTU2ZniIVNaE9caxmUA8YfGjhdyto2VTHAABATagZOGVhr5Rmso7Hmmgvlpb6LlpYMv3ds9vCnjK9KoVGMq7CHxYaHF3bQwv7xdRcXvcc8Gzy7LPyAYHPLDRNV+L7dt2wcnlTjasaKc2Uac/a8zhWw3Q3jtVsie7Jac9NK++fGlHNvuk6da90/qN4LHXUcyKONTNXnKPfR3+TY3EsahD1HgAA1MyY+Kp9a8WyXEoNUqrVGbZ2fW6hSdM1FUuimqkqxjqeUvN0Pqu16o6F/WftGGVls1bQtWtmTtes4/3R71Tcd/18+j1rep/uJ5xkfK0HAADIaLZJy4KpvGHTAwDaYK9ZqP4avsGi2bj8icpWaSbrUl7sIP94puVFAABQT2q8tHdtR36gQ+nrSPQ/FGjJsArr80IH0F69/OELAABQY2oMtI8sf0KxU+m72PLlSAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACosTdaF4PhNrRyqgAAAABJRU5ErkJggg==>

[image5]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABEAAAAYCAYAAAAcYhYyAAABFUlEQVR4Xu3SMUtCURjG8VcqMMhCbAlpDYSghgiEFrcCERHXoKkImopwMMLP4Ga0tLcZEeEg+Akc2q0xEaFBCBf/773nxIs6ODbcB37ofe49h8M5RyRKlMWzjhNsu+cVHKBouhh2UHa/+vyXNTRwjy+coolzVNFHHg+4wxl6uBGTY1xgDz9oYcO928InvnHoOs0T2hIuIMilhBOUMEbOvyAZDFAxnQ5s4xnLpg9Sxwc2TVfAL45M5ye+Ml2QBDoyO7tO3EPadDp4iF3TBfGzX5tu3rJX8ebo/1sxe+X3Y96y7cR6tHpaehB69I9iNreGLlK+kPDejJA1nQ54xTtesG/eSdx9YLOEpExdKtfr5uuFjPLvMwGD+y4YQ2CdEAAAAABJRU5ErkJggg==>

[image6]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADoAAAAXCAYAAABaiVzAAAAB3ElEQVR4Xu2XvStFYRzHf0IRoYhMShaT5C2hDBLKwF8gC5NCiBhMDFJKkWwGi0FJElksXhYDdhIbpVgkvt9+z3Odc+7tOnfgnFvnU5+653mee3u+53m9IhFxZMI+uACnYIG7WvLgICzylKcdw3ACZsABeAYLYTHchnvwFpab9mnLLDwRHcle+AQrHfV18ErSICg7OAc34DysclfH4IiuwjWY5SgPS9Ba2OkttDTCI9gGa+A+/ILjosEsLfDc1Jc5ykmQQZvgJLwU7Tf3kDhy4a7oRsINh3DdXcA30QBeuuA1rHCUBR2Uy6lHtM8Jg7Jjd/BVdDQtM6JvZ0x0VBmu3tQxFH9wyDzbsqCCWmy/EgbNhivwUNydZGM7DUrgDdw0dQ3wBXaYZxL6oIngJrMDP2G76IiOwEXYLHqcLIm+pBzRY+cAfpjvdUswpByUc55f4A7MMJZ80REL66UgpaC8BBzDLdHbzl/AGcINjy/Nj5w1fvAdlKO3DpdFd+O/gjOCy4Azxo9+l4KvoDbktPwcM9WS5PANIb8G5VTi5WDUfLbw+Oh3PIedpEHtJf0dPsB7h8+wNdYy/NigvAPEwcXOCwPPTK/ei3tY4T+rR3H3nYN0Cksd7SIiIiIi/oVvE/JnPcpXvu0AAAAASUVORK5CYII=>

[image7]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAAZCAYAAAAIcL+IAAAAx0lEQVR4Xu3RMQtBURjG8VeYKIsYZVHKdidllDJQrMpqsbDJB7iTxcw38AXEcEerMimbbEaTgf/r3HM7mSwmnvp1nee87j1ckX++kTjKaCD1thelhB189BHggrEzIwUcMUEs7Hp4oG2HEljgjKItxdzpKuYor3w8qB+0WIn5kkavug6QDjtpiTnLwBYkjxPmThcNNp2uhju6qGKkZUXMo+2vy2CLGzxMUdcN/TuG2GOJDTo4YI0Zkjpoo4fOiXk7Gt3MOusfzBNijSGBwLzOUwAAAABJRU5ErkJggg==>