# **FastAPI Nedir?**

FastAPI, Python ile **hızlı, modern ve yüksek performanslı** API'ler oluşturmak için kullanılan bir web framework'üdür. **Pydantic** ve **Starlette** üzerine inşa edilmiştir ve özellikle **hız, kolay kullanım, tip güvenliği ve otomatik dokümantasyon** özellikleriyle öne çıkar.

---

## **FastAPI'nin Avantajları**

✅ **Yüksek Performans:**  
- FastAPI, **Node.js ve Go** gibi framework'lerle karşılaştırılabilecek performans sunar.  
- **Asenkron programlama** desteği sayesinde yüksek trafikli uygulamalar için idealdir.  

✅ **Kolay Kullanım & Hızlı Geliştirme:**  
- **Minimal ve okunabilir** kod yapısı sayesinde hızlı API geliştirmeyi sağlar.  
- Geleneksel **Flask** veya **Django** ile karşılaştırıldığında **daha az boilerplate kod** gerektirir.  

✅ **Tip Güvenliği & Otomatik Validasyon:**  
- **Python'un type hinting** özelliğini kullanarak **veri doğrulama** ve **hata yakalama** işlemlerini otomatik olarak yapar.  
- Yanlış veri girişleri için **otomatik hata mesajları üretir**.  

✅ **Otomatik Swagger & Redoc Desteği:**  
- API için **Swagger UI ve Redoc** dokümantasyonlarını otomatik olarak oluşturur.  

✅ **Asenkron Programlama Desteği:**  
- `async` ve `await` kullanarak yüksek performanslı asenkron işlemleri destekler.  

---

## **FastAPI ile İlk API Uygulaması**

### 📌 **1. Kurulum**  
FastAPI'yi ve çalıştırmak için bir HTTP server olan **Uvicorn**'u yükleyelim:

```bash
pip install fastapi uvicorn
```

### 📌 **2. Basit Bir API Oluşturma**
Aşağıdaki kod ile **basit bir "Hello World" API'si** oluşturabiliriz:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello, FastAPI!"}
```

### 📌 **3. API'yi Çalıştırma**
`main.py` dosyanı **Uvicorn** ile çalıştır:

```bash
uvicorn main:app --reload
```

✅ **Çalıştırdıktan sonra aşağıdaki adreslerden API'ye erişebilirsin:**  
- **Ana Sayfa:** [http://127.0.0.1:8000](http://127.0.0.1:8000)  
- **Swagger UI:** [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)  
- **Redoc UI:** [http://127.0.0.1:8000/redoc](http://127.0.0.1:8000/redoc)  

---

## **FastAPI'de HTTP Metodları Kullanımı**

FastAPI'de farklı HTTP metodlarını kullanarak CRUD işlemleri gerçekleştirebiliriz.

### **1. GET - Veri Okuma**
```python
@app.get("/items/{item_id}")
def read_item(item_id: int, q: str = None):
    return {"item_id": item_id, "query": q}
```

**Örnek Çağrı:**  
`GET /items/10?q=example`  
**Yanıt:**
```json
{
  "item_id": 10,
  "query": "example"
}
```

---

### **2. POST - Yeni Veri Ekleme**
```python
from pydantic import BaseModel

class Item(BaseModel):
    name: str
    price: float
    is_offer: bool = None

@app.post("/items/")
def create_item(item: Item):
    return {"message": "Item created", "item": item}
```

**Örnek JSON Gönderimi:**
```json
{
  "name": "Laptop",
  "price": 2500.99,
  "is_offer": true
}
```

---

### **3. PUT - Veri Güncelleme**
```python
@app.put("/items/{item_id}")
def update_item(item_id: int, item: Item):
    return {"message": "Item updated", "item_id": item_id, "item": item}
```

---

### **4. DELETE - Veri Silme**
```python
@app.delete("/items/{item_id}")
def delete_item(item_id: int):
    return {"message": f"Item {item_id} deleted"}
```

---

## **FastAPI'de Asenkron Programlama**
FastAPI, **asenkron fonksiyonları** destekler ve `async def` ile tanımlanan fonksiyonlar kullanılarak işlemler bloklanmadan çalıştırılabilir.

```python
import asyncio

@app.get("/async_example")
async def async_example():
    await asyncio.sleep(2)  # 2 saniye bekle
    return {"message": "Asenkron işlem tamamlandı!"}
```

---

## **FastAPI'de Middleware Kullanımı**
Middleware, gelen istekleri işlemek veya yanıtları değiştirmek için kullanılır.

```python
from fastapi import Request
from fastapi.middleware.cors import CORSMiddleware

# CORS Middleware ekleme
app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],  # Tüm domainlere izin ver
    allow_credentials=True,
    allow_methods=["*"],  
    allow_headers=["*"],
)

@app.middleware("http")
async def add_process_time_header(request: Request, call_next):
    response = await call_next(request)
    response.headers["X-Process-Time"] = str(0.5)
    return response
```

---

## **FastAPI ile Veritabanı Kullanımı**
FastAPI, SQLAlchemy ve Tortoise ORM gibi ORM kütüphaneleriyle veritabanı işlemlerini destekler.

### **SQLite Kullanımı (SQLAlchemy ile)**
```python
from sqlalchemy import create_engine, Column, Integer, String
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy.orm import sessionmaker

DATABASE_URL = "sqlite:///./test.db"
engine = create_engine(DATABASE_URL)
SessionLocal = sessionmaker(autocommit=False, autoflush=False, bind=engine)
Base = declarative_base()

class User(Base):
    __tablename__ = "users"

    id = Column(Integer, primary_key=True, index=True)
    name = Column(String, index=True)

Base.metadata.create_all(bind=engine)
```

---

## **FastAPI ile Authentication (JWT Kullanımı)**
JWT (JSON Web Token) ile kullanıcı doğrulama işlemi yapmak mümkündür.

```python
from fastapi.security import OAuth2PasswordBearer

oauth2_scheme = OAuth2PasswordBearer(tokenUrl="token")

@app.get("/users/me")
async def read_users_me(token: str = Depends(oauth2_scheme)):
    return {"token": token}
```

---

## **FastAPI'nin Kullanım Alanları**
- **RESTful API geliştirme**
- **Gerçek zamanlı veri işleme**
- **Mikro servis mimarileri**
- **Veri doğrulama ve giriş kontrolü**
- **AI & Machine Learning servisleri**
- **IOT (Internet of Things) uygulamaları**

---

## **Sonuç**
FastAPI, modern Python uygulamaları için **hızlı, verimli ve güvenli** bir API framework'üdür. Özellikle **asenkron destek**, **tip güvenliği**, **otomatik dokümantasyon** ve **yüksek performans** gibi özellikleri sayesinde birçok modern projede tercih edilmektedir.

Eğer **hızlı bir şekilde API geliştirmek** istiyorsan, FastAPI harika bir seçenek! 🚀

