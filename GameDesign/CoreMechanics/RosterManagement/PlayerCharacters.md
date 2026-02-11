# Player Characters (Oyuncu Karakterleri)

Bu doküman, oyundaki "Oyuncu Karakterlerinin" özelliklerini, kişilik tiplerini ve bunların oyun mekaniği üzerindeki etkilerini tanımlar. Oyuncular, pasif istatistik yığınları olmaktan öte, kendi kişilikleri ve beklentileri olan "NPC" birimler olarak simüle edilecektir.

## 1. Karakter Arketipleri ve Kişilik Özellikleri (Traits)

Oyuncu karakterleri, WoW Classic topluluğunda yaygın olarak görülen archetiplerden esinlenerek tasarlanmıştır. Bu arketipler, sadece birer etiket değil, oyunun algoritmalarına etki eden, oyuncunun yönetim stratejilerini doğrudan etkileyen özellikler (traits) sistemine sahip olacaktır.

### 1.1 The Loot Goblin
*   **Özellik (Trait):** Açgözlü (Greedy)
*   **Oyun İçi Etki (Mekanik):** Eşya alamadığında moral kaybı 2 kat hızlı olur. GDKP gibi sistemlerde teklifleri yükseltme eğilimi gösterir.
*   **Yönetim Stratejisi:** Önemsiz eşyaları vererek geçici olarak susturmak veya guildden ayrılma riskini göze almak.

### 1.2 The Casual Dad
*   **Özellik (Trait):** Güvenilir ama Yavaş (Reliable but Slow)
*   **Oyun İçi Etki (Mekanik):** Raidlere %100 katılım gösterme eğilimindedir ancak consumables (iksir vb.) getirme konusunda eksik kalabilir. Bazen AFK kalma riski taşır. Performansı ortalamanın altında olabilir.
*   **Yönetim Stratejisi:** Yedek kadroda tutmak veya "farm" görevlerinden muaf tutmak. Güvenilirliği nedeniyle önemli görevlerde değerlendirilebilir.

### 1.3 The Hardcore Parser
*   **Özellik (Trait):** Elitist
*   **Oyun İçi Etki (Mekanik):** DPS'i yüksektir ancak tehdit (threat) sınırını aşarak wipe'lara neden olabilir. Düşük performans gösteren guild üyelerine karşı "toxic" fısıltılar atma eğilimindedir.
*   **Yönetim Stratejisi:** Egosunu tatmin edecek özel görevler vermek veya performans odaklı guildlerde tutmak. Sosyal çatışmalara neden olabilir.

### 1.4 The E-Girl / Socialite
*   **Özellik (Trait):** Karizmatik (Charismatic)
*   **Oyun İçi Etki (Mekanik):** Raid performansı düşük olabilir ancak guild moralini (bir buff gibi) artırır. Guild'den ayrılması durumunda 3-4 başka oyuncuyu da peşinden götürme riski vardır.
*   **Yönetim Stratejisi:** Performans eksikliklerine rağmen sosyal faydaları nedeniyle "dokunulmazlık statüsü" vermek zorunda kalmak.

## 2. Karakter Gelişimi ve Performans

Karakterlerin `ilvl`, `skill rating` gibi nicel parametreleri, `Personality Traits` ile birleşerek dinamik bir performans profili oluşturacaktır.

*   **Skill Rating:** Raid katılımları ve başarılı mekanik icraları ile zamanla artar.
*   **Morale:** Başarılı raidler, iyi loot, pozitif sosyal etkileşimlerle artar; wipe'lar, bench'te kalma, kötü loot ile azalır. Kişilik özellikleri moral değişimlerini etkiler.
*   **Attendance Rate:** Karakterin raide katılım olasılığıdır. "Casual Dad" gibi tiplerde daha yüksek güvenilirlik, bazı random eventlerle düşebilir.

## 3. Yönetimsel Etkileşimler

Oyuncu, her bir karakterin bireysel özelliklerini ve ihtiyaçlarını göz önünde bulundurarak kadro seçimleri, loot kararları ve hatta sosyal etkileşimler aracılığıyla guild üyeleriyle etkileşime girecektir. Bu etkileşimler, guildin genel performansını ve istikrarını doğrudan etkileyecektir.

## 4. Eksik Alanlar / Geliştirme Notları

*   **Traitlerin detaylı matematiksel etkileri:** Her trait'in hangi mekaniklere yüzde kaç etki edeceği (`<input gerekiyor>`)
*   **Traitlerin edinilmesi/değişimi:** Karakterler zamanla trait kazanabilir veya kaybedebilir mi? (`<input gerekiyor>`)
*   **Karakterlerin özelleştirilmesi:** Görsel veya isimsel özelleştirme seçenekleri (`<input gerekiyor>`)
