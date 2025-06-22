# NeuroTask

**Yapay Zekâ Destekli Masaüstü Görev ve Odak Takip Sistemi**

---

## İçindekiler

- [Proje Hakkında](#proje-hakkında)  
- [Proje Yapısı](#proje-yapısı)  
- [Teknolojiler & Bağımlılıklar](#teknolojiler--bağımlılıklar)  
- [Kurulum ve Çalıştırma](#kurulum-ve-çalıştırma)  
- [Yapılandırma (Configuration)](#yapılandırma-configuration)  
- [Branch ve Versiyon Kontrolü](#branch-ve-versiyon-kontrolü)  
- [Kodlama Standartları](#kodlama-standartları)  
- [Katmanlar ve Sorumluluklar](#katmanlar-ve-sorumluluklar)  
- [Dependency Injection (DI)](#dependency-injection-di)  
- [Yapay Zekâ Entegrasyonu](#yapay-zekâ-entegrasyonu)  
- [Geliştirme Rehberi](#geliştirme-rehberi)  
- [Testler](#testler)  
- [Katkıda Bulunma](#katkıda-bulunma)  
- [Lisans](#lisans)  

---

## Proje Hakkında

NeuroTask, kullanıcıların günlük görevlerini takip etmelerini ve odaklanmalarını destekleyen, yapay zekâ destekli bir masaüstü uygulamasıdır.  
.NET 8 ile geliştirilmiş olup, ileride mobil versiyonlarla senkronize çalışması hedeflenmektedir.  
Yapay zekâ modülü, görev önerileri ve odak süresi optimizasyonu gibi özellikler sunar.

---

## Proje Yapısı

Solution: NeuroTask

    NeuroTask.Desktop (Ana masaüstü uygulaması, WPF)

    NeuroTask.Core (Domain modelleri, iş kuralları, servis arayüzleri)

    NeuroTask.Data (Veri erişim katmanı, repositoryler)

    NeuroTask.AI (Yapay zekâ servisleri ve entegrasyonları)

---

## Teknolojiler & Bağımlılıklar

- .NET 8  
- WPF (NeuroTask.Desktop için)  
- Microsoft.Extensions.DependencyInjection (Dependency Injection için)  
- MS SQL Server (Veritabanı)  
- ML.NET API veya benzeri yapay zekâ API’si (NeuroTask.AI)  
- Dapper veya Entity Framework Core (veritabanı erişim için)  

---

## Kurulum ve Çalıştırma

1. GitHub deposunu klonlayın:  
   ```bash
   git clone https://github.com/KullaniciAdi/NeuroTask.git

    Visual Studio 2022 veya üzeri ile çözümü açın.

    NeuroTask.Desktop projesini başlangıç projesi olarak seçin.

    config.json dosyasını NeuroTask.Desktop içinde oluşturun ve gerekli bağlantı dizesi ile AI API anahtarını ekleyin.

    Gerekli NuGet paketlerini yükleyin:

        Microsoft.Extensions.DependencyInjection

        Dapper veya Microsoft.EntityFrameworkCore (hangi ORM kullanıyorsanız)

        System.Data.SqlClient veya Microsoft.Data.SqlClient

    Veritabanı bağlantı ayarlarını güncelleyin ve veritabanı oluşturun.

    Uygulamayı çalıştırın.

---

## Yapılandırma (Configuration)

config.json örneği:

    {
      "ConnectionStrings": {
        "DefaultConnection": "Server=YOUR_SERVER;Database=NeuroTaskDB;Trusted_Connection=True;TrustServerCertificate=True;"
      },
      "AI": {
        "ApiKey": "YOUR_API_KEY_HERE"
      },
      "Logging": {
        "LogLevel": "Information"
      }
    }

    Config dosyası NeuroTask.Desktop projesinin kök dizininde olmalıdır.

    Config değerleri uygulama başlatılırken okunur ve ilgili servislere DI ile aktarılır.

---

## Branch ve Versiyon Kontrolü

    main branch’ı: Stabil, deploy edilebilir sürümler içerir.

    develop branch’ı: Güncel geliştirme kodları için.

    Feature branch’ları: Yeni özellik geliştirmek için feature/özellik-adi formatında.

    Bugfix branch’ları: Hata düzeltmeleri için bugfix/hata-adi.

    PR (Pull Request) ile kod review ve test sonrasında develop veya main branch’ına merge edilir.

---

## Kodlama Standartları

    C# kodlama standartlarına uyulmalı (camelCase, PascalCase kullanımı)

    Yorum satırları ile önemli fonksiyonlar ve karmaşık kodlar açıklanmalı

    Async metotlar tercih edilmeli, async/await kullanılmalı

    Dependency Injection kullanılmalı, new operatörü ile bağımlılık oluşturulmamalı

    Exception handling için global ve lokal strateji belirlenmeli

---

## Katmanlar ve Sorumluluklar
    NeuroTask.Core	Domain modelleri, iş kuralları, servis arayüzleri
    NeuroTask.Data	Veritabanı erişimi, repositoryler
    NeuroTask.AI	Yapay zekâ API entegrasyonu, AI iş mantığı
    NeuroTask.Desktop	Kullanıcı arayüzü, DI konfigürasyonu

---

## Dependency Injection (DI)

    Microsoft.Extensions.DependencyInjection paketi kullanılır.

    Tüm servis ve repository arayüzleri ServiceCollection üzerinden kayıt edilir.

    Ana uygulamada ServiceProvider oluşturularak servisler çekilir.

    Böylece test edilebilirlik ve modülerlik sağlanır.

---

## Yapay Zekâ Entegrasyonu

    AI modülü, görev önerileri ve odak süresi analizleri için API çağrıları yapar.

    NeuroTask.AI projesinde IAIService ve AIService gibi arayüz ve implementasyonlar yer alır.

    API anahtarı config.json üzerinden alınır ve servislerde kullanılır.

---

## Geliştirme Rehberi

    Öncelikle NeuroTask.Core içinde domain modelleri ve servis arayüzlerini oluşturun.

    NeuroTask.Data’da repositoryleri ve veri erişim mantığını yazın.

    NeuroTask.AI katmanında yapay zekâ ile ilgili servisleri geliştirin.

    NeuroTask.Desktop içinde arayüzü tasarlayın ve servisleri DI ile çekip kullanın.

    Küçük parçalara bölerek feature branch’lar açın ve PR ile kodunuzu main/develop branch’larına entegre edin.

---

## Testler

    Unit testler NeuroTask.Core ve NeuroTask.Data katmanları için önerilir.

    AI katmanı için entegrasyon testleri yazılabilir.

    UI testi için WPF UI test araçları veya manuel test planları kullanılabilir.

---

## Katkıda Bulunma

    Fork yapıp feature branch açarak geliştirme yapabilirsiniz.

    Kod standartlarına uyun ve kapsamlı test yapın.

    Pull Request açarken detaylı açıklama ekleyin.

    Sorunları GitHub Issues bölümüne bildirin.

---

## Lisans

Bu proje MIT Lisansı ile lisanslanmıştır. Detaylar için LICENSE dosyasına bakınız.

---

## İletişim
Proje ile ilgili soru, öneri veya destek için:

    E-posta: 1741kerem@gmail.com

    GitHub: github.com/KeremZayim
