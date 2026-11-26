# MultiConnect sürümleri

MultiConnect'in yayınlanmış sürümleri (Windows, .NET 10). Kaynak kod bu depoda değildir.

- **Kurulum:** [Releases](https://github.com/oguzhan-keten/MultiConnect-releases/releases/latest) sayfasından
  `MultiConnect.exe`'yi indirip çalıştırın. 4.4.0 ve sonrası yeni sürümleri kendisi bulur ve
  **Ayarlar → Hakkında → Güncellemeler** veya üstteki şeritten tek tıkla günceller.
- **update.json / update.json.sig:** Programın okuduğu sürüm bilgisi ve imzası. Program yalnızca geliştiricinin
  anahtarıyla imzalanmış, SHA-256 parmak izi ve boyutu tutan exe'yi kurar.
- Her sürümün notlarında exe'nin SHA-256 değeri yazar; elle indirdiğiniz dosyayı
  `Get-FileHash MultiConnect.exe` ile karşılaştırabilirsiniz.