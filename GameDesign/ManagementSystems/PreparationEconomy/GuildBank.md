# Guild Bank (Guild Bankası)

Bu doküman, guild bankasının işlevlerini, oyuncunun banka üzerindeki yönetim yetkilerini, kaynakların depolanması ve dağıtılması mekaniklerini ve guild ekonomisi içindeki rolünü tanımlar.

## 1. Guild Bankasının İşlevleri

Guild bankası, guild üyelerinin ortak kaynaklarını, eşyalarını ve altınını depoladığı ve yönettiği merkezi bir depodur. Temel işlevleri şunlardır:

*   **Kaynak Depolama:** Consumable'lar (flask, potion, buff food), crafting materyalleri, değerli eşyalar ve gold.
*   **Raid Hazırlığı:** Raid öncesi karakterlere gerekli consumable'ların sağlanması.
*   **Ekipman Geliştirme:** Karakterlerin ekipmanlarını geliştirmek için (enchant, gem) materyal tedariki.
*   **Acil Durum Fonu:** Beklenmedik durumlarda (örn. yüksek tamir faturaları, kilit bir oyuncunun acil ihtiyacı) kullanılacak gold rezervi.

## 2. Yönetim ve Erişim

Oyuncu (Guild Master), guild bankası üzerinde tam yetkiye sahiptir ancak bu yetkinin kullanımı "Guild Politics & Culture" üzerinde önemli etkiler yaratır.

*   **Erişim Katmanları:** Farklı guild rütbelerine (örn. Officer, Core Raider, Member) farklı erişim yetkileri atanabilir. Örneğin, Officer'lar belirli materyalleri çekebilirken, Member'lar sadece consumable'ları görebilir.
*   **Oyuncu Kararları:** Oyuncu, kimin neye erişebileceğine, hangi materyallerin kilitli tutulacağına veya öncelikli olarak kimlere dağıtılacağına karar verir.

## 3. Kaynak Yönetimi ve Dinamikler

Guild bankasındaki kaynaklar dinamiktir ve sürekli olarak giriş-çıkış halindedir.

*   **Katkı Sistemi:** Guild üyelerinin "Dispatch Missions" (Gönderme Görevleri) aracılığıyla veya doğrudan bağış yoluyla bankaya materyal/gold katkıda bulunma mekaniği.
    *   **"Leech" (Parazit) Sorunu:** Hiç katkıda bulunmayıp sürekli bankadan kaynak çeken oyuncuların tespiti ve yönetimi. Bu, `Player Personality Traits` ve `Guild Politics & Culture` alanlarında drama yaratır.
*   **Finansman Politikası:** Özellikle raid kompozisyonundaki kilit oyuncuların (tanklar, en iyi DPS'ler) pahalı consumable'lar veya enchant'larla guild bankasından finanse edilmesi kararı.
*   **Loot Hoarding (Ganimet Biriktirme):** Guild bankasında değerli eşyaların "doğru oyuncu yok" veya "şu an kimseye lazım değil" gerekçesiyle uzun süre bekletilmesi. Bu durum, oyuncular arasında memnuniyetsizlik yaratabilir.

## 4. Ekonomi ile Etkileşim

Guild bankası, simüle edilmiş sunucu ekonomisi ile sürekli etkileşim halindedir.

*   **Satın Alma/Satma:** Oyuncu, gerekli materyalleri simüle edilmiş pazardan gold karşılığı satın alabilir veya fazla materyalleri satarak gold elde edebilir.
*   **Piyasa Etkisi:** `Item Economy` dokümanında belirtildiği gibi, botlar veya dış etkenler nedeniyle piyasa fiyatlarındaki dalgalanmalar, guild bankasının alım/satım stratejilerini doğrudan etkiler.

## 5. Eksik Alanlar / Geliştirme Notları

*   **Banka Arayüzü (UI):** Mobil platformda bir guild bankası arayüzü nasıl tasarlanmalı? Kaynakların takibi, dağıtım ve katkıların gösterimi nasıl olmalı? (`<input gerekiyor>`)
*   **Banka Raporlama:** Oyuncunun, bankadaki kaynak hareketlerini (kim ne koydu, kim ne çekti) takip edebileceği raporlama mekaniği. (`<input gerekiyor>`)
*   **Kaynak Hedefleri:** Oyuncunun, guild bankası için belirli kaynak hedefleri belirlemesi (örn. "bir sonraki raid için X adet Flask of the Titans"). (`<input gerekiyor>`)
*   **Banka Güvenliği:** İçerden veya dışarıdan bankaya yönelik tehditler ve bunların yönetimi. (`<input gerekiyor>`)
