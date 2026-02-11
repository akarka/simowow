# Character Progression (Karakter Gelişimi)

Bu doküman, oyundaki "Oyuncu Karakterlerinin" zaman içindeki gelişimini, bu gelişimi etkileyen faktörleri (beceri, ekipman, moral) ve guild yönetim stratejileriyle nasıl entegre olduğunu tanımlar.

## 1. Temel Gelişim Parametreleri

Her bir oyuncu karakteri, raid performanslarını ve genel guild içindeki değerlerini etkileyen temel parametrelere sahiptir:

*   **Gear Item Level (ilvl):** Karakterin donanımının genel kalitesini ve gücünü temsil eden birleşik bir skor. Yüksek ilvl, genellikle daha iyi birincil ve ikincil istatistiklere dönüşür. Raidlerden kazanılan loot ile artar.
*   **Secondary Stats (İkincil İstatistikler):** Kritikal Vuruş Şansı, Hız, Mastery, Çok Yönlülük gibi savaş performansını artıran ek istatistikler. Ekipman yükseltmeleriyle artar.
*   **Skill Rating (Beceri Derecesi):** Karakterin sınıfı ve uzmanlığı konusundaki yeterliliğini gösteren sayısal bir değer. Başarılı raid karşılaşmaları ve "pratik" yoluyla gelişir.
*   **Morale (Moral):** Karakterin genel mutluluğunu ve motivasyonunu yansıtır. Yüksek moral performansı artırabilir, düşük moral olumsuz etkiler.
*   **Attendance Rate (Katılım Oranı):** Karakterin planlanan raidlere katılma olasılığı.

## 2. Gelişim Mekanikleri

Karakter ve guild ilerlemesi, raid karşılaşmaları ve stratejik yönetimle yönlendirilen sürekli bir gelişim döngüsüdür.

### 2.1 Skill Rating Gelişimi
*   **Pasif Kazanım:** Karakterler, başarılı raid karşılaşmalarına aktif katılım ve "training" (eğitim) yoluyla zamanla `Skill Rating` kazanır.
*   **Mekanik İcra:** Raid sırasında mekanikleri başarıyla uygulamak, `Skill Rating` için özel kazanımlar sağlayabilir.
*   **Yönetici Müdahalesi:** Oyuncu, belirli karakterler için `Skill Rating` büyümesini hızlandırmak amacıyla kaynak (oyun içi para birimi, eğitim süresi) yatırım yapabilir. (`<input gerekiyor>`)

### 2.2 Ekipman Yükseltmeleri
*   **Ana Kaynak:** Ekipman yükseltmelerinin birincil kaynağı, başarılı raid boss kesimleridir. Daha yüksek zorluk seviyesindeki bosslar daha iyi `ilvl` ekipman düşürür.
*   **Ekipman Geliştirme:** Ekipmanlar, enchant'lar, gem'ler ve yükseltmeler yoluyla daha da geliştirilebilir, bu da `ilvl` ve ikincil istatistikleri artırır. Bu süreç, "Item Economy" mekaniği ile bağlantılıdır.

### 2.3 Moral Değişimleri
*   **Pozitif Etkiler:** Başarılı raid kesimleri, nadir ganimet kazanımı, pozitif rastgele olaylar ve etkili guild yönetimi (adil ganimet dağıtımı, çatışma çözme) morali artırır.
*   **Negatif Etkiler:** Tekrarlayan raid wipe'ları, olumsuz rastgele olaylar, kötü ganimet şansı, karakter hareketsizliği (bench'te kalma) morali düşürür.
*   **Geribildirim Döngüsü:** Moral, boss zorluk hesaplamalarındaki `morale_mult` çarpanını doğrudan etkiler, böylece yüksek moral daha kolay savaşlara, kolay savaşlar da daha yüksek morale yol açar. Karakter `Personality Traits` moral değişimlerinin şiddetini etkiler.

## 3. Eksik Alanlar / Geliştirme Notları

*   **Skill Rating için detaylı formüller:** Hangi eylemler Skill Rating'i ne kadar artırır? (`<input gerekiyor>`)
*   **Karakter özel yetenekleri:** Skill Rating veya ilerlemeyle kilidi açılan yeni yetenekler veya pasif bonuslar olacak mı? (`<input gerekiyor>`)
*   **"Pratik" veya "Eğitim" mekaniği:** Karakterler raid dışında nasıl pratik yapabilir veya eğitim alabilir? (`<input gerekiyor>`)
*   **Moral eşikleri ve etkileri:** Düşük/yüksek moralin karakter performansı ve guildden ayrılma olasılığı üzerindeki kesin etkileri (`<input gerekiyor>`)
