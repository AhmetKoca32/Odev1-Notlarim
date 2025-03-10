# 📌 Pydantic Nedir?

[Pydantic](https://docs.pydantic.dev/) Python için veri doğrulama ve ayıklama (parsing) sağlayan bir kütüphanedir. **Python'un type hinting sistemini** kullanarak JSON veya Python objeleri üzerinde veri doğrulama yapmamıza olanak tanır.

Pydantic'in temel amacı, veri modellerini tanımlamak, doğrulamak ve yönetmektir. **FastAPI** gibi modern Python framework'lerinde veri doğrulama işlemleri için yaygın olarak kullanılır.

---

## 🎯 Pydantic'in Faydaları
✅ **Otomatik Veri Doğrulama**: Yanlış veri türlerini algılar ve hata fırlatır.  
✅ **Dönüştürme ve Normalizasyon**: Verileri belirli türlere dönüştürebilir.  
✅ **Basit ve Anlaşılır**: Python'un type hints sistemini kullanır.  
✅ **JSON desteği**: JSON serileştirme ve ayrıştırma işlemleri kolaydır.  

---

## 🔧 Pydantic Kurulumu
Pydantic kütüphanesini yüklemek için aşağıdaki komutu kullanabilirsin:

```bash
pip install pydantic
```

Eğer **Pydantic v2** kullanıyorsan, aşağıdaki komut ile yükleyebilirsin:

```bash
pip install pydantic[email]
```

---

## 🚀 Pydantic ile Temel Kullanım

### 📌 Basit Model Tanımlama
```python
from pydantic import BaseModel

class User(BaseModel):
    id: int
    name: str
    email: str
    age: int

# Geçerli bir kullanıcı
user = User(id=1, name="Ahmet", email="ahmet@example.com", age=25)
print(user)
```

📌 **Yanlış veri tipinde giriş yapılırsa hata fırlatır:**
```python
user = User(id="a", name="Ahmet", email="ahmet@example.com", age=25)
```
⛔ **Hata:** `ValidationError: id must be an integer`

---

## 🎯 Pydantic ile Veri Doğrulama
Pydantic, otomatik olarak **veri doğrulama (validation) ve dönüşüm (conversion)** işlemlerini yapar.

### 🔍 Varsayılan Değerler ve Doğrulama

```python
from pydantic import BaseModel, Field

class Product(BaseModel):
    name: str
    price: float = Field(gt=0, description="Fiyat 0'dan büyük olmalı")
    stock: int = Field(default=10, ge=0)

# Geçerli bir ürün
product = Product(name="Laptop", price=1200.5)
print(product)
```

- `gt=0` → **Fiyat 0'dan büyük olmalı.**
- `default=10` → **Varsayılan stok miktarı 10.**
- `ge=0` → **Stok miktarı 0 veya daha büyük olmalı.**

📌 Eğer **fiyat negatif verilirse**, hata alınır:
```python
product = Product(name="Laptop", price=-10)
```
⛔ **ValidationError:** `price must be greater than 0`

---

## 📌 JSON ve Dict Dönüştürme
Pydantic modelleri, kolayca JSON ve `dict` formatına dönüştürülebilir.

```python
user = User(id=1, name="Ahmet", email="ahmet@example.com", age=25)

# Dictionary'ye çevirme
print(user.dict())

# JSON formatına çevirme
print(user.json())
```

---

## 🔥 Gelişmiş Kullanım

### 📌 E-posta Doğrulama
```python
from pydantic import BaseModel, EmailStr

class User(BaseModel):
    name: str
    email: EmailStr

# Geçerli e-posta
user = User(name="Ahmet", email="ahmet@example.com")
print(user)

# Geçersiz e-posta
user = User(name="Mehmet", email="mehmet.com")  # ⛔ HATA!
```

---

### 📌 Tarih ve Saat Kullanımı
Pydantic, **datetime** nesneleriyle kolayca çalışabilir.

```python
from pydantic import BaseModel
from datetime import datetime

class Event(BaseModel):
    name: str
    start_time: datetime

event = Event(name="Toplantı", start_time="2024-03-10T15:00:00")
print(event)
```

✅ **Pydantic, tarih ve saat bilgisini otomatik olarak `datetime` nesnesine çevirir.**

---

## 🏆 Sonuç
Pydantic, veri doğrulama ve dönüştürme işlemlerini oldukça kolaylaştıran güçlü bir kütüphanedir. **Özellikle API geliştirme ve veri girişlerini doğrulama süreçlerinde büyük kolaylık sağlar.**

✅ **Kolay kullanım**  
✅ **Otomatik doğrulama ve dönüştürme**  
✅ **JSON ve dict desteği**  
✅ **FastAPI gibi framework'ler ile uyumlu**

Eğer API geliştirme yapıyorsan veya veri doğrulama süreçlerini kolaylaştırmak istiyorsan, **Pydantic tam sana göre!** 🚀
