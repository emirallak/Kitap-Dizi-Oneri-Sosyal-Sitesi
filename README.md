# Kitap ve Dizi/Film Öneri Sosyal Platformu

> A Spring Boot social platform where users discover books and films via the Google Books and TMDB APIs, build libraries and custom lists, follow each other, and like or comment on activity.

Kocaeli Üniversitesi Bilgisayar Mühendisliği, **Yazılım Laboratuvarı** kapsamında geliştirilmiş bir web uygulaması. Kullanıcılar kitap, film ve dizileri arar, kendi kütüphanelerine ekler, özel listeler oluşturur ve diğer kullanıcıların aktivitelerini takip eder.

## Özellikler

- **Kimlik doğrulama:** Spring Security ile kayıt olma, giriş yapma ve oturum yönetimi.
- **İçerik arama:**
  - Kitaplar için **Google Books API**, film ve diziler için **TMDB API** entegrasyonu.
  - Kitap ve film detay sayfaları.
- **Kişisel kütüphane:** İçerikleri kullanıcı kütüphanesine ekleme.
- **Özel listeler:** Liste oluşturma ve silme, listeye içerik ekleme ve çıkarma.
- **Sosyal özellikler:**
  - Kullanıcı profilleri ve profil düzenleme.
  - Diğer kullanıcıları takip etme.
  - Aktivite akışı.
  - Aktivitelere beğeni ve yorum ekleme ve yorum silme.

## Mimari

Uygulama katmanlı bir **MVC** yapısıyla geliştirildi:

```
src/main/java/org/example/yazlab2/
├── Kontroller/   # Spring MVC controller'ları (AnaSayfa, Arama, Detay, Profil, OzelListe, Begeni…)
├── Servis/       # İş mantığı + dış API istemcileri (TmdbServis, GoogleBooksServis…)
├── Depo/         # Spring Data JPA repository'leri
├── Varliklar/    # JPA entity'leri (Kullanici, Icerik, OzelListe, Takip, AktiviteYorum…)
├── DTO/          # API yanıtları ve görünüm modelleri
└── Ayarlar/      # Spring Security yapılandırması
src/main/resources/templates/   # Thymeleaf şablonları
```

**Veri modeli:** `Kullanici`, `Icerik`, `KullaniciIcerik` (kütüphane), `OzelListe` / `OzelListeIcerik`, `Takip`, `AktiviteBegeni`, `AktiviteYorum`. Tablolar Hibernate tarafından otomatik oluşturulur (`ddl-auto=update`).

## Teknolojiler

| Alan | Teknoloji |
| --- | --- |
| Dil | Java 17 |
| Framework | Spring Boot 4, Spring MVC, Spring Security, Spring Data JPA, Bean Validation |
| Görünüm | Thymeleaf |
| Veritabanı | PostgreSQL |
| Dış API'ler | TMDB, Google Books |
| Diğer | Lombok, Maven |

## Kurulum ve Çalıştırma

1. Depodaki `yazlab2.zip` arşivini açın.
2. PostgreSQL'de `yazlab2` adında bir veritabanı oluşturun.
3. `src/main/resources/application.properties` dosyasındaki veritabanı kullanıcı adı ve şifresini düzenleyin.
4. [TMDB](https://www.themoviedb.org/settings/api) üzerinden bir API anahtarı alın ve `TmdbServis` sınıfına tanımlayın.
5. Uygulamayı başlatın:

   ```bash
   cd yazlab2
   mvn spring-boot:run
   ```

6. Tarayıcıda `http://localhost:8080` adresini açın.

## Geliştirici

**Muhammed Emir Allak**: [GitHub](https://github.com/emirallak) · [LinkedIn](https://www.linkedin.com/in/muhammedemir-allak-a445a3246/)
