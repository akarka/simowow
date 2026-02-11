# Loot Distribution Methods (Ganimet Dağıtım Yöntemleri)

Bu doküman, oyundaki farklı ganimet dağıtım sistemlerini, mekanik işleyişlerini, yarattıkları sosyal riskleri (drama potansiyeli) ve oyuncu üzerindeki yönetim yükünü tanımlar. Oyuncu, guild kültürüne ve hedeflerine uygun bir dağıtım sistemi seçmek zorundadır.

## 1. Ganimet Sistemi Türleri ve Özellikleri

`Mobil Oyun Analizi ve Kapsam Daraltma.txt` belgesinde belirtilen ganimet sistemleri, sadece birer algoritma değil, aynı zamanda birer "drama motoru"dur. Bu sistemlerin varlığı, oyuncuyu sadece matematiksel optimizasyon (kime en çok stat verir?) ile sosyal tatmin (kimi mutlu etmeliyim?) arasında seçim yapmaya zorlar.

### 1.1 DKP (Dragon Kill Points)
*   **Mekanik İşleyiş:** Raid'lere katılarak puan biriktirme ve eşyalar için açık artırma usulüyle harcama.
*   **Sosyal Risk (Drama Potansiyeli):** Enflasyon (çok fazla DKP birikimi) ve yeni oyuncuların sistemde geride kalması, yeterli puanı olmadığı için loot alamaması sorunu.
*   **Yönetim Yükü:** Düşük (Genellikle otomatik hesaplama ile yönetilir).
*   **Kültürel Etki:** Uzun süreli ve düzenli katılımı ödüllendirir.

### 1.2 Loot Council
*   **Mekanik İşleyiş:** Yönetimin (guild master ve officer'lar) kararıyla eşyanın kime verileceğine doğrudan karar verilmesi. Kararlar genellikle upgrade seviyesi, katılım, performans gibi faktörlere dayanır.
*   **Sosyal Risk (Drama Potansiyeli):** "Favoritizm" ve "Yolsuzluk" suçlamaları, kararların şeffaf olmaması durumunda büyük guild içi çatışmalar.
*   **Yönetim Yükü:** Yüksek (Manuel karar alma, kararları savunma ve açıklamalar yapma gerekliliği).
*   **Kültürel Etki:** Optimal gear dağıtımına olanak tanır ancak guild içi güvene dayalıdır.

### 1.3 GDKP (Gold Bid - Gold DKP)
*   **Mekanik İşleyiş:** Eşyaların raid içinde altın karşılığı açık artırma ile satılması. Elde edilen altın, raid sonu katılımcılara dağıtılır.
*   **Sosyal Risk (Drama Potansiyeli):** "Pay-to-Win" algısı yaratabilir. Gerçek para ticareti (RMT) simülasyonuna yol açabilir. "Hardcore" oyuncuların "Casual" oyunculara paralı askerlik yapmasına neden olabilir, bu da guild kültürünü yozlaştırır.
*   **Yönetim Yükü:** Orta (Oyun içi ekonomi dengesini bozma riski taşır).
*   **Kültürel Etki:** Gold zengini oyuncuların hızlıca gearlanmasını sağlar, ancak guild içi dayanışmayı azaltabilir.

### 1.4 Suicide Kings
*   **Mekanik İşleyiş:** Önceden belirlenmiş bir liste sırasına göre eşyaların dağıtılması. Bir oyuncu eşya aldığında listenin sonuna geçer.
*   **Sosyal Risk (Drama Potansiyeli):** Liste sırası değişmezliği nedeniyle özellikle listenin sonunda kalan oyuncuların motivasyon kaybı. Belli itemlara ihtiyaç duymayan oyuncuların sıra yanmasın diye item almaması.
*   **Yönetim Yükü:** Düşük.
*   **Kültürel Etki:** Şeffaf ve öngörülebilir bir sistemdir ancak esneklikten yoksundur.

## 2. Sistem Seçiminin Sonuçları

Oyuncu, oyun başında (veya haftalık toplantılarda) dağıtım sistemini seçmelidir. Bu seçimin doğrudan sonuçları olacaktır:

*   **DKP:** Adil ancak yeni oyuncu bulmayı zorlaştırır (Enflasyon sorunu).
*   **Loot Council:** Esnektir ancak dedikodu (Drama) puanını artırır.
*   **GDKP:** Guildi zenginleştirir ancak "Hardcore" oyuncuların "Casual" oyunculara paralı askerlik yapmasına neden olur, bu da guild kültürünü yozlaştırır.

## 3. Eksik Alanlar / Geliştirme Notları

*   **Sistem Değişimi Mekaniği:** Guildler oyun içinde loot dağıtım sistemini değiştirebilir mi? Değişim kararı nasıl alınır ve olası sonuçları nelerdir? (`<input gerekiyor>`)
*   **Player Personality Traits ile Etkileşim:** "Loot Goblin" gibi oyuncu tipleri, hangi sistemde daha mutlu/mutsuz olur veya sistemi manipüle etmeye çalışır? (`<input gerekiyor>`)
*   **Off-spec ve Main-spec Loot Kuralları:** Her sistemde off-spec itemlara nasıl yaklaşılır? (`<input gerekiyor>`)
*   **Legendary Item Dağıtımı:** Efsanevi eşyaların dağıtımı için özel kurallar veya mini-oyunlar var mı? (`<input gerekiyor>`)
