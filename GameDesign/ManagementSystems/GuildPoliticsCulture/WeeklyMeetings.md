# Weekly Meetings (Haftalık Toplantılar)

Bu doküman, oyuncunun (Guild Master olarak) haftalık olarak düzenleyeceği "Officer Toplantıları" veya genel "Guild Toplantıları" mekaniğini, bu toplantılarda ele alınacak gündem maddelerini, karar alma süreçlerini ve bu toplantıların guild yönetimi üzerindeki etkilerini tanımlar. Toplantılar, Reigns oyunundaki kart sistemine benzer bir yapıya sahip olacaktır.

## 1. Toplantı Mekaniği: Kart Sistemi

Haftalık toplantılar, oyuncuya farklı gündem maddelerini ve kriz senaryolarını "karar kartları" aracılığıyla sunar. Oyuncu, bu kartlar üzerinde seçim yaparak guildin gidişatını belirler.

*   **Toplantı Sıklığı:** Haftalık (veya belirli bir oyun içi döngüye göre).
*   **Gündem Oluşumu:** Toplantı gündemi, guildin mevcut durumuna (moral, gold, raid ilerlemesi), aktif kriz senaryolarına ve rastgele olaylara göre dinamik olarak oluşur.
*   **Karar Kartları:** Her bir gündem maddesi, ekranda bir "kart" olarak belirir. Kartın üzerinde konunun özeti ve oyuncunun seçebileceği 2-3 farklı aksiyon seçeneği bulunur.
*   **Çok Yönlü Sonuçlar:** Her aksiyonun kısa ve uzun vadeli sonuçları vardır. Bu sonuçlar; guild morali, gold miktarı, karakter morali, raid performansı, `Personality Traits`'e sahip karakterlerin tepkileri gibi farklı metrikleri etkiler.

## 2. Tipik Toplantı Gündemleri ve Karar Örnekleri

Haftalık toplantılarda ele alınabilecek tipik konular ve oyuncunun verebileceği kararlar:

### 2.1 Loot Politikası Değerlendirmesi
*   **Kart Örneği:** "Guild üyeleri mevcut DKP sisteminden şikayetçi. Yeni oyuncular loot alamadığını, eski oyuncular ise DKP'nin değersizleştiğini düşünüyor."
*   **Seçenekler:**
    *   "Sistemi DKP'den EPGP'ye çevir." (Yeni oyuncuları mutlu eder, ancak eski oyuncuların tepkisini çekebilir.)
    *   "Mevcut sistemi savun, sorun yok." (Kısa vadede değişiklik olmaz, ancak memnuniyetsizlik artabilir.)
    *   "Bir defaya mahsus yeni oyunculara DKP bonusu ver." (Geçici çözüm, uzun vadeli sorunları çözmez.)

### 2.2 Raid Stratejisi ve Performans
*   **Kart Örneği:** "Geçen haftaki raidlerde DPS yetersizliği nedeniyle boss'u kesemedik. Raid kompozisyonunu değiştirmeliyiz."
*   **Seçenekler:**
    *   "Bazı healerları DPS'e çevir." (Heal yetersizliğine yol açabilir, riskli.)
    *   "DPS'i düşük olanları bench'e al, yerlerine yenilerini dene." (Bench'e alınanların moralini düşürür, `Crisis Scenarios` tetikleyebilir.)
    *   "Consumable kullanımını zorunlu kıl." (Oyunculara ek maliyet bindirir, tepki çekebilir.)

### 2.3 Kriz Yönetimi (Örnek: Poaching)
*   **Kart Örneği:** (`CrisisScenarios.md` dokümanındaki örnek senaryo kullanılabilir: "Ana Tankımız (MT), rakip guild 'Death & Taxes'tan teklif aldı...")

### 2.4 İşe Alım Politikası
*   **Kart Örneği:** "Yeni bir Officer, guild'in `Roster`ında Rogue açığı olduğunu düşünüyor ve aktif olarak Rogue arayışına girmeyi öneriyor."
*   **Seçenekler:**
    *   "Sadece Rogue alımı için ilan ver." (Diğer sınıf başvuranlarını dışlar, guildin esnekliğini azaltır.)
    *   "Herhangi bir iyi DPS başvurusunu değerlendir." (Açığı kapatmayabilir, ancak daha geniş bir havuzdan seçim sağlar.)
    *   "Mevcut oyuncuların alt karakterlerini Rogue olarak geliştirmesini teşvik et." (Zaman ve kaynak gerektirir.)

## 3. Toplantı Katılımcıları ve Etkileşimler

Toplantılar genellikle oyuncu (Guild Master) ve Officer'lar (AI karakterler) arasında geçecektir. Officer'ların `Personality Traits`'leri ve geçmiş deneyimleri, kartlara verdikleri tepkileri ve önerileri etkileyecektir.

*   **Officer Geri Bildirimleri:** Her karar seçeneği için Officer'lar farklı görüşler sunabilir. Oyuncu, bu görüşleri dikkate alarak son kararını verir.
*   **Karar Güvenilirliği:** Oyuncunun geçmiş kararlarının tutarlılığı, Officer'ların ve genel olarak guildin oyuncuya duyduğu güveni etkiler.

## 4. Eksik Alanlar / Geliştirme Notları

*   **Kart tasarımları ve görselleştirme:** Mobil UI'da kartlar nasıl görünecek, bilgiyi nasıl sunacak? (`<input gerekiyor>`)
*   **Karar seçeneklerinin sayısı ve karmaşıklığı:** Her kart için kaç seçenek olacak ve bu seçeneklerin sonuçları ne kadar öngörülebilir olacak? (`<input gerekiyor>`)
*   **Toplantı UI:** Oyuncunun toplantıları yönettiği arayüzün akışı nasıl olacak? (`<input gerekiyor>`)
*   **Officer'ların Traitlerine göre özelleştirilmiş tepkiler:** Officer AI'larının kararlara nasıl tepki vereceği ve bu tepkilerin sonraki toplantılarda veya `Social Dynamics` üzerinde nasıl bir etki yaratacağı. (`<input gerekiyor>`)
