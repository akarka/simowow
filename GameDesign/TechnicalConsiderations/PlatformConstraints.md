# Platform Constraints (Platform Kısıtlamaları)

Bu doküman, mobil platformun getirdiği teknik ve tasarım kısıtlamalarını ve bu kısıtlamaların oyunun genel tasarımına, mekaniklerine ve kullanıcı deneyimine (UX) nasıl yön verdiğini tanımlar. Projenin kapsam daraltma (scoping down) stratejileri, bu kısıtlamalar göz önünde bulundurularak geliştirilmiştir.

## 1. Teknik Kısıtlamalar

Mobil cihazlar, masaüstü bilgisayarlara kıyasla belirli teknik sınırlamalara sahiptir.

*   **İşlemci Gücü ve Performans:**
    *   Sınırlı işlemci ve grafik işlemci gücü, karmaşık 3D grafikler veya gerçek zamanlı fizik simülasyonları gibi yoğun görsel öğelerden kaçınılmasını gerektirir.
    *   Bu nedenle, `Mobile UI Strategy` dokümanında belirtildiği gibi 2D "Dots" sistemi ve metin tabanlı savaş görselleri tercih edilmiştir. 40 karakterin aynı anda büyü efektleri atması performans sorunlarına yol açacaktır.
*   **Bellek (RAM):**
    *   Sınırlı RAM, oyunun bellek ayak izini küçük tutmayı gerektirir. Bu, büyük açık dünya haritalarından veya çok detaylı assetlerden kaçınılması anlamına gelir.
*   **Depolama Alanı:**
    *   Kullanıcıların mobil cihazlarında sınırlı depolama alanı vardır. Oyunun dosya boyutunu makul tutmak, indirme oranlarını ve kullanıcı tutma oranlarını artırır.
*   **Batarya Ömrü:**
    *   Oyunun batarya tüketimini optimize etmesi, uzun süreli oyun seanslarına olanak tanır ve kullanıcı memnuniyetini artırır. Yoğun grafikler veya sürekli işlemci kullanımı bataryayı hızla tüketir.

## 2. Tasarım ve Kullanıcı Deneyimi (UX) Kısıtlamaları

Mobil platform, kullanıcı etkileşimi ve arayüz tasarımı açısından kendine özgü dinamiklere sahiptir.

*   **Ekran Boyutu:**
    *   Küçük ekran boyutları, "veri yoğunluklu" bir UI tasarımında en büyük zorluğu oluşturur. `Information Hierarchy` dokümanında belirtildiği gibi, bilgiyi gizlemek değil, doğru hiyerarşide ve optimize edilmiş bir şekilde sunmak esastır.
    *   `Mobile UI Strategy` dokümanındaki "Design by Width" ve "Grid" yapısı, farklı ekran boyutlarına uyum sağlamayı hedefler.
*   **Dokunmatik Kontroller:**
    *   Dokunmatik ekranlar, hassas mikro yönetim gerektiren mekanikler için uygun değildir. `Combat Simulation` dokümanında belirtildiği gibi, "interrupts", "dispels" veya "threat management" gibi anlık refleks gerektiren mekanikler, dokunmatik kontrollerle zorlayıcı olabilir.
    *   Bu nedenle "Auto-Battler" dönüşümü ve "Komutan Yetenekleri" gibi daha yüksek seviyeli müdahale mekanikleri benimsenmiştir.
*   **Oturum Süresi:**
    *   Mobil oyunlar genellikle kısa ve kesintili oyun seansları için tasarlanır. Oyuncular, otobüste, sırada beklerken veya kısa molalarda oyun oynayabilir.
    *   Oyunun "core loop"u, 5-10 dakikalık kısa oturumlara uygun olmalıdır. `Dispatch Missions` ve `Weekly Meetings` gibi mekanikler bu prensibe uygun tasarlanmıştır.

## 3. Ağ Bağlantısı ve Veri Tüketimi

Mobil cihazların sürekli ağ bağlantısına ihtiyaç duyması ve veri tüketimi de önemlidir.

*   **Çevrimdışı Oynanış:** Temel yönetim mekaniklerinin bir kısmının çevrimdışı oynanabilir olması (`<input gerekiyor>`), internet bağlantısı olmayan durumlarda bile oyuncunun oyuna erişimini sürdürmesini sağlar.
*   **Veri Tüketimi:** Oyunun minimum veri tüketimiyle çalışması, mobil veri kullanan oyuncular için önemlidir.

## 4. Eksik Alanlar / Geliştirme Notları

*   **Desteklenecek Minimum Cihaz Özellikleri:** Oyunun hangi minimum mobil cihaz özellikleri (işletim sistemi versiyonu, RAM, işlemci) üzerinde çalışacağı. (`<input gerekiyor>`)
*   **Performans Testi Metodolojisi:** Mobil cihazlarda performansın nasıl test edileceği ve optimize edileceği. (`<input gerekiyor>`)
*   **Uygulama Boyutu Optimizasyonu:** Uygulama boyutunu düşük tutmak için kullanılacak teknikler (texture sıkıştırma, asset bundling). (`<input gerekiyor>`)
*   **Titreşim ve Haptik Geri Bildirim:** Dokunmatik etkileşimleri zenginleştirmek için titreşim geri bildiriminin kullanılması. (`<input gerekiyor>`)
