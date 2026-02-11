# Guild Yönetimi Simülasyonu: Mobil Oyun Analizi ve Revize Edilmiş Mekanikler Özeti

Bu belge, "Guild Management Simulation Game" projesi için yapılan detaylı pazar analizi ve kapsam daraltma stratejileri doğrultusunda revize edilmiş oyun mekaniklerini ve tasarım yaklaşımlarını özetlemektedir.

## 1. Oyun Konsepti Analizi: "Officer Simulator" ve Sosyo-Politik Derinlik
*   **Çekirdek Mekaniklerin Dekonstrüksiyonu:** Oyunun türünü "Organizasyonel Davranış Simülatörü" olarak tanımlama.
    *   **1.1 Personel ve Kadro Yönetimi:** 40 kişilik raid kadrosunun yönetimi, "Bench" dinamiği, İşe Alım ve Deneme Süreleri.
    *   **1.2 Ganimet Politikası ve Dağıtım Sistemleri:** DKP, Loot Council, GDKP, Suicide Kings gibi sistemlerin "drama motoru" olarak işlevi, matematiksel optimizasyon ve sosyal tatmin dengesi.
    *   **1.3 Lojistik, Ekonomi ve Hazırlık:** Raid öncesi hazırlık süreçleri, kaynak yönetimi, Guild Bankası, "World Buffs" koordinasyonu.
    *   **1.4 Sosyal Simülasyon ve "İnsan Faktörü":** Oyuncu kişilik tipleri (Casual Dad, Loot Goblin, Min-Maxer), Kriz Senaryoları (Poaching, Guild Splits, GM Burnout).

## 2. Pazar Araştırması ve Rakip Analizi (Özet)
*   "Sosyal Derinlikli MMO Yönetim Simülasyonu" alanındaki pazar boşluğu.
*   **Doğrudan Rakipler ve Eksik Yönleri:** Raid Manager (savaş odaklı), Pocket Guild (casual), Tycoon ve Idle RPG'ler (insan faktörü eksikliği).
*   **Dolaylı Rakipler ve İlham Kaynakları:** Football Manager (UI/UX ve veri yoğunluğu), RimWorld/Dwarf Fortress (Emergent Storytelling, Traits sistemi), Heroes for Hire/GuildOS (masaüstü arayüz metaforu).

## 3. Kapsam Daraltma (Scoping Down) Stratejileri
*   Mobil platform kısıtlamaları ve MVP yaklaşımı doğrultusunda öneriler.
    *   **3.1 Görsel Kapsam: Soyutlama ve Temsili Anlatım:**
        *   2D "Dots" ve Taktiksel Harita Yaklaşımı (Football Manager benzeri).
        *   Metin Tabanlı ve UI Odaklı Savaş (Combat Log, Reigns benzeri karar kartları).
    *   **3.2 Kadro Yönetimi ve UI Optimizasyonu:**
        *   Raid boyutunu 20 veya 25 kişi ile sınırlamak.
        *   Hiyerarşik Yönetim (Squad System) ile 8 "Sınıf Lideri" üzerinden yönetim.
        *   Akıllı Filtreleme ve Bağlamsal UI.
    *   **3.3 Dünya ve Ekonomi Kapsamı: "Menu-Driven" Yaklaşım:**
        *   Dispatch Missions (Gönderme Görevleri) ile consumable farming.
        *   Simüle Edilmiş Sunucu Ekonomisi (AI kontrollü, bot etkisi).
    *   **3.4 Savaş Mekanikleri: "Auto-Battler" Dönüşümü:**
        *   %90 Hazırlık ve %10 Müdahale prensibi.
        *   Otomatik savaş, oyuncu sadece "Komutan Yetenekleri"ni (Cooldowns) kullanır.

## 4. İleri Seviye Tasarım: Sosyal Dinamikler ve "Drama Motoru"
*   **4.1 Kişilik Matrisi ve "Trait" Sistemi:** Oyuncu tiplerinin (Loot Goblin, Casual Dad vb.) oyun mekaniklerine entegrasyonu.
*   **4.2 Ganimet Dağıtımı "Mini Oyunu":** Müzakere simülasyonu, "fısıltı" mekaniği, sistem seçiminin sonuçları.
*   **4.3 Kriz Senaryoları ve Haftalık Toplantılar:** Reigns benzeri kart sistemi ile "Officer Toplantıları" ve kritik kararlar.

## 5. Kullanıcı Arayüzü (UI) ve Kullanıcı Deneyimi (UX) Tasarımı
*   **5.1 "Design by Width" ve Ölçeklenebilirlik:** Grid yapısı, akıllı bildirimler.
*   **5.2 GuildOS Arayüzü:** "Sanal Masaüstü" estetiği, tematik navigasyon.

## 6. Monetizasyon (Gelir Modeli) Stratejileri
*   **6.1 Gacha Sistemi (Recruitment):** "Oyuncu Başvuruları" üzerinden entegrasyon.
*   **6.2 Kozmetik ve Kolaylık (QoL):** Guild özelleştirmeleri, Manager Skins.
*   **6.3 Reklam Modeli (Rewarded Ads):** Raid Wipes sonrası tamir masrafları için opsiyonel reklamlar.

## 7. Sonuç ve Yol Haritası (Özet)
*   Projenin "sosyal mühendislik ve kriz yönetimi" oyunu olarak konumlandırılması.
*   Önerilen Geliştirme Yol Haritası (Faz 1: Prototip, Faz 2: Sosyal Motor, Faz 3: UI Polish, Faz 4: İçerik).
