
issuing_team: "GameMechanicsAndCoreSystemsTeam"
target_teams:
  - "Executive Management Team"
update_type: "Feedback"
related_documents:
  - "updates/2026-02-13-raid-simulation-detail-request.md"
  - "GameDesign/CoreMechanics/RaidExecution/CombatSimulation.md"
status: "Archived"

---

summary: |
  ## Konu: Raid Simülasyonu Stratejik Yaklaşımına İlişkin Geri Bildirim

  Executive Management ekibine,

  `updates/2026-02-13-raid-simulation-detail-request.md` referanslı talebinize istinaden, raid simülasyonu mekaniği için önerdiğimiz stratejik yaklaşımı aşağıda sunuyoruz.

  ### Önerilen Yaklaşım: Abstrakt/Metin Bazlı Simülasyon

  Mevcut `CombatSimulation.md` dokümanında belirtilen "Auto-Battler" ve "%90 Hazırlık, %10 Müdahale" prensipleri doğrultusunda, **Abstrakt/Metin Bazlı Simülasyon** (örneğin *Football Manager* maç motoru gibi) yaklaşımının projemiz için en doğru tercih olduğuna inanıyoruz. Savaş, canlı bir log, kritik olay uyarıları ve oyuncunun stratejik anlarda kullandığı "Komutan Yetenekleri" üzerinden takip edilecektir.

  ### Stratejik Gerekçeler:

  1.  **Temel Tasarım Felsefesi ile Uyum:** Bu yaklaşım, oyuncunun anlık reflekslerinden ziyade hazırlık ve strateji kurma becerilerini ödüllendiren temel felsefemizle birebir örtüşmektedir. Oyuncunun dikkati, 40 karakteri küçük bir ekranda görsel olarak takip etmek yerine, savaşın gidişatını özetleyen verileri okuyup doğru zamanda "Komutan Yeteneği" kullanmaya odaklanacaktır.

  2.  **Mobil Performans ve Erişilebilirlik:** Yüksek detaylı, tam görsel bir simülasyon, özellikle 40 kişilik raid'lerde çok sayıda mobil cihaz için ciddi performans sorunları yaratacaktır. Abstrakt bir sistem, donanım gereksinimlerini minimumda tutarak daha geniş bir oyuncu kitlesine ulaşmamızı sağlar.

  3.  **Geliştirme Süresi ve Maliyeti:** Karakter ve boss'ların tüm yetenekleri için animasyonlar, görsel efektler ve karmaşık pozisyonlama mantığı gerektiren bir sistem, geliştirme takvimini aylar, hatta yıllarca uzatabilir. Abstrakt bir yaklaşım, MVP (Minimum Viable Product) hedeflerimizle uyumlu olarak çok daha hızlı geliştirilebilir ve iterasyona açıktır.

  4.  **Hedef Oyuncu Kitlesi:** SimoWoW, "hardcore" MMO oyuncularının stratejik ve yönetimsel yönünü seven "düşünen" oyuncuları hedefler. Bu kitle için anlamlı istatistikler, log'lar ve kritik karar anları, görsel bir şölenden daha tatmin edici ve tekrar oynanabilir bir deneyim sunacaktır.

  Bu nedenlerle, geliştirme sürecinde **Abstrakt/Metin Bazlı Simülasyon** modelini esas alarak ilerlemeyi planlıyoruz. Bu yaklaşım, projenin temel vizyonunu desteklerken, teknik ve zamansal riskleri en aza indirmektedir.
