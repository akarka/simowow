# Combat Simulation (Savaş Simülasyonu)

Bu doküman, raid savaşlarının mobil platforma uygun "Auto-Battler" dönüşümünü, oyuncunun savaşa müdahale mekaniklerini ve genel savaş döngüsünü tanımlar. Odak noktası, oyuncunun anlık refleksleri yerine hazırlık ve stratejik komuta becerileridir.

## 1. Savaşın Temel Prensibi: %90 Hazırlık, %10 Müdahale

Savaş mekanikleri, dokunmatik kontrollerle anlık refleks gerektiren "interrupts", "dispels" veya "threat management" gibi mikro yönetimlerden arındırılmıştır. Savaş, oyuncunun ön hazırlığının ve stratejik kararlarının belirleyici olduğu bir "Auto-Battler" sistemi şeklinde işleyecektir.

*   **Hazırlık Aşaması:** Savaşın %90'lık kısmını oluşturur. Bu aşamada oyuncu şunları yapar:
    *   **Kadro Seçimi ve Kompozisyon:** Boss'a ve mekaniklerine uygun karakterleri seçer.
    *   **Ekipman Dağıtımı:** Doğru direnç (Fire Resist, Nature Resist) ekipmanlarını dağıtır.
    *   **Grup Ayarlamaları:** Tank grupları, Healer rotasyonları gibi düzenlemeler yapar.
    *   **Strateji Belirleme:** Boss'un mekaniklerine karşı genel bir savaş stratejisi belirler.
*   **Müdahale Aşaması:** Savaş başladığında karakterler otomatik olarak hareket eder. Oyuncunun doğrudan müdahalesi %10 ile sınırlıdır ve "Komutan Yetenekleri" (Cooldowns) aracılığıyla gerçekleşir.

## 2. Otomatik Savaş ve Komutan Yetenekleri

Karakterler, belirlenen stratejiler ve yapay zeka seviyeleri doğrultusunda kendi aksiyonlarını otomatik olarak gerçekleştirir. Oyuncu, savaşın akışına kritik anlarda müdahale eder.

*   **Otomatik Karakter Aksiyonları:** DPS'ler vurur, Healer'lar iyileştirir, Tank'lar tehdit oluşturur ve hasar emer. Bu aksiyonların etkinliği karakterlerin `Skill Rating`, `Gear Item Level` ve `Personality Traits` gibi özelliklerine bağlıdır.
*   **Komutan Yetenekleri (Cooldowns):** Oyuncunun savaş sırasında kullanabileceği, raid'in gidişatını değiştirebilecek güçlü yeteneklerdir. Örnekler:
    *   "Herkes Kenara!" (Boss bir alan hasarı yapacağında, tüm raid'in alandan çıkması için komut).
    *   "Büyük İyileştirme Dalgaları!" (Raid genelinde yüksek hasar alındığında tüm healer'ların en güçlü iyileştirme yeteneklerini kullanması).
    *   "Tankları Değiştir!" (Tank değiştirme mekaniği gerektiğinde komut).
*   **Müdahale Başarısı:** Komutan yeteneklerinin başarı oranı, oyuncuların reaksiyon süresine değil, karakterlerin yapay zeka seviyesine, `Morale` durumuna ve oyuncunun komutu verme zamanlamasına bağlıdır.

## 3. Savaş Akışı ve Geri Bildirim

Savaş, bir dizi aşama veya faza sahip olabilir. Oyuncuya, savaşın gidişatı hakkında önemli geri bildirimler sağlanır.

*   **Savaş Log'u:** Savaş sırasında önemli olayları (hasar, iyileştirme, mekanik başarı/başarısızlığı) gösteren akıcı bir metin log'u.
*   **Kritik Uyarılar:** "Ana Tank Kritik Hasar Aldı!", "Healer Mana <%10" gibi belirgin UI uyarıları.
*   **Karar Kartları:** Kritik anlarda Reigns oyunundaki gibi, oyuncuya anlık kararlar soran kartlar (örn. "Wipe çağrısı yap", "Battle Rez kullan").

## 4. Eksik Alanlar / Geliştirme Notları

*   **Komutan Yeteneklerinin çeşitliliği ve maliyeti:** Hangi yetenekler olacak, cooldown süreleri ve enerji/mana maliyetleri nasıl belirlenecek? (`<input gerekiyor>`)
*   **Karakter AI'sının detayları:** Hangi koşullar altında karakterler hangi yetenekleri kullanacak, hangi stratejilere öncelik verecek? (`<input gerekiyor>`)
*   **Savaş arayüzü tasarımı:** Mobil ekranda savaşın gidişatını takip etmek ve komutan yeteneklerini kullanmak için UI nasıl görünecek? (`<input gerekiyor>`)
*   **Savaş sonu istatistikleri:** DPS, HPS, alınan hasar gibi detaylı raporlama (`<input gerekiyor>`)
