# Information Hierarchy (Bilgi Hiyerarşisi)

Bu doküman, oyuncuya sunulan bilgilerin nasıl organize edileceğini, önceliklendirileceğini ve görselleştirileceğini tanımlar. Mobil platformda "veri yoğunluklu" bir oyunda, bilginin gizlenmesi değil, doğru hiyerarşide sunulması kritik öneme sahiptir. Amaç, oyuncunun bilişsel yükünü (Cognitive Load) azaltmaktır.

## 1. Bilgi Önceliklendirme ve Süzme

Oyuncu, tüm detayları aynı anda görmek zorunda kalmamalıdır. Sistem, kritik bilgileri öne çıkarırken, daha az acil detayları isteğe bağlı olarak erişilebilir kılar.

*   **Akıllı Bildirimler:** Sistem, sadece kritik hataları veya acil durumları (örn: "Healer Mana <%10", "Main Tank kritik hasar aldı!") büyük, yanıp sönen ikonlar veya belirgin uyarı mesajlarıyla bildirmelidir.
*   **Bağlamsal UI:** Oyuncunun o anki görevine veya baktığı ekrana göre ilgili bilgilerin önceliklendirilmesi. Örneğin, `Raid Execution` sırasında karakterin `Consumables` envanteri yerine canı ve mana durumu öncelikli olur.
*   **Drill-down Mekaniği:** `Football Manager Mobile` arayüzüne benzer şekilde, oyuncu bir özet bilgiyi gördüğünde, daha fazla detay için kolayca "drill-down" yapabilmelidir. Örneğin, bir karakterin sağlık durumunu gösteren bir ikona dokunulduğunda, o karakterin detaylı statü sayfası açılabilir.

## 2. Görselleştirme ve Renk Kodlaması

Bilgiler, metin ağırlıklı olmaktan ziyade, hızlıca yorumlanabilen görsel ipuçlarıyla desteklenmelidir.

*   **Grid Yapısı ve Renk Kodlaması:** `Mobile UI Strategy` dokümanında belirtildiği gibi, karakter listeleri veya raid çerçeveleri için `Grid` (Izgara) yapısı kullanılacaktır.
    *   **Durum Göstergeleri:** Karakterlerin canı azaldıkça ızgaradaki kutunun rengi yeşilden kırmızıya dönmeli. Üzerindeki yazıyı okumasa bile oyuncu, renk koduyla durumun aciliyetini anlamalıdır.
    *   **Buff/Debuff İkonları:** Karakterler üzerindeki önemli buff/debuff'lar, küçük ve tanınabilir ikonlarla gösterilmelidir.
*   **Progress Barları:** Raid boss'larının veya görevlerin ilerlemesi, net ve anlaşılır progress barları ile görselleştirilir.

## 3. Bilgi Gruplaması ve Modülerlik

İlgili bilgiler, hiyerarşik olarak gruplandırılmalı ve farklı ekranlarda veya panellerde modüler bir şekilde sunulmalıdır.

*   **Ana Ekran (Dashboard):** Guildin genel durumunu (gold, raid ilerlemesi, genel moral) gösteren yüksek seviyeli bir özet ekranı. Buradan alt menülere kolayca geçiş sağlanır.
*   **Detay Panelleri:** Bir karakterin veya boss'un detaylarına inildiğinde, ilgili tüm bilgiler (statlar, traitler, mekanikler) kendi içinde mantıksal olarak gruplandırılmış panellerde sunulur.
*   **Navigasyon:** `GuildOS Interface Concept` dokümanında belirtileceği üzere, sekmeli navigasyon veya "sanal masaüstü" ikonları, farklı bilgi alanları arasında kolay geçişi sağlamalıdır.

## 4. Bilişsel Yükü Azaltma Stratejileri

*   **Tutarlılık:** UI elementleri ve bilgi sunumu, oyunun genelinde tutarlı olmalıdır. Öğrenilen bir kalıp, oyunun farklı bölümlerinde de geçerli olmalıdır.
*   **Net Dil ve Semboller:** Kullanılan metinler kısa, net ve anlaşılır olmalıdır. Semboller ve ikonlar, evrensel olarak tanınabilir veya oyun içinde kolayca öğrenilebilir olmalıdır.
*   **Gereksiz Bilgiyi Gizleme:** Oyuncunun o anda ihtiyacı olmayan bilgiler varsayılan olarak gizlenmeli, ancak erişilebilir olmalıdır.

## 5. Eksik Alanlar / Geliştirme Notları

*   **Spesifik UI Elementleri:** Her bir bilgi türü için kullanılacak spesifik UI elementleri (grafikler, tablolar, listeler) ve bunların mobil uyumluluğu. (`<input gerekiyor>`)
*   **Özelleştirme Seçenekleri:** Oyuncunun hangi bilgileri hangi ekranlarda görmek istediğini özelleştirmesine izin veren mekanikler. (`<input gerekiyor>`)
*   **Eğitim (Tutorial):** Oyuncunun bilgi hiyerarşisini ve UI'ı anlamasına yardımcı olacak bir başlangıç eğitimi. (`<input gerekiyor>`)
