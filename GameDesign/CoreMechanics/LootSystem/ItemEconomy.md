# Item Economy (Eşya Ekonomisi)

Bu doküman, oyun içindeki eşyaların ekonomisini, guild bankası yönetimini, kaynak toplama mekaniklerini ve simüle edilmiş dış etkenlerin eşya piyasası üzerindeki etkilerini tanımlar.

## 1. Eşya Kaynakları ve Akışı

Eşyalar, ana olarak raidlerden düşen ganimetler, görevlerden elde edilen ödüller ve karakterlerin "Dispatch Missions" (Gönderme Görevleri) aracılığıyla topladığı kaynaklar (crafting materyalleri, consumable'lar) yoluyla oyuna dahil olur.

## 2. Guild Bankası Yönetimi

Guild bankası, guild üyelerinin ortak kaynaklarını ve eşyalarını depoladığı merkezi bir yerdir. Oyuncu, guild bankasının yöneticisi olarak kritik kararlar vermek zorundadır.

*   **Ortak Kaynakların Yönetimi:** Guild bankasındaki materyaller, consumable'lar ve gold, raid hazırlığı ve karakterlerin geliştirilmesi için kullanılır.
*   **Finansman:** Özellikle tanklar ve en iyi DPS'ler gibi kilit oyuncuların pahalı consumable'lar veya enchant'lar ile finanse edilmesi.
*   **Katkı Sistemi:** Guild üyelerinin bankaya katkıda bulunma mekaniği ve "leech" (parazit) oyuncuların tespiti. (`<input gerekiyor>`)
*   **Eşya Saklama:** Guild bankasında "doğru oyuncu yok" diyerek eşya tutma ("Loot Hoarding") mekaniği ve bunun moral üzerindeki etkileri.

## 3. Simüle Edilmiş Sunucu Ekonomisi

Gerçek oyuncular arası bir pazar yeri (Auction House) kurmak yerine, oyunun ekonomisi tamamen yapay zeka tarafından simüle edilecektir.

*   **Fiyat Dinamikleri:** Consumable fiyatları, materyal değerleri ve eşya fiyatları, arz-talep dengesi ve dış etkenler tarafından dinamik olarak belirlenir.
*   **Bot Etkisi:** "Botting Problems" (Bot Sorunları), ekonomideki fiyatları düşüren veya nadir eşyaları tüketen rastgele "Global Event"ler olarak kurgulanacaktır. Oyuncu, botlardan ucuz malzeme alıp "etik değer" kaybetmek ile pahalıya kendi toplamak arasında seçim yapabilir. Bu, oyuncuya stratejik ve etik bir ikilem sunar.
*   **Enflasyon/Deflasyon:** Ekonomik olaylar ve guild'in genel gold kazanım hızı, oyunun geneline yayılan bir enflasyon/deflasyon dinamiği yaratabilir. (`<input gerekiyor>`)

## 4. Consumable ve Hazırlık Ekonomisi

Raid öncesi hazırlık süreçleri, guild ekonomisinin önemli bir parçasıdır.

*   **Consumable Farming:** Her raid için flask, potion, buff food toplanması gerekiyor. Bu, "Dispatch Missions" aracılığıyla gerçekleştirilir.
*   **Resistance Gear Farming:** Belirli bosslar için gerekli olan Fire Resist veya Nature Resist gibi ekipmanların toplanması. Bu da görevler aracılığıyla simüle edilebilir.
*   **Enchant/Gem Stratejisi:** Guild bankasında materyal yönetimi ve hangi karakterlere öncelik verileceği. Pahalı enchant'lar için bütçe tahsisi.

## 5. Dış Etkenler

Simüle edilmiş dış etkenler, eşya ekonomisi üzerinde önemli bir role sahiptir.

*   **Streamer Etkisi:** Büyük bir streamer'ın oyuna dahil olması veya belirli bir item/strat üzerine yoğunlaşması, o itemın/materyalin fiyatını değiştirebilir.
*   **Patch Değişiklikleri:** Simüle edilmiş oyun yamaları, bazı eşyaların değerini artırabilir veya azaltabilir.
*   **Black Lotus Kıtlığı:** Flask yapımı için gerekli olan nadir bir materyalin (Black Lotus gibi) botlar veya diğer simüle edilmiş guildler tarafından manipüle edilmesi, oyunun ekonomi dinamiğine derinlik katar.

## 6. Eksik Alanlar / Geliştirme Notları

*   **Crafting Sistemi:** Guild üyelerinin meslekleri (professions) nasıl yönetilir ve crafting sistemi ekonomiye nasıl entegre edilir? (`<input gerekiyor>`)
*   **Vendor Mekanikleri:** NPC satıcılar ve alıcılar, ekonomiye nasıl etki eder? (`<input gerekiyor>`)
*   **Ekonomi Yönetimi UI:** Oyuncunun ekonomi verilerini (fiyatlar, arz-talep) görebileceği bir arayüz. (`<input gerekiyor>`)
*   **Gold kazanım yolları:** Guild ve bireysel oyuncuların gold kazanma mekanikleri nelerdir? (`<input gerekiyor>`)
