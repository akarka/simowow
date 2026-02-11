# MVP Definition (Minimum Uygulanabilir Ürün Tanımı)

Bu doküman, "Guild Management Simulation Game" için Minimum Uygulanabilir Ürün (MVP) kapsamını tanımlar. Mobil oyun geliştirmede MVP yaklaşımı, projenin hayatta kalması için kritiktir ve çekirdek oyun döngüsünü mümkün olan en erken aşamada oyuncularla buluşturmayı hedefler.

## 1. MVP'nin Amacı

MVP'nin temel amacı, oyunun çekirdek "Officer Simulator" deneyimini, yani "sosyal mühendislik ve kriz yönetimi" odaklı guild yönetimini doğrulamaktır. Bu, teknik karmaşıklığı minimize ederken, anlatısal derinliği ve UI/UX'i maksimize etmeyi içerir.

## 2. MVP Kapsamındaki Temel Özellikler

MVP, `Mobil Oyun Analizi ve Kapsam Daraltma.txt` belgesinde önerilen "Geliştirme Yol Haritası"nın ilk iki fazını temel alacaktır:

### 2.1 Faz 1 (Prototip): Çekirdek Loop ve Savaş Mekaniği

Bu faz, oyunun temel döngüsünü ve daraltılmış savaş mekaniklerini içerir.

*   **2D "Dots" Savaş Sistemi:** `Mobile UI Strategy` dokümanında belirtildiği gibi, raid savaşları için basitleştirilmiş 2D ikonlar ve taktiksel harita kullanımı.
*   **Temel DKP/Loot Algoritması:** `Loot Distribution Methods` dokümanındaki DKP sisteminin metin tabanlı veya basit UI ile çalıştırılması. Loot'un dağıtımı ve karakterlere atanması.
*   **Basit Roster Yönetimi:** `Guild Roster System` dokümanında belirtilen kadro havuzu, raid seçimi ve temel karakter profillerinin (`Player Characters`) listelenmesi.
*   **Auto-Battler Savaş Simülasyonu:** `Combat Simulation` dokümanında belirtildiği gibi, %90 hazırlık, %10 müdahale prensibine dayalı otomatik savaş ve temel Komutan Yetenekleri.
*   **Boss Mekanikleri (Basit):** `Boss Mechanics` dokümanından seçilecek 1-2 basit boss mekaniği ve statik parametreler. Prosedürel üretim bu aşamada sınırlı olabilir.

### 2.2 Faz 2 (Sosyal Motor): İnsan Faktörü ve Drama

Bu faz, oyunun benzersiz sosyal dinamiklerini ve "insan faktörünü" MVP'ye dahil eder.

*   **Kişilik Özellikleri (Traits):** `Personality Traits` dokümanında belirtildiği gibi, temel karakter traitlerinin (örn. Loot Goblin, Casual Dad) sisteme entegrasyonu ve bu traitlerin moral/performans üzerindeki etkileri.
*   **"Drama Kartları" ve Haftalık Toplantılar:** `Weekly Meetings` dokümanında belirtildiği gibi, Reigns benzeri bir kart sistemi aracılığıyla temel kriz senaryolarının (`Crisis Scenarios`) ve haftalık toplantıların simülasyonu. Oyuncunun kararlarının sosyal dinamikler üzerindeki etkisi.
*   **Moral Sistemi:** Karakterlerin moralinin, traitleri ve oyuncunun kararlarına göre nasıl değiştiğinin modellenmesi.

## 3. MVP Kapsamının Dışında Kalanlar (İlk Sürüm İçin)

Aşağıdaki özellikler, MVP kapsamında yer almayacak ve sonraki fazlarda geliştirilecektir:

*   **Gelişmiş Raid Kompozisyon Optimizasyonu:** `Squad System` gibi hiyerarşik yönetim mekanikleri (Faz 3).
*   **Kompleks Ekonomi Simülasyonu:** `Item Economy` dokümanındaki tam simüle edilmiş sunucu ekonomisi ve "Bot Etkisi" (Faz 3).
*   **Geniş Kapsamlı Monetizasyon:** `Monetization Strategy` dokümanındaki tüm gelir modelleri (Gacha, kozmetikler, reklamlar) başlangıçta sınırlı veya hiç olmayabilir. (Faz 3 veya sonrası)
*   **Meta İlerleme:** Server sıralamaları, Achievement'lar ve detaylı sezonluk ilerleme mekanikleri (Faz 4).
*   **Tüm Boss Mekanikleri:** Sadece çekirdek boss mekaniklerinin bir alt kümesi MVP'de yer alacaktır. (Faz 4)

## 4. Eksik Alanlar / Geliştirme Notları

*   **MVP için spesifik metrikler:** MVP'nin başarısını ölçmek için kullanılacak anahtar performans göstergeleri (KPI'lar) nelerdir? (`<input gerekiyor>`)
*   **MVP deneme grupları:** MVP'yi hangi hedef kitleyle test edeceğiz ve geri bildirim süreci nasıl işleyecek? (`<input gerekiyor>`)
*   **MVP'nin görsel stili:** MVP'de kullanılacak 2D "Dots" sistemi için stil rehberi. (`<input gerekiyor>`)
