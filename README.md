# Kareden Videoya

Telefondaki fotoğraf ve videolardan YouTube videosu hazırlayan, tarayıcıda çalışan uygulama (PWA). Dosyalar telefondan dışarı gönderilmez; video cihazda oluşturulur. Tek dosya: `index.html`; çevrimdışı önbellek `sw.js`.

**Adres:** https://aaskinkk-cloud.github.io/kareden-videoya/  
**Güncel sürüm:** 7.5 · 18.10.2026

## Bölümler
- **Klipler** – klip sırası, katmanlar (zaman çizelgesi: böl, çoğalt, uzat/kısalt), kadraj, hareket (Ken Burns), takip eden yazı, toplu ayarlar.
- **Şablon** – giriş başlığı, açılış efektleri, bantlar, abone hatırlatıcı, kapanış kartı, hazır paketler.
- **Görünüm · efekt** – arka plan, renk, geçişler.
- **Müzik** – telifsiz hazır müzik, kendi şarkıların, otomatik sığdırma, ses kısma (ducking).
- **Ses** – seslendirme kaydı, okuma ekranı (prompter), Türkçe ses.
- **Altyazı** – otomatik altyazı, akıllı metin düzeltme, görünüm.
- **Logo · Kapak · Yayın · Aktar** – logo, kapak adayları, başlık/açıklama/etiket, MP4 dışa aktarma ve hazır ayarlar.
- **Basit mod** – temel bölümler görünür; gizlenen ayarlar aynen çalışır.

## Sürüm notları
- **7.5** – Kesik video düzeltmesi. Akış modunda (hızlı çözücü kullanılamayınca) telefon oluşturma sürerken oynayan videonun karelerini atlıyordu; testte karelerin yarısı tekrar ediyordu. Artık kaçan kare fark edilince video geri sarılıp daha yavaş oynatılarak yeniden yakalanıyor. 7.4'teki yavaşlatma kaldırıldı (kendisi kare tekrarı yapıyordu); görüntü yetmeyen kliplerde bekleme geçişin silik yarılarına bölünüyor. Bitişte bilgi satırında "video kare tekrarı: X/Y" ve kodlayıcı kare düşürürse uyarı gösterilir.
- **7.4** – Videolar arası geçiş akıcı: gelen video geçiş boyunca artık donmuyor, oynayarak giriyor (önce kırpılan başın öncesi, yoksa sonun sonrası kullanılır; ikisi de yoksa klip fark edilmeyecek kadar yavaşlatılır). Klibin kendi sesi ve altyazısı görüntüyle aynı yerden başlar. Önizlemede sıradaki video geçişten önce hazırlanır. Kayıtta anahtar kare aralığı 0,5 sn → 2 sn (kalite nabzı/titreme azalır). Akış modunda 1,5 kat hız yerine normal hız (kare atlama yok).
- **7.3** – Telefonda **stüdyo düzeni**: üstte sabit önizleme, ortada yalnız seçili aracın paneli (kendi içinde kayar), altta araç çubuğu. Aynı araca tekrar dokununca ya da "▾ Kapat" ile panel kapanır, önizleme ekranı doldurur. Katmanlar ve klip şeridi Klipler panelinde. Yazı alanına dokununca (klavye) önizleme küçülür, çubuklar gizlenir, yazılan alan görünür kalır. Küçült/Büyüt panel açıkken önizlemenin payını belirler. Yatay telefonda önizleme solda, panel sağda. Masaüstü düzeni değişmedi. Önizleme tam ekran düğmesindeki hata (eksik öğe yüzünden tam ekran isteğinin yarıda kesilmesi) düzeltildi.
- **7.2** – "Sesim" (kendi sesine yakın okuma) denemesi.
- **7.1** – Basit mod; tekrar eden/kullanılmayan bölümlerin ayıklanması; altyazı öncesi akıllı metin düzeltme.

## Güncelleme
Yeni sürümün tüm dosyalarını depo köküne yükle; uygulamayı bir kez kapatıp aç (önbellek `sw.js` sürümüyle yenilenir).
