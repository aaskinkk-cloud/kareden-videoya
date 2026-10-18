# Kareden Videoya

Telefondaki fotoğraf ve videolardan YouTube videosu hazırlayan, tarayıcıda çalışan uygulama (PWA). Dosyalar telefondan dışarı gönderilmez; video cihazda oluşturulur. Tek dosya: `index.html`; çevrimdışı önbellek `sw.js`.

**Adres:** https://aaskinkk-cloud.github.io/kareden-videoya/  
**Güncel sürüm:** 8.0 · 18.10.2026

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
- **8.0** – Hızlı çözücüye **WebGL aktarma yolu** eklendi (karenin GPU dokusu doğrudan kullanılır; HDR/10 bit karelerde 2B tuval siyah verirken çalışabilir). Sıra: çiz → webgl → bitmap → kopya; çalışan yol hatırlanır. Ön hazırlık artık en çok bir kez (0,5x) tekrar ediyor ve yalnız %3'ten fazla kayıpta; 7.9'daki 0,25x'e kadar tekrarlar süreyi katlıyordu.
- **7.9** – **Ön hazırlık:** hızlı çözücünün okuyamadığı videolar (ör. Samsung HDR / 10 bit HEVC `hvc1.2.…` → siyah kare) kayıttan önce bir kez gerçek hızda oynatılıp 8 bit H.264 ara dosyaya çevrilir; asıl kayıt bunu hızlı çözücüyle okur. Kare kaçarsa o klip daha yavaş tekrar çevrilir. İlerleme satırında "ön hazırlık 1/3 · %…" ve "⚡ hızlı çözme (ön hazırlıklı)" görünür. Ara dosyalar yalnız bellekte tutulur, kayıttan sonra silinir. Kalıcı en hızlı yol: kamerada HDR10+ videoyu kapatmak.
- **7.8** – Hızlı çözücü siyah kare verince yavaş akış moduna geçmeden önce kareyi aktarmanın iki yolu daha deneniyor (ImageBitmap, piksel kopyası). Çalışan yol telefonda hatırlanır, sonraki kayıtlarda doğrudan kullanılır. İlerleme satırında kullanılan yol yazar, örn. "⚡ hızlı çözme (kopya)"; akış modunda neden ve kod bilgisi gösterilir.
- **7.7** – Video oluşturulurken hangi çözme yolunun kullanıldığı canlı görünür: ilerleme satırında "⚡ hızlı çözme" ya da "🐢 akış modu — neden"; ilk video klipte kısa bildirim.
- **7.6** – Akış modu tam kayıpsız: aradaki tek kare kaybı da yakalanıyor (testte kare tekrarı 0). Kayıp olmayınca hız kademeli olarak geri artıyor, kayıp görülen hıza bir daha çıkılmıyor. Hızlı çözücü kod adı farkı (hvc1/hev1, avc1/avc3) yüzünden açılamıyorsa diğer adla deneniyor. Bilgi satırında "yavaş yola düşen: dosya: neden" gösteriliyor.
- **7.5** – Kesik video düzeltmesi. Akış modunda (hızlı çözücü kullanılamayınca) telefon oluşturma sürerken oynayan videonun karelerini atlıyordu; testte karelerin yarısı tekrar ediyordu. Artık kaçan kare fark edilince video geri sarılıp daha yavaş oynatılarak yeniden yakalanıyor. 7.4'teki yavaşlatma kaldırıldı (kendisi kare tekrarı yapıyordu); görüntü yetmeyen kliplerde bekleme geçişin silik yarılarına bölünüyor. Bitişte bilgi satırında "video kare tekrarı: X/Y" ve kodlayıcı kare düşürürse uyarı gösterilir.
- **7.4** – Videolar arası geçiş akıcı: gelen video geçiş boyunca artık donmuyor, oynayarak giriyor (önce kırpılan başın öncesi, yoksa sonun sonrası kullanılır; ikisi de yoksa klip fark edilmeyecek kadar yavaşlatılır). Klibin kendi sesi ve altyazısı görüntüyle aynı yerden başlar. Önizlemede sıradaki video geçişten önce hazırlanır. Kayıtta anahtar kare aralığı 0,5 sn → 2 sn (kalite nabzı/titreme azalır). Akış modunda 1,5 kat hız yerine normal hız (kare atlama yok).
- **7.3** – Telefonda **stüdyo düzeni**: üstte sabit önizleme, ortada yalnız seçili aracın paneli (kendi içinde kayar), altta araç çubuğu. Aynı araca tekrar dokununca ya da "▾ Kapat" ile panel kapanır, önizleme ekranı doldurur. Katmanlar ve klip şeridi Klipler panelinde. Yazı alanına dokununca (klavye) önizleme küçülür, çubuklar gizlenir, yazılan alan görünür kalır. Küçült/Büyüt panel açıkken önizlemenin payını belirler. Yatay telefonda önizleme solda, panel sağda. Masaüstü düzeni değişmedi. Önizleme tam ekran düğmesindeki hata (eksik öğe yüzünden tam ekran isteğinin yarıda kesilmesi) düzeltildi.
- **7.2** – "Sesim" (kendi sesine yakın okuma) denemesi.
- **7.1** – Basit mod; tekrar eden/kullanılmayan bölümlerin ayıklanması; altyazı öncesi akıllı metin düzeltme.

## Güncelleme
Yeni sürümün tüm dosyalarını depo köküne yükle; uygulamayı bir kez kapatıp aç (önbellek `sw.js` sürümüyle yenilenir).
