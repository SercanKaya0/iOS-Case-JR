# HR App

Modern İK ekipleri için geliştirilmiş, aday değerlendirme ve işe alım süreçlerini kolaylaştırmayı amaçlayan bir mobil uygulama.

## 👨‍💻 Geliştirici
**Rol:** Jr. iOS Developer

---

## 📘 İçindekiler

- [📖 Giriş](#giriş)
- [⚙️ Gereksinimler](#gereksinimler)
- [✨ Nice to Have Özellikler](#nice-to-have-ozellikler)
- [🚀 Özellikler](#özellikler)
  - [🎬 Launch Screen](#launch-screen)
  - [💧 Splash Screen](#splash-screen)
  - [🛳️ Onboard](#onboard)
  - [🔐 Login](#login)
  - [🔢 OTP](#otp)
  - [🏠 Home](#home)
  - [⚙️ Settings](#settings)

---

## 📖 Giriş

**HR App**, birden fazla markaya kolayca uyarlanabilecek esnek bir yapıda tasarlanmıştır. Amaç; yalnızca marka kimliğine uygun tasarımlar giydirilerek, minimum geliştirme ile farklı pazarlarda kullanılabilecek bir İnsan Kaynakları uygulaması sunmaktır.

---

## ⚙️ Gereksinimler

- **Mimari:** MVVM-R
- **Branch Yapısı:**
  - `feature/hrapp-000-feature-name`
  - `bug/hrapp-000-fix-description`
  - **Commit Örneği:** `HRAPP-101 Login ekranı tasarlandı.`
- **Geliştirme:** Mevcut proje üzerinden devam edilecektir.
- **Swift Package Manager (SPM)**
- **Minimum iOS Sürümü:** iOS 15+
- **Dil Desteği:** Türkçe & İngilizce (JSON tabanlı lokalizasyon)
- **Karanlık Mod (Dark Mode)** desteği
- **Layout:** Auto Layout ile responsive tasarım
- **Geliştirme Yöntemi:** Programmatic veya XIB
- **Servis Katmanı:** DataProvider isim bir spm package içeriside bulunmalıdır.

---

## ✨ Nice to Have Özellikler

- Lottie animasyonları
- Firebase Remote Config hazırlığı
- Dev / Preprod / Prod şema yapısı
- Firebase Cloud Messaging desteği
- Firebase Analytics event'leri
- Firebase Crashlytic Entegrasyonu
- SwiftLint Kurulumu
- Deeplink Entegrasyonu - (Scheme: loodosCase)

---

## 🚀 Özellikler

### 🎬 Launch Screen
- [Figma Linki](https://www.figma.com/design/MbORukxK22gzWuvYmP41Vv/Supa-Resume---Light---Dark--FREE-Resume-Cover-Letter---Community-?node-id=33-5366)
- **Task Kodu:** `HRAPP-000`
- Auto Layout uyumlu
- Dark Mode desteği
- Uygulama bu ekranla başlamalı
---

### 💧 Splash Screen
- [Figma Linki](https://www.figma.com/design/MbORukxK22gzWuvYmP41Vv/Supa-Resume---Light---Dark--FREE-Resume-Cover-Letter---Community-?node-id=33-5366)
- **CURL Örneği:**
  ```bash
  curl -X POST https://api.dev.hrapp.com/login \
    -H "Content-Type: application/json" \
    -d '{
      "username": "test.case",
      "password": "123123"
    }'
  ```
- **Task Kodu:** `HRAPP-001`
- Auto Layout ile tüm cihaz boyutlarına uyumlu tasarım
- Dark Mode desteği
- Launch sonrası gösterilir
- Genel Akış;
    - Uygulama Launch Screen sonrasında SplashViewController üzerinden başlar.
    - Yukarıdaki CURL örneği ile belirtilen API'ye istek göndererek ilgili JSON verisini alabilirsiniz.
    - Bu JSON dosyasındaki key–value verileri, lokalizasyon amaçlı kullanılacaktır.
    - Çekilen JSON dosyası cihazın yerel deposunda (örneğin UserDefaults veya dosya sistemi) saklanmalıdır.
    - Yönlendirme Kuralları:
        - Eğer kullanıcı onboard ekranlarını daha önce görmemişse, uygulama Onboard ekranına yönlendirilmelidir.
        - Kullanıcı giriş yaptıysa, doğrudan Anasayfa (Home) ekranına yönlendirilmelidir.
        - Kullanıcı giriş yapmadıysa, Login ekranına yönlendirilmelidir.
        - Başlangıç Noktası:
        - Geliştirmeye SplashViewController dosyasından başlanmalıdır.
        - Uygulama açıldığında kullanıcının dil dosyasını çekebilmesi için dikkat edilmesi gerekenler;
            - Uygulama yüklendiğinde eğer cihaz dili türkçe değilse en-US, eğer türkçe ise tr-TR olarak localizable dosyası çekilmelidir.
---

### 🛳️ Onboard
- [Figma Linki](https://www.figma.com/design/MbORukxK22gzWuvYmP41Vv/Supa-Resume---Light---Dark--FREE-Resume-Cover-Letter---Community-?node-id=33-5366)
- **CURL Örneği:**
  ```bash
  curl -X POST https://api.dev.hrapp.com/login \
    -H "Content-Type: application/json" \
    -d '{
      "username": "test.case",
      "password": "123123"
    }'
  ```
- **Task Kodu:** `HRAPP-002`
- Auto Layout ile tüm cihaz boyutlarına uyumlu tasarım
- Dark Mode desteği
- Genel Akış;
    - Yukarıdaki CURL örneği ile belirtilen API'den alınan JSON verisi Splash ekranında çekilip Onboard ekranına aktarılmalıdır.
    - Resimler yüklenirken iOS native loading mekanizması kullanılmalıdır.
    - Görseller yüklenirken hata alınırsa, tasarımdaki placeholder görsel gösterilmelidir.
    - Resimler cache'lenmelidir; böylece kullanıcı Onboard ekranını tekrar gördüğünde yeniden indirilmelerine gerek kalmaz.
    - Kullanıcı Onboard ekranında geri butonunu kullanarak çıkış yapamamalıdır.
    - Kullanıcı "Devam Et" butonuna bastığında, bir sonraki Onboard sayfası gösterilmelidir.
    - Kullanıcı "Atla" (Skip) butonuna basarsa, doğrudan Login ekranına yönlendirilmelidir.
    - Kullanıcı son Onboard ekranındaysa ve "Devam Et" butonuna basarsa, Login ekranına yönlendirme yapılmalıdır.
- **Nice to Have:**
  - Firebase Event Yollama (onboard_skipped, onboard_continue)

---

### 🔐 Login
- [Figma Linki](https://www.figma.com/design/MbORukxK22gzWuvYmP41Vv/Supa-Resume---Light---Dark--FREE-Resume-Cover-Letter---Community-?node-id=33-5366)
- **Task Kodu:** `HRAPP-003`
- **Test Kullanıcı Bilgileri:**  
  `username: test.case`, `password: 123123`
- **CURL Örneği:**
  ```bash
  curl -X POST https://api.dev.hrapp.com/login \
    -H "Content-Type: application/json" \
    -d '{
      "username": "test.case",
      "password": "123123"
    }'
  ```
- Tüm cihaz boyutlarına uyumlu Auto Layout tasarımı
- Dark Mode desteği

- **Genel Akış:**
  - Kullanıcı adı alanı minimum 3, maksimum 50 karakter olmalıdır.
  - Şifre alanı minimum 6, maksimum 20 karakter olmalıdır.
  - Tüm giriş alanlarında emoji kullanımı engellenmelidir.
  - Herhangi bir giriş alanında doğrulama hatası mevcutsa, "Giriş Yap" butonu pasif durumda olmalıdır.
  - Hatalı alanların altında kullanıcıya durumu açıklayan bilgilendirici metin gösterilmelidir.  
    Örnek: `Kullanıcı adı en az 3 karakter olmalıdır.`
  - Giriş başarılı olduğunda kullanıcı OTP ekranına yönlendirilmelidir.
  - Login isteğinden dönen response verileri OTP ekranına aktarılmalıdır.
    - Bu veri aktarımı ve yönlendirme işlemi için örnek bir kod parçası sağlanacaktır.
    - pushOTP(expiresIn: Int?) kullanılarak değeri taşıyabilirsiniz.

- **Nice to Have:**
  - Firebase üzerinden login başarılı/başarısız event'lerinin gönderilmesi
  - Giriş alanlarının yeniden kullanılabilir (reusable) component yapısında tasarlanması

---

### 🔢 OTP
- **Task Kodu:** `HRAPP-004`
- **Test Kullanıcı Bilgileri:**  
  `otp: 12345`
- Tüm cihaz boyutlarına uyumlu Auto Layout tasarımı
- Dark Mode desteği

- **Genel Akış:**
  - Kullanıcı, klavyedeki otomatik öneri (AutoFill) özelliğiyle tek kullanımlık kodu kolayca girebilmelidir.
  - Tasarıma uygun bir progress bar bulunmalı ve login yanıtında dönen `expiresIn` süresi kadar geri sayım yapmalıdır.
  - OTP alanına `"12345"` yazılıp "Giriş Yap" butonuna basıldığında işlem başarılı kabul edilir.
  - "Giriş Yap" butonu yalnızca tüm OTP input alanları doluysa aktif hale gelmelidir.
  - Kullanıcı, geri butonuyla Login ekranına dönebilmelidir.
  - Uygulama arka plana alındığında geri sayım durmamalı; örneğin, 30. saniyede arka plana alınıp 20 saniye sonra geri dönüldüğünde, sayaç 10. saniyeden devam etmelidir.
  - Giriş işlemi başarılı olduğunda kullanıcı Home ekranına yönlendirilmelidir.

 - **Nice to Have:**
  - Firebase üzerinden otp_success ve otp_error event’lerinin gönderilmesi
  - OTP input alanlarının yeniden kullanılabilir (reusable) bir component olarak tasarlanması

---

### 🏠 Home
- [Figma Linki](https://www.figma.com/design/MbORukxK22gzWuvYmP41Vv/Supa-Resume---Light---Dark--FREE-Resume-Cover-Letter---Community-?node-id=33-5366)
- **Task Kodu:** `HRAPP-005`
- **Banner CURL Örneği:**
  ```bash
  curl -X POST https://api.dev.hrapp.com/login \
    -H "Content-Type: application/json" \
    -d '{
      "username": "test.case",
      "password": "123123"
    }'
  ```
  - **Otopark CURL Örneği:**
  ```bash
  curl -X POST https://api.dev.hrapp.com/login \
    -H "Content-Type: application/json" \
    -d '{
      "username": "test.case",
      "password": "123123"
    }'
  ```
- Tüm cihaz boyutlarına uyumlu Auto Layout tasarımı
- Dark Mode desteği
- CollectionView ile geliştirme yapılacaktır.
   - Banner 10 saniyede bir otomatik olarak scroll etmelidir.
   - Eğer son banner gösteriliyorsa, 10 saniye sonra tekrar en başa dönmelidir (sonsuz döngü).
- CollectionView Cell kullanılmamalıdır. Tarafınıza verilen özel sınıf kullanılarak entegrasyon yapılmalıdır.  
  Kullanılacak sınıf: `LCGenericCollectionViewCell`

  ```swift
  let cell: LCGenericCollectionViewCell<ExampleView> = collectionView.dequeueReusableCell(for: indexPath)
    let view = ExampleView()
    view.set(viewModel: cellModel)
    cell.cellView = cellView
  return cell
  ```
 - Kullanıcı Banner’a tıkladığında detay sayfasına yönlendirilmelidir.
 - Maslak Otopark bileşeni bir servis isteğiyle durumunu göstermelidir ("BOŞ" veya "DOLU").
   - Servis yanıtında dönen süre (örneğin 60 saniye) kadar bekleyip yeniden istek atılmalıdır.
   - Eğer servisten gelen süre “0” ise, tekrar istek atılmamalıdır (timer durdurulmalıdır).
 - Kullanıcı bu ekrandan geri dönüş yapamamalıdır.
 - Ekran, TabBar’da yer almalıdır. (MainTabBarViewController)

- **Nice to Have:**
  - Firebase click_banner, refresh_carpark, stop_timer, click_home_tab eventleri.


---

### ⚙️ Settings
- **Task Kodu:** `HRAPP-006`
- [Figma Linki](https://www.figma.com/design/MbORukxK22gzWuvYmP41Vv/Supa-Resume---Light---Dark--FREE-Resume-Cover-Letter---Community-?node-id=33-5366)
- TabBar’da erişilebilir bir sayfa olarak gösterilmelidir.
- Kullanıcı, "Dil Değiştir" butonuna tıkladığında bir sheet açılmalı ve buradan dil seçimi yapabilmelidir.
- Seçim yapıldığında bir loading göstergesi çıkarılmalı ve uygulama dili anlık olarak değişmelidir.
  - Bu değişiklik, kullanıcı Settings ekranından çıkmadan gerçekleşmelidir.
- Eğer cihaz dili Türkçe değilse, varsayılan dil İngilizce olarak ayarlanmalıdır.
- Kullanıcı "Çıkış Yap" butonuna bastığında, Login ekranına yönlendirilmelidir.

- **Nice to Have:**
  - Firebase logout event’i

---

## 📎 Ek Bilgi

- Localizasyon yaparken servisten gelen keylere gösterim yapacağız. Json dosyasında tüm textler hazır olacaktır uygun keyi kullanmanız yeterli olcaktır. ("login_title" : "Hoşgeldiniz")
- Servislerden eğer 401 gelirse uygulama Logine yönlenmelidir ve kullanıcı bilgileri silinmelidir..
---

> Bu proje, minimum geliştirme ile farklı marka ihtiyaçlarına uyum sağlamayı hedefleyen, ölçeklenebilir ve modüler bir yapı üzerine kurulmuştur.
