# API Nedir?

## API (Application Programming Interface) Nedir?

API (Uygulama Programlama Arayüzü), farklı yazılımların birbiriyle iletişim kurmasını sağlayan bir ara yüzdür. API'ler, geliştiricilere belirli bir sistemin veya hizmetin yeteneklerini kullanabilmeleri için bir dizi fonksiyon ve protokol sunar.

## API'nin Amacı ve Kullanım Alanları

API'ler, uygulamaların birbirleriyle etkileşimde bulunmasını kolaylaştırır ve yazılım geliştiricilere zamandan tasarruf sağlar. API'lerin yaygın kullanım alanları şunlardır:

- **Web API'leri**: Farklı web hizmetlerinin (Google Maps, Twitter API vb.) entegrasyonu
- **Veritabanı API'leri**: Veritabanına erişim ve sorgulama yapılması
- **Donanım API'leri**: Yazılımların donanımla iletişim kurması (kamera, mikrofon vb.)
- **Bulut Servisleri API'leri**: AWS, Google Cloud gibi hizmetlerin kullanılması
- **Mobil API'ler**: Android ve iOS sistemleri için geliştirilen API'ler

## API Çeşitleri

API'ler kullanım alanlarına ve erişim düzeylerine göre farklı türlere ayrılabilir:

### 1. **Açık (Public) API'ler**
Bu API'ler herkese açıktır ve genellikle belirli bir kimlik doğrulama mekanizması ile erişilebilir.

### 2. **Özel (Private) API'ler**
Belirli bir organizasyon veya uygulama içinde kullanılır ve dışarıdan erişime kapalıdır.

### 3. **Ortak (Partner) API'ler**
Sadece belirli iş ortaklarının kullanabileceği API'lerdir.

### 4. **Kompozit API'ler**
Birden fazla API'yi birleştirerek tek bir istekte birden fazla işlem yapmaya olanak tanır.

## API Mimarileri ve Protokolleri

API'ler farklı mimariler ve protokoller kullanarak geliştirilebilir. En yaygın API mimarileri şunlardır:

### 1. **RESTful API**
- HTTP protokolü üzerinden çalışır
- JSON veya XML veri formatını kullanır
- Stateless (durumsuz) yapısı sayesinde her isteğini bağımsız olarak ele alır

### 2. **SOAP API**
- XML tabanlı bir protokoldür
- HTTP, SMTP gibi protokoller üzerinden çalışabilir
- Daha güvenli ve katı bir yapıya sahiptir

### 3. **GraphQL API**
- Kullanıcıların tam olarak ihtiyacı olan veriyi sorgulamasını sağlar
- REST'e göre daha esnek ve optimize edilmiştir

### 4. **gRPC API**
- Google tarafından geliştirilmiştir
- Yüksek performanslı iletişim sağlar
- Protobuf (Protocol Buffers) veri formatını kullanır

## API Kullanımı ve Örnek Bir API Talebi

API kullanımı genellikle belirli HTTP metodları ile gerçekleştirilir:

- **GET**: Veri çekme
- **POST**: Veri gönderme
- **PUT**: Veri güncelleme
- **DELETE**: Veri silme

### Örnek Bir REST API Talebi (Python):
```python
import requests

url = "https://api.example.com/data"
headers = {"Authorization": "Bearer YOUR_API_KEY"}
response = requests.get(url, headers=headers)

if response.status_code == 200:
    print(response.json())
else:
    print("Hata: ", response.status_code)
```

Bu kod, belirli bir URL'ye API isteği göndererek JSON formatında veri çekmektedir.

## Sonuç

API'ler, modern yazılım geliştirmenin ayrılmaz bir parçası haline gelmiştir. Web servislerinden mobil uygulamalara kadar çok geniş bir alanda kullanılan API'ler, sistemlerin birbiriyle entegrasyonunu sağlayarak geliştiricilere esneklik ve verimlilik kazandırır. Doğru API mimarisi ve protokolü seçilerek en iyi performans ve güvenlik sağlanabilir.

