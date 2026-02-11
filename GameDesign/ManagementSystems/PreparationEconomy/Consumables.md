# Consumables (Tüketilebilir Malzemeler)

Bu doküman, oyundaki tüketilebilir malzemelerin (consumables) önemini, raid hazırlığındaki rollerini, edinme mekaniklerini ve guild ekonomisi içindeki yerini tanımlar.

## 1. Tüketilebilir Malzemelerin Önemi

Flask'lar, potion'lar, buff food'lar gibi tüketilebilir malzemeler, başarılı raidler için kritik öneme sahiptir. Karakterlerin performansını geçici olarak artırarak boss karşılaşmalarında gerekli DPS/HPS eşiklerinin karşılanmasına yardımcı olurlar.

*   **Raid Performansı:** Her raid için belirli tüketilebilir malzemelerin toplanması zorunludur. Bunların kullanımı, raid'in genel gücünü ve başarı şansını artırır.
*   **Maliyet:** Tüketilebilir malzemelerin tedariki, guild ekonomisi üzerinde önemli bir maliyet kalemi oluşturur.

## 2. Edinme Mekanikleri: "Dispatch Missions" (Gönderme Görevleri)

Oyuncunun manuel olarak açık dünyada "farm" yapması yerine, tüketilebilir malzemelerin edinimi "Menu-Driven" (Menü Odaklı) bir yaklaşımla "Dispatch Missions" aracılığıyla simüle edilecektir.

*   **Görev Atama:** Oyuncu, belirli karakterleri veya grupları (örn. "Mage ekibini Black Lotus toplamaya gönder") belirli kaynakları toplamak üzere görevlendirir.
*   **Başarı Şansı:** Görevlerin başarı şansı, görevlendirilen karakterlerin `Personality Traits` (örn. çalışkanlık), `Skill Rating` (örn. toplama mesleği becerisi), `Morale` ve simüle edilmiş sunucu ekonomisindeki `PvP Yoğunluğu` (istatistiksel bir değer) gibi faktörlere bağlı olacaktır.
*   **Süre ve Getiri:** Görevler belirli bir süre alır ve başarılı olmaları durumunda belirli miktarda tüketilebilir malzeme veya crafting materyali getirirler.
*   **Kaynak Türleri:** Flask materyalleri (örn. Black Lotus), iksir hammaddeleri, yemek malzemeleri (örn. balıklar).

## 3. Consumable Yönetimi ve Guild Bankası

Toplanan tüketilebilir malzemeler öncelikle `GuildBank`'ta depolanır ve ihtiyaç durumunda raid üyelerine dağıtılır.

*   **Dağıtım Politikası:** Hangi karakterlere hangi consumable'ların verileceği, guildin stratejisi ve kaynak durumuyla belirlenir. Özellikle tanklar ve kilit DPS'ler öncelikli olabilir.
*   **Denetim:** Karakterlerin raid öncesi veya sırasında gerekli consumable'ları kullanıp kullanmadığının takibi. "I forgot my consumes" (consumable'larımı unuttum) durumu, `Roster Management` ve `Guild Politics & Culture` alanlarında drama yaratabilir.

## 4. Dış Etkenlerin Rolü

`Item Economy` dokümanında belirtildiği gibi, dış etkenler tüketilebilir malzeme piyasasını önemli ölçüde etkiler.

*   **Simüle Edilmiş Sunucu Ekonomisi:** Consumable'ların fiyatları, simüle edilmiş sunucu ekonomisi tarafından belirlenir. `Bot Etkisi`, Black Lotus gibi nadir materyallerin fiyatlarını manipüle edebilir.
*   **Streamer Etkisi:** Bir streamer'ın belirli bir consumable'ı öne çıkarması, ona olan talebi ve dolayısıyla fiyatını artırabilir.

## 5. Eksik Alanlar / Geliştirme Notları

*   **Consumable Türleri ve Etkileri:** Hangi tüketilebilir malzemeler oyunda olacak ve bunların karakter performansına etkileri nelerdir? (`<input gerekiyor>`)
*   **Görevlendirilebilecek karakter sayısı:** Bir "Dispatch Mission" için kaç karakter görevlendirilebilir? (`<input gerekiyor>`)
*   **Görev başarısızlığı sonuçları:** Görev başarısız olursa karakterler ne gibi sonuçlarla karşılaşır (moral kaybı, yaralanma)? (`<input gerekiyor>`)
*   **Consumable farm guild eventleri:** Oyuncunun özel consumable farm eventleri düzenlemesi (`<input gerekiyor>`)
