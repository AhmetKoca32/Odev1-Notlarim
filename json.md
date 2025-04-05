# 📦 JSON (JavaScript Object Notation) Nedir?

## 📘 Tanım

**JSON (JavaScript Object Notation)**, verilerin **anahtar-değer (key-value)** çiftleri şeklinde saklandığı ve kolayca okunabilir bir veri biçimidir. Başlangıçta JavaScript tabanlı olsa da günümüzde **Python, Java, C#, PHP, Go, Dart** gibi birçok programlama dili tarafından desteklenmektedir.

---

## 🔍 JSON Nerelerde Kullanılır?

JSON, özellikle **veri aktarımı ve saklama** süreçlerinde yaygın olarak kullanılır:

- 🌐 **Web API’lerde** istemci-sunucu arasında veri alışverişinde  
- 💾 **Veritabanlarında** veri saklamak için (örneğin: MongoDB, Firebase)
- 📲 **Mobil uygulamalarda** veri senkronizasyonu için
- 🔧 **Konfigürasyon dosyalarında** (örnek: `package.json`)
- 🔄 **Veri serileştirme** ve **deserileştirme** işlemlerinde

---

## 🧩 JSON Yapısı

JSON verisi iki temel yapıya dayanır:

1. **Nesne (Object)**: `{ }` süslü parantezlerle tanımlanır ve anahtar-değer çiftleri içerir.
2. **Dizi (Array)**: `[ ]` köşeli parantezlerle tanımlanır ve sıralı veri listesi içerir.

### 📌 Örnek JSON Nesnesi

```json
{
  "isim": "Ahmet Koca",
  "yas": 22,
  "ogrenci": true,
  "diller": ["Java", "Python", "Flutter"],
  "adres": {
    "sehir": "Isparta",
    "ulke": "Türkiye"
  }
}
```

---

## 🔐 Veri Tipleri

JSON'da kullanılabilen veri türleri şunlardır:

| Veri Tipi | Örnek |
|-----------|-------|
| **String** | `"merhaba"` |
| **Number** | `42`, `3.14` |
| **Boolean** | `true`, `false` |
| **Array** | `["elma", "armut"]` |
| **Object** | `{"anahtar": "deger"}` |
| **null** | `null` |

---

## 📡 JSON'un Avantajları

✅ **Basit ve okunabilir** yapı  
✅ **Platformdan bağımsız**  
✅ **Hafif** ve **hızlı işlenebilir**  
✅ XML'e göre daha sade  
✅ Web ve mobil uygulamalarda doğrudan kullanılabilir  

---

## 🔧 JSON Nasıl Kullanılır?

### ✅ JavaScript ile örnek:

```javascript
let jsonData = '{"ad": "Ahmet", "yas": 22}';
let obje = JSON.parse(jsonData);  // JSON string -> JS object

console.log(obje.ad); // "Ahmet"

let yeniJson = JSON.stringify(obje); // JS object -> JSON string
```

### ✅ Python ile örnek:

```python
import json

veri = '{"ad": "Ahmet", "yas": 22}'
obje = json.loads(veri)  # JSON string -> Python dict

print(obje["ad"])  # "Ahmet"

json_string = json.dumps(obje)  # Python dict -> JSON string
```

---

### 🧹 JSON Beautifier Nedir?

**JSON Beautifier (Biçimlendirici)**, karışık ve tek satıra sıkıştırılmış JSON verilerini, **okunabilir** ve **düzenli** hale getiren araçlardır. Bu araçlar özellikle büyük JSON dosyalarında yapıların daha kolay görülmesini sağlar.

#### 🌐 Popüler JSON Beautifier Siteleri:

- [https://jsonformatter.org](https://jsonformatter.org)  
- [https://jsonbeautifier.org](https://jsonbeautifier.org)  
- [https://jsoneditoronline.org](https://jsoneditoronline.org)

#### 🛠️ Ne İşe Yarar?

- Karmaşık JSON verilerini okunabilir hale getirir  
- JSON hatalarını tespit etmeye yardımcı olur  
- Veri yapısını ağaç şeklinde incelemeyi sağlar  
- Geliştiricilerin debug sürecini kolaylaştırır  

---

## 📁 JSON ile Karıştırılanlar

| Format | Açıklama |
|--------|----------|
| **XML** | Daha eski, daha karmaşık bir veri formatı |
| **YAML** | Özellikle konfigürasyon dosyalarında popüler |
| **CSV** | Tablo şeklinde veri saklamak için kullanılır, yapısal veri desteği zayıf |

---

## 🧠 Özetle

- **JSON**, veri alışverişinde kullanılan **hafif**, **okunabilir** ve **dil bağımsız** bir formattır.
- Web servislerinden mobil uygulamalara, konfigürasyonlardan veritabanlarına kadar birçok alanda kullanılır.
- Anahtar-değer mantığı ile çalışır ve dizilerle desteklenir.
- **JSON Beautifier** araçları, JSON verisini daha anlaşılır hale getirerek geliştirme sürecini kolaylaştırır.
