# Kareden Videoya

## 8.11 (23.10.2026) — Tam ekran düğmesi geri
- Kurulu uygulamada gizlenen tam ekran düğmesi yeniden görünür ve çalışır. Düğmeye basınca Chrome kendi "Tam ekrandan çıkmak için…" uyarısını bir kez gösterir (tarayıcı kuralı). Dokununca kendiliğinden tam ekran isteği gönderilmez.

## 8.10 (22.10.2026) — Kurulu uygulamada tam ekran düğmesi
- Ana ekrandan yüklenen uygulama baştan tam ekran açıldığı için tam ekran düğmesi gizlendi ve basılsa da tam ekran isteği gönderilmez. Önceden düğmeye basınca uyarı çıkıyor, sayfa yeniden diziliyor, yazılar kayboluyor / sayfa değişiyordu.

## 8.9 (22.10.2026) — Tam ekran uyarısı kesin çözüm
- Sayfanın kendiliğinden tam ekrana geçme istekleri (ilk dokunuşta, açılışta, dosya seçiciden dönünce) **tamamen kaldırıldı**; Chrome'un "Tam ekrandan çıkmak için…" uyarısı ekrana dokununca artık çıkmaz. Tam ekran isteği yalnız tam ekran düğmesine basınca gönderilir. Ana ekrandan yüklenen uygulama zaten tam ekran açılır.

## 8.8 (22.10.2026) — Açılışta tam ekran
- Ana ekrandan açılınca uygulama **doğrudan tam ekran** gelir (`manifest.webmanifest`: `"display": "fullscreen"`). Tarayıcı içinden tam ekran isteği gönderilmediği için Chrome'un "Tam ekrandan çıkmak için…" uyarısı da çıkmaz.
- Daha önce yüklenmiş simge eski ayarla açılabilir: simgeyi kaldırıp Chrome › ⋮ › **Uygulamayı yükle** ile yeniden yükle.

## 8.7 (22.10.2026) — Sessiz ekran
- **Tam ekran uyarısı:** Ana ekrandan açılan (kurulu, tam ekran) uygulamada içeriden tam ekran isteği gönderilmez → Chrome'un "Tam ekrandan çıkmak için yukarıdan sürükleyip…" uyarısı çıkmaz. Chrome sekmesinde tam ekrana her girişte bu uyarıyı tarayıcı kendisi gösterir; sayfa kapatamaz.
- **Kelimeye dokununca Google paneli:** Chrome'un "Dokunarak ara" paneli açılmasın diye sayfa (ve içindeki çerçeveler) dokunuşu kendisi karşılar. Uzun basıp seçme çalışır.
- Blok `/* SESSİZ EKRAN */` adıyla `index.html`'in başındadır; tüm uygulamalarda aynıdır.

Telefondaki fotoğraf ve videolardan YouTube videosu hazırlayan, tarayıcıda çalışan uygulama (PWA). Dosyalar telefondan dışarı gönderilmez; video cihazda oluşturulur. Tek dosya: `index.html`; çevrimdışı önbellek `sw.js`.

**Adres:** https://aaskinkk-cloud.github.io/kareden-videoya/  
**Güncel sürüm:** 8.6 · 18.10.2026

## Bölümler
- **Klipler** – klip sırası, katmanlar (zaman çizelgesi: böl, çoğalt, uzat/kısalt), kadraj, hareket (Ken Burns), takip eden yazı, toplu ayarlar.
- **Şablon** – giriş başlığı, açılış efektleri, bantlar, abone hatırlatıcı, kapanış kartı, hazır paketler.
- **Görünüm · efekt** – arka plan, renk, geçişler.
- **Müzik** – telifsiz hazır müzik, kendi şarkıların, otomatik sığdırma, ses kısma (ducking).
- **Ses** – seslendirme kaydı, okuma ekranı (prompter), Türkçe ses.
- **Altyazı** – otomatik altyazı, akıllı metin düzeltme, görünüm.
- **Logo · Kapak · Yayın · Aktar** – logo, kapak adayları, başlık/açıklama/etiket, MP4 dışa aktarma ve hazır ayarlar.
- **● Kayıt düğmesi** (oynatıcının yanında) – tek dokunuşla video oluşturur, bitince MP4 kaydını sorar.
- **Basit mod** – temel bölümler görünür; gizlenen ayarlar aynen çalışır.

## Sürüm notları
- **8.6** – **Ön hazırlık yeniden yazıldı.** Ölçüm: kareyi tuvale çizmek kare başına ~20 ms (asıl yavaşlık), kareyi videodan doğrudan almak ~0,1 ms. Yeni **doğrudan yol**: kareler doğrudan kodlayıcıya gider, video ekran yenileme hızının izin verdiği hızda oynar (120 Hz ekran + 30 fps → ~3,4x). Başta 8 karelik deneme yapılır; çıkan görüntü ekrandakiyle yön ve renk olarak karşılaştırılır (dikey/döndürülmüş videolar otomatik düzeltilir). Uyuşmazsa **güvenli yol** (her karede durup çizer, kayıpsız, ~1x). Deneme sonucu telefonda hatırlanır. İlerleme satırında hız (ör. "· 3,4x") ya da "· güvenli yol" yazar. 8.4–8.5'teki sürekli geri sarma sorunu bu yolla ortadan kalktı.
- **8.5** – Ön hazırlık sürerken ekran açık tutulur (ekran kilidi); ekran kapanır ya da uygulamadan çıkılırsa Chrome videoyu durdurduğu için hazırlık duruyordu — artık geri dönünce kaldığı yerden sürer. Takılma bekçisi: ekran açıkken 8 sn ilerleme yoksa dürtülür, yine olmazsa bırakılır. Yarım kalan hazırlık kullanılmaz (eksik kare çıkmasın). İlk karelerdeki kayıp da yakalanıyor.
- **8.4** – Ön hazırlık hızlandı: video 2x'ten başlar, kare kaybı yoksa 4x'e kadar çıkar (120 Hz ekranda saniyede 120 kare yakalanabilir). Kare kaçarsa klip baştan alınmaz; son yakalanan kareye geri sarılıp hız düşürülerek devam edilir (kayıpsız). Telefonda bulunan en iyi hız hatırlanır. 8.3'e kadar en çok 1x idi ve kayıpta klip 0,5x ile baştan alınıyordu (2 dk video 2–6 dk). İlerleme satırında anlık hız (ör. "· 3,2x") görünür.
- **8.3** – Önizleme altı araç çubuğu yenilendi (telefon): tek parça ince çubuk — Ekle · Dikey · Takip yazı · Küçült · Büyüt · Tam ekran · Diğer. Basit mod, tema, yeni video ve video bilgisi "Diğer" menüsünde. Kayıt göstergesi videonun üstünden kalktı; kayıt sırasında araç çubuğunun yerinde ince bir satır (yüzde · durum · Duraklat · İptal), bitince aynı yerde "Video hazır — MP4 olarak kaydedilsin mi?" · ⬇ MP4 kaydet · Sonra. Video artık kayıt boyunca tamamen görünür.
- **8.2** – Ön hazırlık yalnız klipte kullanılan kısmı (geçiş payıyla) çeviriyor; 8.1 kaynak videonun tamamını çeviriyordu (60 sn videodan 5 sn kullanılsa 60 sn bekleniyordu). Aynı dosyadan kesilen klipler birleşik aralığı paylaşır; kırpma aralık dışına çıkarsa yeniden hazırlanır. 10 dk sınırı kalktı.
- **8.1** – **Arka plan hazırlığı:** ön hazırlık video eklenince, sen düzenlerken yapılır (klip şeridinde "⚡ Videolar hızlı kayıt için hazırlanıyor"); kayıtta beklenmez, tekrar kayıtta yeniden yapılmaz, bölünen klipler aynı hazırlığı paylaşır (10 dk'dan uzun kaynaklar kayıt anında hazırlanır). **Kayıt düğmesi:** oynatıcının yanında kırmızı ● — her sekmede görünür, dokununca kayıt hemen başlar; panel kapanır, önizleme ekranı doldurur. Bitince önizlemenin ortasında "MP4 olarak kaydedilsin mi?" — ⬇ MP4 kaydet / Sonra. Kayıt göstergesi telefonda sığacak şekilde küçültüldü. Durdur düğmesi artık gizlenmiyor.
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
