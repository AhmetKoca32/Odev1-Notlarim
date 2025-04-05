# 🌐 HTTP Protokolleri Nedir? Ne İçin Kullanılır?

## 📘 HTTP Nedir?

**HTTP (HyperText Transfer Protocol)**, istemci (client) ile sunucu (server) arasında veri iletimi için kullanılan bir iletişim protokolüdür. Genellikle web tarayıcıları ve web sunucuları arasında gerçekleşen iletişimin temelini oluşturur. HTTP, metin, resim, video ve diğer multimedya içeriklerin internet üzerinden iletilmesini sağlar.

## 🔧 HTTP Ne İçin Kullanılır?

HTTP, özellikle aşağıdaki amaçlarla kullanılır:

- Web sitelerinin kullanıcıya içerik sunması
- Form verilerinin sunucuya iletilmesi
- API (Application Programming Interface) üzerinden veri alışverişi
- Web servisleri ile iletişim
- Dosya indirme/yükleme işlemleri

---

## 🧩 HTTP Nasıl Çalışır?

HTTP, **istemci-sunucu modeli**ne göre çalışır:

1. **İstemci (Client)**: Genellikle bir web tarayıcısıdır. Belirli bir URL’ye (örneğin, `https://example.com`) istek gönderir.
2. **Sunucu (Server)**: İsteği alır, işler ve yanıt verir. Yanıt genellikle HTML, JSON, XML, resim veya video olabilir.
3. **İletişim Süreci**:
   - Bağlantı kurulmaz (HTTP 1.0’da her istek ayrı bağlantı ile yapılırdı, HTTP/1.1 ve HTTP/2’de kalıcı bağlantı kullanılabilir).
   - İstemci bir **HTTP Request** (İstek) gönderir.
   - Sunucu buna bir **HTTP Response** (Yanıt) döner.

---

## 🛠️ HTTP Metotları

HTTP protokolü, sunucuya ne tür bir işlem yapılacağını belirtmek için bazı metotlar (verbs) kullanır:

| Metot  | Açıklama |
|--------|----------|
| `GET`     | Sunucudan veri istemek için kullanılır. Örn: bir web sayfasını görüntülemek |
| `POST`    | Sunucuya veri göndermek için kullanılır. Örn: bir form gönderimi |
| `PUT`     | Var olan veriyi güncellemek için |
| `DELETE`  | Bir kaynağı silmek için |
| `PATCH`   | Kaynağın bir kısmını güncellemek için |
| `HEAD`    | `GET` gibidir ama sadece başlık bilgisi döner |
| `OPTIONS` | Sunucunun hangi metotlara izin verdiğini sorgulamak için |

---

## 📦 HTTP İstek ve Yanıt Yapısı

### 📨 HTTP İsteği (Request)

Bir HTTP isteği 3 ana bölümden oluşur:

```
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0
```

### 📬 HTTP Yanıtı (Response)

Sunucu tarafından dönen örnek bir yanıt:

```
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 1234

<html>...</html>
```

---

## 🔐 HTTP vs HTTPS

| Özellik | HTTP | HTTPS |
|--------|------|-------|
| Güvenlik | Şifreleme yok | SSL/TLS ile şifrelenmiş |
| Veri Gizliliği | Yok | Var |
| Port | 80 | 443 |
| Kullanım Alanı | Genel | Güvenli veri iletimi gereken yerlerde (bankacılık, giriş formları vb.) |

---

## ⚙️ HTTP Sürümleri

| Sürüm | Özellikler |
|-------|------------|
| HTTP/1.0 | Her istek için ayrı bağlantı kurar |
| HTTP/1.1 | Kalıcı bağlantı, daha hızlı |
| HTTP/2 | Çoklu istekler tek bağlantıda taşınabilir (multiplexing), daha verimli |
| HTTP/3 | UDP tabanlı, daha hızlı ve düşük gecikmeli iletişim |

---

## 📌 Özetle

- HTTP, internet üzerinden veri alışverişini sağlayan temel protokoldür.
- Web sitelerinin çalışmasını mümkün kılar.
- Birçok farklı metot sayesinde farklı işlemleri yönetir.
- HTTPS ile güvenli hale getirilir.
