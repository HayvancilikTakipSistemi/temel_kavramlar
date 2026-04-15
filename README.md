# 🚀 Backend & Frontend Fundamentals

Bu repo, yazılıma yeni başlayanlar için **backend, frontend ve modern web geliştirme kavramlarını kısa, net ve örneklerle açıklamak** amacıyla hazırlanmıştır.

---

## 📌 İçindekiler

* Backend & API
* Frontend (Blazor, React, Angular)
* DTO & Modelleme
* EF Core & Veritabanı
* Authentication (JWT & Identity)
* CRUD & HTTP
* Yazılım Prensipleri
* Veri Yapıları

---

# 🔹 Backend & API

### Backend Nedir?

Uygulamanın arka planda çalışan kısmıdır (veritabanı, işlemler vs).

### API Nedir?

Frontend ile backend arasında iletişim sağlar.

📌 Örnek:

* Kullanıcıları getir → API → veritabanından çeker → JSON döner

---

### HTTP Metotları

* GET → veri al
* POST → veri gönder
* PUT → güncelle
* DELETE → sil

📌 Örnek:

```http
GET /api/users
POST /api/users
```

---

### GetById

Belirli ID’ye göre veri getirir.

```csharp
var user = users.FirstOrDefault(x => x.Id == 1);
```

---

### CORS

Farklı sitelerin API’ye erişmesine izin verir.

---

### Swagger

API’yi tarayıcıdan test etmeni sağlar.

---

# 🔹 Frontend

### Frontend Nedir?

Kullanıcının gördüğü arayüzdür.

---

### Blazor Nedir?

C# ile frontend yazmanı sağlar.

```csharp
<button @onclick="Artir">Artır</button>

@code {
    int sayi = 0;
    void Artir() => sayi++;
}
```

---

### Blazor WASM

Kod tarayıcıda çalışır.

---

### React / Angular

JavaScript tabanlı frontend teknolojileridir.

---

### View

Kullanıcının gördüğü sayfa.

---

# 🔹 DTO & Modelleme

### DTO Nedir?

Veri taşımak için sade nesne.

```csharp
class UserDTO {
    public int Id;
    public string Name;
}
```

---

### Entity (Model)

Veritabanı tablosunu temsil eder.

---

### DTO vs Entity

* Entity → tüm veri
* DTO → gerekli veri

---

### ExaminationDrug

İlişki tablosu (örnek: Muayene + İlaç)

---

### Self-Referencing

Bir tablonun kendine bağlanması.

```csharp
class Employee {
    public int Id;
    public int? ManagerId;
}
```

---

# 🔹 EF Core & Veritabanı

### EF Core

C# ile veritabanı yönetmeni sağlar.

---

### Code-First

Önce kod yazılır → veritabanı oluşur.

```csharp
class Product {
    public int Id { get; set; }
}
```

---

### Database-First

Önce veritabanı → sonra kod oluşturulur.

---

### Migration

Veritabanını güncelleme sistemi.

---

### EF Core CRUD

```csharp
// Create
context.Add(user);

// Read
context.Users.ToList();

// Update
context.Update(user);

// Delete
context.Remove(user);
```

---

### Try-Catch

Hataları yakalamak için kullanılır.

```csharp
try {
    context.SaveChanges();
}
catch {
    // hata yönetimi
}
```

---

# 🔹 Authentication

### ASP.NET Identity

Hazır kullanıcı sistemi (login/register).

---

### JWT

Kullanıcıya verilen token (kimlik).

📌 Mantık:

* Login → token al
* Sonraki isteklerde gönder

---

### CustomAuthStateProvider

Blazor’da kullanıcı giriş kontrolü yapar.

---

# 🔹 CRUD & Mantık

### CRUD

* Create
* Read
* Update
* Delete

---

### Endpoint

API adresidir.

📌 Örnek:

```
/api/users
```

---

# 🔹 Yazılım Prensipleri

### DRY

Aynı kodu tekrar yazma.

---

### Clean Code

Okunabilir ve düzenli kod yaz.

---

# 🔹 Veri Yapıları

### Dictionary

Anahtar-değer yapısı.

```csharp
var dict = new Dictionary<int, string>();
dict[1] = "Ahmet";
```

---

### LINQ

Liste filtreleme.

```csharp
var sonuc = list.Where(x => x > 5);
```

---

### List Mantığı

Liste üzerinde veri işleme (filtreleme, seçme vs).

---

# 🔹 Genel Mantık

### Client - Server

* Client → istek atar
* Server → cevap verir

---

### Fullstack

Hem frontend hem backend geliştiren kişi.

---

# 🎯 Amaç

Bu repo, temel yazılım kavramlarını **karmaşıklaştırmadan öğretmek** için hazırlanmıştır.

---
