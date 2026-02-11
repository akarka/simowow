# Mobile UI Strategy (Mobil Kullanıcı Arayüzü Stratejisi)

Bu doküman, mobil platformun kısıtlamaları ve fırsatları göz önünde bulundurularak, oyunun kullanıcı arayüzü (UI) ve kullanıcı deneyimi (UX) için genel stratejileri tanımlar. Amaç, veri yoğunluklu bir yönetim simülasyonunu mobil ekranda sezgisel ve erişilebilir kılmaktır.

## 1. Görsel Kapsam: Soyutlama ve Temsili Anlatım

Raid savaşlarının karmaşık 3D görselleştirmeleri yerine, performans ve netlik odaklı soyutlamalar benimsenecektir.

*   **2D "Dots" ve Taktiksel Harita (Football Manager Yaklaşımı):**
    *   Raid sırasında karakterler detaylı 3D modeller yerine, sınıf renkleriyle (örneğin Warrior: Kahverengi, Mage: Mavi, Rogue: Sarı) kodlanmış "noktalar" veya "ikonlar" olarak gösterilecektir.
    *   Boss sabit bir merkezde dururken, oyuncu bu noktaların formasyonunu kuş bakışı (top-down) bir haritada izler.
    *   **Avantajlar:** Animasyon maliyeti sıfıra iner, oyuncu görsele değil stratejik pozisyonlanmaya odaklanır, "Raid Leader" hissiyatını güçlendirir.
*   **Metin Tabanlı ve UI Odaklı Savaş (MUD/Log Stili):**
    *   Savaşın görselleştirilmesi yerine, akan bir "Combat Log" ve kritik anlarda çıkan karar kartları kullanılabilir.
    *   **Senaryo:** Ekranda "Main Tank kritik hasar aldı!" uyarısı belirir. Oyuncuya anlık bir karar sorulur: "Healer'ların manasını harcayarak büyük iyileştirme yap" veya "Off-Tank'ı devreye sok".
    *   **Referans:** Reigns oyunundaki kart kaydırma mekaniği, raid sırasındaki kritik kararlar (Wipe çağrısı yapmak, Battle Rez kullanmak vb.) için mükemmel bir kapsam daraltma yöntemidir.

## 2. Kadro Yönetimi ve UI Optimizasyonu

40 kişilik bir listeyi mobil ekranda yönetmenin zorlukları, UI/UX optimizasyonlarıyla aşılacaktır.

*   **Raid Boyutunun Optimize Edilmesi:** Raid boyutunun **20 veya 25 kişi ile sınırlanması**, hem UI tasarımını rahatlatır hem de oyuncunun bilişsel yükünü (cognitive load) azaltır.
*   **Hiyerarşik Yönetim (Squad System):** Oyuncu 40 kişiyi tek tek yönetmek yerine, sadece 8 "Sınıf Liderini" yönetmelidir.
    *   **İşleyiş:** Oyuncu "Mage Lideri"ne "Alan Hasarı (AoE) yapın" emri verir. Lider, kendi grubundaki 5 Mage'i yönetir. Bu, mikro yönetimi azaltırken stratejik derinliği korur.
*   **Akıllı Filtreleme ve Bağlamsal UI:** Ekranda tüm can barları yerine, sadece "Tehlikede Olanlar" veya "Özel Görevli Oyuncular" gösterilmelidir. Football Manager Mobile arayüzündeki gibi, oyuncu detaylara girmek istediğinde "drill-down" yapabilmelidir.

## 3. "Design by Width" ve Ölçeklenebilirlik

Mobil cihazların farklı ekran boyutları ve yönelimleri göz önünde bulundurularak esnek bir UI tasarımı benimsenecektir.

*   **Grid Yapısı:** 40 (veya 20-25) birimi ekranda göstermek için "Grid" (Izgara) yapısı kullanılacaktır. Bu yapı, karakterlerin durumunu hızlıca anlamak için renk kodlaması gibi görsel ipuçları sunar.
*   **Akıllı Bildirimler:** Oyuncu her şeyi takip etmek zorunda kalmamalıdır. Sistem, sadece kritik hataları (örn: "Healer Mana <%10") büyük, yanıp sönen ikonlarla bildirmelidir.
*   **Responsive Tasarım:** UI elementleri, ekran boyutuna ve yönelimine (yatay/dikey) göre dinamik olarak kendini ayarlamalıdır.

## 4. Eksik Alanlar / Geliştirme Notları

*   **Taktiksel Harita Detayları:** 2D "Dots" haritası üzerinde hangi bilgiler (boss'un alanı, tehlikeli bölgeler, karakterlerin durumları) nasıl gösterilecek? (`<input gerekiyor>`)
*   **Komutan Yetenekleri UI:** "Komutan Yetenekleri"ni kullanmak için mobil ekranda en uygun UI elementleri nelerdir (düğmeler, kaydırıcılar)? (`<input gerekiyor>`)
*   **Sınıf Lideri Arayüzü:** Sınıf liderlerine komut verme ve onların altındaki karakterleri takip etme arayüzü nasıl işleyecek? (`<input gerekiyor>`)
*   **Tablet Uyumluluğu:** Tabletler için özel bir UI optimizasyonu düşünülüyor mu? (`<input gerekiyor>`)
