# GuildOS Interface Concept (GuildOS Arayüz Konsepti)

Bu doküman, oyunun kullanıcı arayüzü (UI) için genel "Sanal Masaüstü" veya "GuildOS" estetiğini ve temasını tanımlar. `Heroes for Hire` ve `Hypnospace Outlaw` gibi oyunlardan ilham alınarak, oyuncuya kendini gerçekten bir bilgisayar başında raid yöneten bir "Officer" gibi hissettiren sürükleyici bir arayüz deneyimi sunulacaktır.

## 1. Sanal Masaüstü Estetiği

Oyunun arayüzü, eski bir işletim sisteminin (örn. retro Windows 95/XP veya Discord benzeri) "masaüstü" görünümünü taklit edecektir. Bu estetik, oyunun atmosferine büyük ölçüde katkıda bulunacaktır.

*   **Tema:** Retro bilgisayar arayüzü, hafif piksel sanatı dokunuşları veya minimalist bir "terminal" görünümü.
*   **Arka Plan:** Kişiselleştirilebilir masaüstü arka planı (örn. guild logosu, raid haritası).
*   **Fare İmleci:** Temaya uygun özel bir fare imleci (mobil cihazlarda dokunmatik eşdeğeri).

## 2. Navigasyon ve Uygulama Yönetimi

Klasik bir işletim sistemi metaforu, menüler ve sekmeler arasındaki gezinmeyi daha tematik ve sezgisel hale getirir.

*   **Masaüstü İkonları:** Ana oyun mekanikleri (Roster, Loot, Raid, Guild Bankası, Toplantılar, Monetizasyon vb.) masaüstünde birer "uygulama ikonu" olarak temsil edilecektir (örn. `Roster.exe`, `LootLog.txt`, `WorldMap.jpg`).
*   **Görev Çubuğu (Taskbar):** Açık olan tüm "uygulamaları" gösteren bir görev çubuğu veya alt bar. Oyuncu, bu bar üzerinden açık pencereler arasında hızlıca geçiş yapabilir.
*   **Pencere Sistemi:** Her oyun içi bölüm veya bilgi ekranı (örn. karakter profili, boss stratejisi, guild moral raporu) ayrı bir pencere olarak açılır, boyutu ayarlanabilir ve sürüklenerek yeri değiştirilebilir.
*   **Bildirimler:** Sistem mesajları veya önemli oyun içi olaylar (örn. "Ana Tank kritik hasar aldı!") masaüstü "popup" pencereleri veya sistem tepsisi bildirimleri olarak görünebilir.

## 3. Tematik UI Elementleri

Arayüzün her bir parçası, seçilen tema ile uyumlu olacaktır.

*   **Yazı Tipleri:** Retro veya terminal tarzı yazı tipleri.
*   **Ses Efektleri:** Eski bilgisayar açılış sesleri, bildirim sesleri, pencere açma/kapama sesleri.
*   **Simgeler:** Pikselleştirilmiş veya tematik simgeler.
*   **Animasyonlar:** Pencere açılış/kapanış animasyonları, dosya yükleme simülasyonları.

## 4. Kullanıcı Deneyimi Üzerindeki Etki

Bu arayüz konsepti, oyuncuya sadece bilgi sunmakla kalmayacak, aynı zamanda bir "rol yapma" unsuru da katacaktır.

*   **Sürükleyicilik:** Oyuncu, kendini gerçekten bir guild yöneticisinin bilgisayarının başındaymış gibi hissedecektir.
*   **Kontrol Hissi:** Masaüstü ortamının getirdiği aşinalık, oyuncuya karmaşık sistemler üzerinde daha fazla kontrol hissi verebilir.
*   **Kişiselleştirme:** Oyuncu, masaüstü ikonlarının yerleşimini veya arka planını özelleştirebilir.

## 5. Eksik Alanlar / Geliştirme Notları

*   **Mobil Uyarlama:** Dokunmatik ekranlar için pencere yönetimi, sürükle-bırak ve ikon etkileşimleri nasıl optimize edilecek? (`<input gerekiyor>`)
*   **Pencere Z-Order Yönetimi:** Birçok pencere açıkken, hangi pencerenin üstte olacağı ve nasıl yönetileceği. (`<input gerekiyor>`)
*   **Tema Seçenekleri:** Farklı işletim sistemi temaları veya renk şemaları sunulacak mı? (`<input gerekiyor>`)
*   **Widget'lar:** Masaüstünde küçük bilgi widget'ları (örn. raid ilerleme widget'ı, guild gold widget'ı) olacak mı? (`<input gerekiyor>`)
