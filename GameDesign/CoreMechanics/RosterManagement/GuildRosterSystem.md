# Guild Roster System (Guild Kadro Sistemi)

Bu doküman, oyuncunun guild kadrosunu nasıl yöneteceğini, raid seçim süreçlerini, işe alım mekaniklerini ve mobil platforma özel optimize edilmiş yönetim yaklaşımlarını tanımlar.

## 1. Kadro Havuzu ve Raid Seçimi

Oyuncu, 20 kişilik bir raid için yaklaşık 25-30 kişilik bir karakter havuzundan seçim yapmak zorundadır. Bu seçim süreci, sadece en güçlü karakterleri seçmekten öte, oyuncunun optimizasyon ve diplomasi becerilerini test eden kritik bir mekaniktir.

*   **Optimizasyon İkilemi:** Oyuncu, "en yüksek hasarı veren" karakter yerine "en güvenilir" veya "en az sorun çıkaran" karakteri seçmek zorunda kalabilir.
*   **Seçim Kriterleri:**
    *   **Karakter Performansı:** `ilvl`, `skill rating`, `class/spec` uygunluğu.
    *   **Karakter Güvenilirliği:** `Attendance Rate` (katılım oranı), `Morale` (moral durumu), `Personality Traits` (kişilik özellikleri) ile belirlenen güvenilirlik puanı.
    *   **Raid Kompozisyonu:** Boss mekaniklerine göre ideal tank/healer/DPS oranları ve sınıf sinerjileri.

## 2. İşe Alım ve Deneme Süreçleri

Yeni guild üyeleri, guildin genel yapısını ve performansını etkileyen önemli kararlardır.

*   **Başvuru Süreci:** Oyuncu, yeni üye başvurularını değerlendirir. Bu değerlendirme şunları içerebilir:
    *   `Gear Check` (ekipman kontrolü): Başvuranın ekipman seviyesinin guild standartlarına uygunluğu.
    *   `Log Review`: Geçmiş performans kayıtlarının incelenmesi (varsa).
    *   `Personality Trait` uyumluluğu: Mevcut guild üyeleriyle potansiyel sosyal etkileşim.
*   **Deneme Süresi:** Yeni üyeler için belirli bir deneme süresi uygulanabilir. Bu süre boyunca oyuncu, üyenin performansını ve uyumunu gözlemleyerek guild'e tam üyeliğini onaylayabilir veya reddedebilir. Bu süreç, oyuncuya bir İK (İnsan Kaynakları) müdürü rolü yükler.

## 3. Kadro Yönetimi ve UI Optimizasyonu (Kapsam Daraltma Önerileri)

Mobil platformun kısıtlamaları göz önüne alınarak, 20 kişilik bir kadroyu tek tek yönetmek yerine daha optimize edilmiş yaklaşımlar benimsenecektir.

*   **Raid Boyutunun Optimize Edilmesi:** Raid boyutunun 20 kişiye düşürülmesi. Bu, UI tasarımını rahatlatacak ve oyuncunun bilişsel yükünü azaltacaktır.
*   **Hiyerarşik Yönetim (Squad System):** Oyuncu, 40 kişiyi tek tek yönetmek yerine, belirli sayıda "Sınıf Lideri" (örneğin 8 Sınıf Lideri) üzerinden yönetim sağlayacaktır.
    *   **İşleyiş:** Oyuncu "Mage Lideri"ne "Alan Hasarı (AoE) yapın" emri verir. Lider, kendi grubundaki Mage'leri (5 Mage gibi) yönetir. Bu, mikro yönetimi azaltırken stratejik derinliği korur.
*   **Akıllı Filtreleme ve Bağlamsal UI:** Ekranda tüm can barları/durumlar yerine, sadece "Tehlikede Olanlar" veya "Özel Görevli Oyuncular" gibi kritik bilgiler gösterilecektir. Futbol Manager Mobile arayüzüne benzer şekilde, oyuncu detaylara girmek istediğinde "drill-down" yapabilmelidir.

## 4. Eksik Alanlar / Geliştirme Notları

*   **Sınıf Lideri atama mekaniği:** Sınıf liderleri nasıl belirlenecek? (`<input gerekiyor>`)
*   **Sınıf liderlerinin yetenekleri/pasifleri:** Liderlerin yönetme becerileri nasıl modellenecek? (`<input gerekiyor>`)
*   **İşe alım piyasasının dinamikleri:** Hangi classlar daha sık başvurur, hangi dönemlerde daha nitelikli oyuncular bulunur? (`<input gerekiyor>`)
*   **Kadro değişiminin guild moraline etkisi:** Bir oyuncuyu bench'e almak veya kicklemek diğer oyuncuların moralini nasıl etkiler? (`<input gerekiyor>`)
