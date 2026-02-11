# Boss Mechanics (Boss Mekanikleri)

Bu doküman, oyundaki raid boss'larının mekaniklerini, bu mekaniklerin nasıl tasarlandığını, parametrelerini, prosedürel olarak nasıl ölçeklendirildiğini ve Auto-Battler savaş sistemi içinde oyuncunun hazırlık ve stratejilerini nasıl etkileyeceğini tanımlar.

## 1. Standardize Edilmiş Boss Mekaniği Kategorileri

Boss mekanikleri, modüler kategoriler halinde standardize edilmiştir. Her kategori, zorluk ve karmaşıklık varyasyonları oluşturmak için ayarlanabilen temel parametrelere sahiptir. Bu mekanikler, çeşitli şekillerde birleştirilerek benzersiz boss karşılaşmaları oluşturur.

*   **Targeted Damage (Hedefli Hasar):** Boss'un bir veya daha fazla oyuncuyu hedef alarak hasar veren yetenekleri.
    *   *Parametreler:* Hasar miktarı (%), hedef sayısı, cast frekansı, cast süresi, debuff süresi.
*   **Area Control (AoE - Alan Kontrolü):** Oyuncuların belirli bir alandan çıkmasını veya hasar/debuff almasını gerektiren mekanikler.
    *   *Parametreler:* Alan boyutu, hasar miktarı (%), uygulanan debuff, etki süresi, cast frekansı, uyarı süresi.
*   **Interrupt/Crowd Control (CC - Kesme/Kalabalık Kontrolü):** Boss'un cast'ını kesmeyi veya ek/oyuncular üzerinde CC kullanmayı gerektiren yetenekler.
    *   *Parametreler:* Cast süresi, kesme penceresi, başarısızlık sonucu (raid-wide hasar, boss buff'ı), CC süresi, CC tipi.
*   **Add Spawns (Ek Düşmanlar):** Boss'un ek düşmanlar çağırması.
    *   *Parametreler:* Add sayısı, add sağlığı, add hasarı, spawn frekansı, add yetenekleri, yok olma koşulu.
*   **Raid Split (Raid Bölünmesi):** Raid'in farklı görevleri eş zamanlı olarak yapmak için birden fazla gruba ayrılmasını gerektiren mekanikler.
    *   *Parametreler:* Grup sayısı, grup başına gerekli roller, grup başına ayrı mekanikler, bölünme aşaması için zaman sınırı.
*   **Soak Mechanics (Hasar Emme Mekanikleri):** Bir veya daha fazla oyuncunun hasarı emmek veya olumsuz bir etkiyi önlemek için belirli bir alanda durmasını gerektiren yetenekler.
    *   *Parametreler:* Soak için gerekli oyuncu sayısı, oyuncu başına hasar, soaker'lara uygulanan debuff, soak alanı boyutu, frekans.
*   **Buff/Debuff Rotations (Buff/Debuff Rotasyonları):** Oyuncular veya boss üzerindeki biriken buff'ları veya debuff'ları yönetmeyi gerektiren mekanikler, genellikle takas veya dispel gerektirir.
    *   *Parametreler:* Ceza öncesi stack sayısı, buff/debuff süresi, stack başına ceza/fayda, dispel tipi, uygulama frekansı.
*   **Puzzle/Sequence (Bulmaca/Sıra):** Oyuncuların bir engeli aşmak için belirli bir eylem dizisini gerçekleştirmesini veya bir bulmacayı çözmesini gerektiren mekanikler.
    *   *Parametreler:* Dizideki adım sayısı, zaman sınırı, başarısızlık sonucu, görsel/işitsel ipuçları.

## 2. Prosedürel Boss Üretimi ve Ölçeklendirme

Oyun, teorik olarak sonsuz zorluk ölçeklendirmesi için boss karşılaşmalarının prosedürel olarak üretilmesini destekleyecektir.

*   **Mekanik Havuzu Seçimi:** Her yeni sezon veya ilerleme aşamasında, boss için standardize edilmiş mekanik kategorilerin bir alt kümesi rastgele seçilir. Seçilen mekanik sayısı, istenen `Mechanical_Complexity` değerine göre değişebilir.
*   **Parametre Rastgeleleştirme:** Seçilen her mekanik için temel parametreleri tanımlanmış bir aralıkta rastgeleleştirilir. Bu aralık, `scale_factor` (ölçek faktörü) arttıkça genişler.
*   **Mekanik Etkileşim Üretimi:** Sistem, seçilen mekanikler arasında sinerjik veya çelişkili etkileşimler yaratmaya çalışır (örn. AoE alanıyla birlikte interrupt gerektiren bir Add Spawn).
*   **Faz Tanımı:** Üretilen mekanikler, boss savaşının farklı aşamalarına atanır; sonraki aşamalarda yoğunluk ve karmaşıklık artar.

## 3. Boss Zorluk Hesaplama Modeli (`T_final`)

Bir raid boss karşılaşmasının genel zorluğu (`T_final`), temel zorluk (`T_base`) ve çeşitli çarpanlarla (`comp_mult`, `mech_mult`, `morale_mult`, `tactical_mult`, `scale_factor`, `random_var`) dinamik olarak belirlenir. Bu model, hem encounter ayarı üzerinde hassas kontrol sağlar hem de prosedürel üretimi kolaylaştırır.

*   **`T_base`:** Boss'un HP, hasar output ve mekanik sayısından türetilen temel zorluk değeri.
*   **Çarpanlar:**
    *   `comp_mult`: Raid kompozisyonunun sinerjisi ve dengesine göre zorluğu ayarlar.
    *   `mech_mult`: Aktif tüm mekaniklerin birleşik zorluğunu hesaba katar.
    *   `morale_mult`: Raid üyelerinin ortalama moraline göre performansı etkiler.
    *   `tactical_mult`: Oyuncunun seçtiği stratejiyi (agresif, dengeli, defansif) yansıtır.
    *   `scale_factor`: Oyuncunun ilerleme aşamasına veya "sezon seviyesine" göre zorluğu ölçeklendirir.
    *   `random_var`: Rastgele oyun içi olayların getirdiği değişken faktör.

## 4. Auto-Battler Entegrasyonu ve Oyuncu Etkileşimi

Auto-Battler savaş sisteminde, boss mekaniklerinin anlaşılması ve bunlara karşı hazırlık, başarının anahtarıdır.

*   **Hazırlık Odaklılık:** Oyuncu, boss'un bilinen mekaniklerine göre raid kompozisyonunu, ekipman seçimlerini (örn. Fire Resist) ve genel stratejiyi önceden belirler.
*   **Komutan Yetenekleri:** Boss'un kritik bir mekaniği tetiklendiğinde, oyuncu "Komutan Yetenekleri" aracılığıyla müdahale edebilir (örn. "Herkes Kenara!" komutuyla AoE'den kaçış). Bu, mekaniklerin başarılı bir şekilde atlatılmasında zamanlama becerisi yerine doğru komutun doğru zamanda verilmesini gerektirir.
*   **Geri Bildirim:** Savaş sırasında boss'un mekaniklerini ve bunların raid üzerindeki etkilerini gösteren UI uyarıları ve savaş log'ları, oyuncunun bir sonraki hazırlık için öğrenmesini sağlar.

## 5. Eksik Alanlar / Geliştirme Notları

*   **Boss mekaniği tanımlama formatı:** Her bir mekaniğin veri tabanında nasıl saklanacağı ve prosedürel üretim için hangi alanlara sahip olacağı (`<input gerekiyor>`)
*   **Prosedürel üretim algoritmaları:** Mekanikleri birleştirme ve dengeleme için kullanılacak algoritmalar (`<input gerekiyor>`)
*   **Boss'a özel yetenekler:** Prosedürel mekaniklere ek olarak bazı boss'ların "imza" veya benzersiz yetenekleri olacak mı? (`<input gerekiyor>`)
*   **Zorluk ölçeklendirme eğrisi:** `scale_factor`'ın mekanik parametrelerini (hasar, süre, frekans) nasıl etkilediğinin matematiksel detayları (`<input gerekiyor>`)
