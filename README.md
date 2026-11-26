# MultiConnect

VPN (OpenVPN, WireGuard), SSH, SFTP ve Uzak Masaüstü (RDP) bağlantılarını tek pencereden yöneten Windows uygulaması.
Birden fazla VPN aynı anda açılabilir; her sunucu bir VPN'e bağlanabilir ve sunucuya bağlanırken önce o VPN kurulur.

**[En son sürümü indir](https://github.com/oguzhan-keten/MultiConnect-releases/releases/latest)**

## Özellikler

### VPN
- **OpenVPN ve WireGuard programın içinde:** ayrıca kurmanız gerekmez. OpenVPN Connect veya WireGuard uygulaması
  kuruluysa çakışmaz.
- **Birden fazla VPN aynı anda**, her biri kendi sanal adaptöründe. Tümünü bağla / Tümünü kes; seçilen VPN'ler program
  açılınca kendiliğinden bağlanır.
- `.ovpn` ve WireGuard `.conf` dosyalarını pencereye sürükleyip bırakarak ekleme; WireGuard tünelini programda oluşturma
  (anahtar üretimi dahil).
- **Trafik grafiği:** son 60 saniyenin indirme/yükleme hızı ve toplam aktarılan veri.
- Bölünmüş tünel, kullanıcı adı/parola ve tek kullanımlık kod (OTP) soruları, bağlantı koparsa, ağ değişince veya
  bilgisayar uyanınca otomatik yeniden bağlanma.
- İki VPN aynı tünel ağını kullanıyorsa uyarı ve **Bu VPN'e öncelik ver** seçeneği.

### SSH, SFTP ve dosya düzenleme
- **SSH sekmesinde solda dosyalar (SFTP), sağda terminal.** Dosya paneli terminalin girişini kullanır, parola ikinci kez
  sorulmaz.
- Tam özellikli terminal: 256 renk, fare, Unicode, kopyala/yapıştır, yazı boyutu. Çıktıda adresler, IP'ler ve
  hata/uyarı/başarı kelimeleri renklendirilir.
- Parola veya SSH anahtarıyla giriş, iki adımlı doğrulama (kod sorusu), sunucu kimliği (parmak izi) onayı ve
  değişirse uyarı.
- **SFTP:** yükleme, indirme, Gezgin'den sürükle-bırak (klasörler içleriyle), yeni klasör, yeniden adlandırma, silme;
  dosya türüne göre renkli simgeler, ilerleme çubuğu ve iptal.
- **Program içi editör:** sunucudaki bir dosyaya çift tıklayınca açılır, Ctrl+S doğrudan sunucuya kaydeder. Dosyanın
  izinleri, satır sonları ve kodlaması korunur; dosya bu arada sunucuda değiştiyse kaydetmeden önce sorulur. Satır
  numaraları ve arama (Ctrl+F) vardır.

### Uzak Masaüstü (RDP)
- Windows'un Uzak Masaüstü bağlantısı sekmenin içinde açılır; sekme boyutu değişince uzak masaüstü de yeniden
  boyutlanır. Bağlantı kesilince nedeni yazılır ve **Yeniden bağlan** düğmesi çıkar.

### Düzen
- Sekmeli çalışma: her oturum ayrı sekmede, durum renkli noktayla gösterilir.
- **Gruplar:** sürükleyerek sıralama, bağlantıları gruba sürükleme, her gruba simge ve renk.
- **Arama (Ctrl+K):** bağlantıları ad, sunucu, kullanıcı veya gruba göre süzer; i/İ/ı/I harflerini aynı sayar.
- Genel bakış sayfası, son kullanılan bağlantılar, koyu tema.
- Saatin yanındaki simgeden VPN'leri açıp kapatma; pencere kapatılınca bağlantılar arka planda açık kalır.

### Güvenlik
- **SSH anahtar kasası:** Ed25519 veya RSA anahtarı oluşturma ya da içe aktarma (OpenSSH, PEM, PuTTY `.ppk`).
- Kayıtlı parolalar ve anahtarlar Windows'un kullanıcıya özel şifrelemesiyle (DPAPI) saklanır.
- **Kayıtlı parolalar** penceresi yalnızca Windows hesap parolanızla açılır; her açılış kayda geçer.
- **Parola üretici:** 8-64 karakter, harf/rakam/sembol seçimi, karışabilecek karakterleri çıkarma, güç göstergesi.
- Kopyalanan parolalar Windows pano geçmişine ve bulut panosuna girmez, 30 saniye sonra panodan silinir.
- **Yedekleme:** tüm bağlantılar, VPN'ler, anahtarlar ve parolalar parolalı tek bir dosyaya alınır (Argon2id +
  AES-256-GCM); başka bir bilgisayarda geri yüklenebilir.

## Gereksinimler

- Windows 10 veya 11 (64 bit)
- [.NET 10 Desktop Runtime](https://dotnet.microsoft.com/download/dotnet/10.0)
- Microsoft Edge WebView2 çalışma zamanı (Windows 11'de hazır gelir; SSH terminali için)
- Program açılırken yönetici izni ister, çünkü VPN'ler sanal ağ adaptörü ve yönlendirme ayarlarını değiştirir.
  İsteğe bağlı olarak Windows açılışında izin sorulmadan başlayabilir.

## Kurulum

[Sürümler](https://github.com/oguzhan-keten/MultiConnect-releases/releases/latest) sayfasından `MultiConnect.exe`'yi
indirip istediğiniz bir klasörden çalıştırın. Kurulum sihirbazı yoktur; ayarlar Windows kullanıcınızın klasöründe
saklanır.

## Güncellemeler

- Program yeni sürümleri kendisi bulur: açılışta ve günde iki kez denetler, yeni sürüm varsa üstte bir şerit çıkar.
  **Güncelle** düğmesi yeni sürümü indirir, açık bağlantıları düzgünce kapatır ve programı yeni sürümle yeniden başlatır.
  Denetim **Ayarlar → Hakkında**'dan kapatılabilir veya elle yapılabilir.
- **Her sürüm imzalıdır.** Program yalnızca geliştiricinin anahtarıyla imzalanmış sürüm bilgisini (`update.json`,
  `update.json.sig`) kabul eder ve yalnızca bu bilgideki SHA-256 parmak izi ve boyutu tutan exe'yi kurar. İmzası
  tutmayan veya değiştirilmiş bir dosya kurulmaz.
- Elle indirdiğiniz dosyayı doğrulamak için sürüm notlarındaki SHA-256 değerini şununla karşılaştırabilirsiniz:

  ```powershell
  Get-FileHash .\MultiConnect.exe
  ```

## Kullanılan açık kaynak bileşenler

OpenVPN (GPLv2), wireguard-nt, SSH.NET, xterm.js, AvalonEdit (MIT). Lisansları programda **Ayarlar → Hakkında**
bölümünde yer alır.
