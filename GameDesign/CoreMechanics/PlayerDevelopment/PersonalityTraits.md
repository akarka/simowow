# Personality Traits (Kişilik Özellikleri)

Bu doküman, oyundaki "Oyuncu Karakterlerinin" davranışlarını, performanslarını ve guild içi etkileşimlerini derinden etkileyecek olan "Kişilik Özellikleri" (Personality Traits) sistemini detaylandırır. Bu sistem, karakterleri sadece istatistik yığınları olmaktan çıkarıp, duygusal ve sosyal talepleri olan bireylere dönüştürerek "insan faktörünü" simüle eder.

## 1. Kişilik Matrisi ve Trait Sistemi

Kişilik tipleri, basit etiketlerin ötesine geçerek, oyunun algoritmalarına etki eden, dinamik değişkenler olarak kodlanacaktır. RimWorld ve Crusader Kings III gibi oyunların "Trait" sistemleri bu konuda ilham kaynağıdır.

*   **Traitlerin Mekanik Entegrasyonu:** Her bir `Trait`, karakterin belirli oyun içi eylemlerini, kararlara tepkilerini, moral değişim hızını ve diğer karakterlerle olan ilişkilerini matematiksel olarak etkileyecektir.
*   **Trait Kategorileri:** Traitler; performans, sosyal, ekonomi ve güvenilirlik gibi farklı kategorilerde gruplandırılabilir. (`<input gerekiyor>`)

## 2. Örnek Traitler ve Oyun İçi Etkileri

`PlayerCharacters.md` belgesinde tanımlanan arketiplerin temelindeki traitler, oyun mekaniklerine aşağıdaki gibi entegre edilecektir:

*   **Greedy (Açgözlü):**
    *   **Etki:** Eşya alamadığında `Morale` kaybı 2 kat hızlanır. `GDKP` sisteminde daha yüksek teklif verme eğilimi gösterir. `Loot Council` kararlarından sonra isyan etme olasılığı daha yüksektir.
    *   **Yönetim Stratejisi:** Belirli aralıklarla sembolik eşyalarla ödüllendirme veya stratejik olarak önemli eşyalardan uzak tutma.
*   **Reliable but Slow (Güvenilir ama Yavaş):**
    *   **Etki:** `Attendance Rate` her zaman yüksektir. `Consumables` getirme konusunda düşüktür veya unutur. Savaş sırası mekaniklere tepki süresi diğer karakterlere göre daha yavaştır (`Combat Simulation`da bir gecikmeye neden olabilir).
    *   **Yönetim Stratejisi:** Sabit, düşük riskli rollerde kullanma (örn. off-tank veya raid healer) ve `consumables` eksikliklerini guild bankasından karşılama.
*   **Elitist:**
    *   **Etki:** Yüksek `Skill Rating` ve `ilvl` hedefler. Kendi performansı yüksek olsa da, düşük performans gösteren diğer karakterlerin `Morale` seviyesini düşüren "toxic" fısıltılar atma olasılığı yüksektir. `Threat Management` konusunda riskli oynamaya eğilimlidir.
    *   **Yönetim Stratejisi:** Yüksek performans gerektiren kilit rollerde kullanma, ancak guild içi sosyal dinamikler üzerinde denetim.
*   **Charismatic (Karizmatik):**
    *   **Etki:** Raid genelinde `Morale` üzerinde pozitif bir `Buff` etkisi yaratır. Guild'den ayrılması durumunda, belirli bir yüzdede diğer karakterlerin de guild'i terk etmesine neden olabilir (`Roster Management` için büyük risk).
    *   **Yönetim Stratejisi:** Genellikle kilit pozisyonlarda tutulur, sosyal dengeleyici olarak kullanılır.

## 3. Traitlerin Yönetici Kararlarıyla Etkileşimi

Oyuncunun ganimet dağıtımı, bench kararları, raid kompozisyonu ve kriz yönetimi gibi konulardaki tercihleri, karakterlerin Traitlerine göre farklı tepkilere yol açacaktır. Bu, oyunu bir "sosyal mühendislik" simülasyonuna dönüştürür.

*   **Bench Kararları:** `Bench Mechanics` dokümanında belirtildiği gibi, bench'te kalmak `Morale`'i düşürür ancak `Trait` bu düşüşün şiddetini ve sonuçlarını belirler.
*   **Loot Kararları:** `Loot Distribution Methods` dokümanında belirtildiği gibi, `Trait`ler, ganimet dağıtım kararlarına verilen tepkileri (memnuniyet, öfke, isyan) etkiler.

## 4. Trait Edinimi ve Değişimi

Karakterlerin `Trait`leri statik olmayabilir ve oyunun akışına göre değişebilir.

*   **Edinme:** Uzun süreli başarılar, başarısızlıklar veya belirli olaylar sonucunda yeni `Trait`ler kazanılabilir (örn. sürekli DKP alamayan bir oyuncu "Bitter" (Acımasız) traitini edinebilir). (`<input gerekiyor>`)
*   **Değişim:** Bazı `Trait`ler, oyuncunun başarılı yönetimi veya belirli oyun içi müdahalelerle zayıflatılabilir veya değiştirilebilir (örn. bir "Toxic" oyuncunun olumlu geri bildirimlerle daha "Supportive" hale gelmesi). (`<input gerekiyor>`)

## 5. Eksik Alanlar / Geliştirme Notları

*   **Traitlerin gizliliği/keşfi:** Oyuncu bir karakterin tüm `Trait`lerini baştan mı bilecek, yoksa oyun sırasında keşfedecek mi? (`<input gerekiyor>`)
*   **Trait çakışmaları ve sinerjileri:** Farklı Traitler birbiriyle nasıl etkileşime girer? (`<input gerekiyor>`)
*   **Yeni Trait fikirleri:** Daha fazla oyuncu arketipleri ve bunlara karşılık gelen traitler (`<input gerekiyor>`)
