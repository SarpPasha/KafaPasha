# KafaPasha Studio — 3D Minecraft Stream Avatar & Hardware Telemetry

**KafaPasha Studio**, yayıncılar için geliştirilmiş **60 FPS 3D Minecraft Karakter, Mekanik Klavye ve Mouse Telemetri Stüdyosu** uygulamasıdır. Bu depo, uygulamanın **Uzaktan Otomatik Güncelleme (`.version` & `.exe`)** ve **Merkezi API Anahtarı / HWID Lisans Kontrol (`licenses.json`)** dağıtım merkezidir.

---

## Depo Açıklaması (GitHub Description)

> **KafaPasha Studio — 60 FPS 3D Minecraft Stream Avatar, Mekanik Klavye & Mouse Telemetri Stüdyosu (Resmi OTA Güncelleme ve Lisans Dağıtım Deposu)**

---

## Uzaktan Güncelleme & Lisans Mekanizması Nasıl Çalışır?

Bu depoda kaynak kod **bulunmaz**; yalnızca derlenmiş ve 6 katmanlı tersine mühendislik korumasıyla şifrelenmiş dağıtım dosyaları yer alır:

| Dosya | Görevi |
| :--- | :--- |
| [`.version`](.version) | Güncel uygulama sürüm numarasını (ör. `3.3.0`) tutar. Uygulama açılışta ve periyodik olarak bu dosyayı kontrol eder. |
| [`KafaPasha.exe`](KafaPasha.exe) | Güncel ana Windows masaüstü çalıştırılabilir dosyası. |
| `KafaPasha_v<sürüm>.exe` | `.version` dosyasındaki sürüme karşılık gelen sürüm etiketli kurulum/güncelleme paketi (ör. `KafaPasha_v3.3.0.exe`). |
| [`licenses.json`](licenses.json) | SHA-256 + Donanım Kimliği (`HWID`) tabanlı uzaktan API anahtarı doğrulama, cihaz kilitleme (`remote_hwid_locks`) ve askıya alma (`revoked_profiles`) tablosu. |

### Otomatik Güncelleme Akışı
1. Kullanıcı bilgisayarda `KafaPasha.exe` uygulamasını çalıştırdığında uygulama GitHub üzerindeki `.version` dosyasını okur.
2. Eğer GitHub'daki `.version` değeri mevcut uygulama sürümünden büyükse, `.version` içerisindeki sürüme uygun `.exe` dosyasını (`KafaPasha_v<sürüm>.exe` veya `KafaPasha.exe`) doğrudan GitHub üzerinden indirir.
3. İndirilen `.exe` dosyasının PE (`MZ`) bütünlüğünü doğruladıktan sonra mevcut `.exe` dosyasını otomatik olarak günceller ve uygulamayı yeni sürümle yeniden başlatır.

---

## OBS Studio Kurulumu

1. `KafaPasha.exe` uygulamasını çalıştırın.
2. OBS Studio'da **Kaynaklar (Sources) -> [+] -> Tarayıcı (Browser Source)** ekleyin:
   - **URL:** `http://127.0.0.1:8765`
   - **Genişlik:** `650`
   - **Yükseklik:** `600`
   - **FPS:** `60`

---

## Lisans

Telif Hakkı © 2026 **SarpPasha**. Tüm Hakları Saklıdır. Detaylar için [`LICENSE`](LICENSE) dosyasına göz atın.
