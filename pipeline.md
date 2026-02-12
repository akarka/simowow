# Departmanlar Arası İletişim ve Raporlama Pipeline'ı

## 1. Amaç ve Felsefe

Bu doküman, SimoWoW projesindeki departmanlar (ekipler) arası iletişimi ve iş akışını standart hale getirmek için tasarlanmış esnek bir rehberdir. Amacımız, katı bürokratik süreçler oluşturmak değil, aksine **otomatikleştirilebilir bir raporlama sistemi** kurarak denetim ve denge (check-and-balance) mekanizmasını hayata geçirmektir.

Bu pipeline, her ekibin aldığı kararları, taleplerini ve geri bildirimlerini şeffaf bir şekilde diğer ekiplere iletmesini ve bu etkileşimlerin proje hafızasına kaydedilmesini sağlar.

## 2. Temel İletişim Birimi: "Update" (Güncelleme)

Her türlü departmanlar arası etkileşim, standart bir formatta oluşturulan ve **"Update"** olarak adlandırılan birimler aracılığıyla gerçekleştirilecektir. Bu "Update"ler, ideal olarak `.md` veya `.yml` formatında, proje içindeki merkezi bir `updates/` klasörüne tarih ve konu ile isimlendirilerek eklenmelidir.

### "Update" Formatı

Her "Update" dosyası aşağıdaki temel bilgileri içermelidir:

```yaml
# Örnek: updates/2026-02-13-combat-system-feedback-request.md

# Hangi takımın güncelleme yayınladığı
issuing_team: "Game Mechanics and Core Systems Team"

# Güncellemenin hedeflediği takım(lar)
target_teams:
  - "User Interface and Experience (UI/UX) Team"
  - "Executive Management Team"

# Güncellemenin türü:
# Decision: Alınmış bir tasarım kararı.
# Request: Belirli bir takımdan talep (örn. asset, feedback, data).
# Feedback: Bir karara veya dokümana yönelik geri bildirim.
# Report: Haftalık/aylık ilerleme raporu.
update_type: "Request"

# Etkileşimin ilgili olduğu ana doküman(lar)
related_documents:
  - "GameDesign/CoreMechanics/RaidExecution/CombatSimulation.md"

# Durum:
# Pending_Feedback: Geri bildirim bekleniyor.
# Action_Required: Hedef takımdan bir eylem bekleniyor.
# Completed: Talep/Karar tamamlandı ve kapandı.
# Archived: Bilgilendirme amaçlı, aksiyon gerektirmeyen.
status: "Pending_Feedback"

# ---

# İnsan tarafından okunabilir özet ve detaylar (Markdown formatında)
summary: |
  ## Konu: "Komutan Yetenekleri" İçin UI/UX Geri Bildirim Talebi

  Combat Simulation dokümanında detaylandırılan "Komutan Yetenekleri" konsepti için UI/UX ekibinden ilk arayüz taslakları ve kullanıcı deneyimi üzerine geri bildirim talep ediyoruz.

  **Talebimiz:**
  1. Bu yeteneklerin mobil ekranda nasıl konumlandırılabileceği.
  2. Oyuncunun bu yetenekleri kullanırken nasıl bir akış izleyeceği.
  3. Savaş sırasında arayüzün karmaşıklaşmasını önleyecek tasarım önerileri.

  Executive Management ekibini de bilgilendirme amaçlı döngüye dahil ediyoruz.
```

## 3. İletişim Akış Örneği

1.  **Karar/Talep Başlatma:**
    *   `Game Mechanics` ekibi, `CombatSimulation.md` dokümanını günceller ve Komutan Yetenekleri'ni ekler.
    *   Hemen ardından, yukarıdaki örnekteki gibi bir "Update" dosyası oluşturur ve `updates/` klasörüne ekler. `status` "Pending_Feedback" olarak ayarlanır.

2.  **Otomatik Bildirim (Simülasyon):**
    *   Otomatik bir sistem (örneğin bir CI/CD script'i veya bot), bu yeni dosyayı algılar.
    *   Dosyanın `target_teams` alanında belirtilen `UI/UX Team` ve `Executive Management`'a bildirim gönderir (örn. Discord, Slack, E-posta).

3.  **Geri Bildirim/Aksiyon:**
    *   `UI/UX Team`, talebi inceler ve kendi içinde çalışmaya başlar.
    *   Çalışmalarını tamamladıklarında, orijinal "Update" dosyasına referans veren yeni bir "Update" dosyası oluştururlar:
        *   `update_type`: "Feedback"
        *   `issuing_team`: "User Interface and Experience (UI/UX) Team"
        *   `target_teams`: ["Game Mechanics and Core Systems Team"]
        *   `summary`: "Komutan Yetenekleri için hazırlanan ilk wireframe'ler ve geri bildirimlerimiz ektedir..."
        *   `related_documents`: [Orijinal "Update" dosyası, yeni wireframe dosyaları]

4.  **Döngünün Kapanışı:**
    *   `Game Mechanics` ekibi geri bildirimi alır ve uygular.
    *   Konuyla ilgili tüm aksiyonlar tamamlandığında, orijinal "Update" dosyasının `status` alanı `Completed` olarak güncellenir.

Bu sistem, her kararın ve talebin kaydını tutarak şeffaflık sağlar ve ekipler arası dengeyi korur.
