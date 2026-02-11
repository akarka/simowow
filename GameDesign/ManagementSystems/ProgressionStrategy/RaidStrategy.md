# Raid Strategy (Raid Stratejisi)

Bu doküman, oyuncunun (Guild Master olarak) raid boss'larına karşı uygulayacağı stratejileri, bu stratejilerin geliştirilme, adapte edilme ve uygulanma mekaniklerini, raid kompozisyonunun ve boss mekaniklerinin strateji üzerindeki etkilerini tanımlar. Auto-Battler savaş sistemi bağlamında, stratejinin ana ekseni hazırlık ve planlama olacaktır.

## 1. Strateji Geliştirme ve Iterasyon

Her boss karşılaşması, benzersiz mekanikleri ve zorlukları nedeniyle özel bir strateji gerektirir. Oyuncu, stratejilerini "learning boss" aşamasında geliştirir ve "farming boss" aşamasında optimize eder.

*   **Öğrenme Aşaması ("Learning Boss"):**
    *   İlk wipe'lar ve başarısız denemeler, oyuncuya boss mekanikleri hakkında değerli bilgiler sağlar.
    *   `Combat Simulation` logları ve uyarıları, hangi mekaniklerin sorun yarattığını gösterir.
    *   Oyuncu, kadro kompozisyonu (`Roster Management`), ekipman seçimleri (`Item Economy`, `Consumables`) ve Komutan Yetenekleri (`Combat Simulation`) kullanımını ayarlayarak stratejiyi iteratif olarak geliştirir.
*   **Optimizasyon Aşaması ("Farming Boss"):**
    *   Boss başarıyla kesildikten sonra, strateji "speed run" veya daha az kaynak tüketimi için optimize edilir.
    *   Amaç, aynı başarıyı daha hızlı, daha tutarlı ve daha az maliyetle tekrarlamaktır.

## 2. Kompozisyon ve Mekanik Etkileşimi

Raid stratejisinin temeli, guild kadrosunun güçlü ve zayıf yönlerini boss mekanikleriyle eşleştirmektir.

*   **Raid Kompozisyonu:** `Guild Roster System` dokümanında belirtildiği gibi, boss'a özel ideal sınıf kompozisyonunu kurmak (örn. Ragnaros için mage stack, Patchwerk için warrior stack) stratejinin başlangıç noktasıdır. Sınıf sinerjileri ve buff dağılımı önemlidir.
*   **Boss Mekanikleri:** `Boss Mechanics` dokümanında detaylandırılan standardize edilmiş mekanikler (Targeted Damage, AoE, Interrupt/CC vb.) her boss için farklı kombinasyonlarda karşımıza çıkar. Strateji, bu mekaniklere karşı en etkili tepkiyi vermeyi hedefler.
    *   Örnek: Bir boss'un yoğun AoE mekaniği varsa, yüksek AoE hasarına sahip DPS'ler tercih edilebilir veya raid'in hayatta kalma yetenekleri artırılabilir.
    *   Örnek: Sık Interrupt gerektiren bir boss için, guildde yeterli `Interrupt` yeteneğine sahip karakterlerin olması kritik öneme sahiptir.

## 3. Auto-Battler Ortamında Strateji Uygulaması

Savaşın "Auto-Battler" prensibine dayanması, oyuncunun stratejisinin çoğunlukla raid öncesi planlamaya odaklandığı anlamına gelir.

*   **Ön Hazırlık:** Oyuncu, raid başlamadan önce tüm stratejik kararları (kim hangi rolde, hangi ekipmanlar kullanılacak, hangi Komutan Yetenekleri hangi durumlarda aktif edilecek) belirler.
*   **Komuta ve Kontrol:** Raid sırasında oyuncu, "Komutan Yetenekleri" aracılığıyla kilit anlarda stratejik komutlar verir. Bu, boss mekaniklerine verilen reaktif bir yanıttan çok, önceden planlanmış bir müdahaledir.
*   **Risk ve Ödül:** Agresif bir strateji (`Tactical Approach Multiplier`), daha yüksek DPS potansiyeli sunarken, wipe riskini artırabilir. Defansif bir strateji ise daha güvenli, ancak daha yavaş bir ilerleme anlamına gelebilir.

## 4. Wipe Yönetimi ve Öğrenme Eğrisi

Raid wipe'ları, strateji geliştirme sürecinin doğal bir parçasıdır. Oyuncunun bu durumlara nasıl tepki verdiği, guildin ilerlemesini etkiler.

*   **Wipe Sonuçları:** `Wipe recovery` (tamir masrafı, moral kaybı, zaman kaybı) `Raid Execution` altında detaylandırılacaktır.
*   **Öğrenme:** Her wipe, stratejideki zayıflıkları ve geliştirilmesi gereken alanları gösterir. Oyuncu, savaş loglarını analiz ederek ve `Weekly Meetings` sırasında officer'larla (AI) tartışarak stratejisini ayarlar.

## 5. Eksik Alanlar / Geliştirme Notları

*   **Strateji oluşturma arayüzü:** Oyuncunun raid stratejilerini görsel olarak oluşturabileceği veya ayarlayabileceği bir UI. (`<input gerekiyor>`)
*   **Simüle edilmiş PTR testleri:** Oyuncunun yeni stratejileri "Public Test Realm" benzeri bir ortamda test edebilmesi mekaniği. (`<input gerekiyor>`)
*   **Boss mekaniği ipuçları/zayıf noktaları:** Oyun, oyuncuya boss mekanikleri hakkında ipuçlarını nasıl sunacak? (`<input gerekiyor>`)
*   **Farklı zorluk seviyeleri için strateji varyasyonları:** Normal, Heroic, Mythic gibi farklı zorluk seviyeleri için stratejiler nasıl değişir? (`<input gerekiyor>`)
