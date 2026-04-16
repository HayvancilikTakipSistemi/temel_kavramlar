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

### API Nedir? API (Application Programming Interface)

Frontend ile backend arasında iletişim sağlar.

📌 Örnek:

* Kullanıcıları getir → API → veritabanından çeker → JSON döner
* json nedir? farklı sistemlerin veri alışverişi için standartlaştırılmış ve verimli bir yol sağlayan hafif bir veri alışverişi formatıdır

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

### CORS (Cross-Origin Resource Sharing)

Farklı sitelerin API’ye erişmesine izin verir.
Yani bir web sitesinin başka bir domain’den veri isteyip isteyemeyeceğini kontrol eder
---

### Swagger

API’yi tarayıcıdan test etmeni sağlar.
 yani  aslında bir nevi API (Application Programming Interface) dokümantasyonu oluşturmak, paylaşmak ve test etmek için kullanılan bir araç ve çerçevedir

---

# 🔹 Frontend

### Frontend Nedir?

Kullanıcının gördüğü arayüzdür.

---

### Blazor Nedir?

HTML, CSS ve C# tabanlı, web uygulamalarını daha hızlı geliştirmenize yardımcı olan modern bir ön uç web çerçevesidir.

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
web tarayıcısında çalışan yazılımlar oluşturmak için geliştirilmiş bir standarttır

---

### React / Angular
JavaScript tabanlı frontend teknolojileridir.
react:  single-page sayfalar ve mobil uygulamalar geliştirmek için kullanılır
Google tarafından geliştirilen, TypeScript ile yazılmış, açık kaynaklı,
Angular: SPA (Single Page Application) uygulamaları yapılmasını sağlayan JavaScript framework'üdür

---

### View

Kullanıcının gördüğü sayfa.

---

# 🔹 DTO & Modelleme

### DTO Nedir?

Veri taşımak için sade nesne.
DTO (Data Transfer Object) kullanılmasının nedeni veri transferidir. Örneğin, bir client sayfasının bir sunucudan veri alması veya sunucuya veri göndermesi gerektiğinde, DTO’lar veri taşıma işlemini etkin ve düzenli bir şekilde üstlenir.

```csharp
class UserDTO {
    public int Id;
    public string Name;
}
```

---

### Entity (Model)

Veritabanı tablosunu temsil eder.
Veritabanındaki tablolara karşılık gelen nesnelerdir
---

### DTO vs Entity

* Entity → tüm veri
* DTO → sadece gerekli veri
* 🚨 Neden DTO kullanılır?

Eğer DTO kullanmazsan:

Gereksiz veri dışarı çıkar
Güvenlik açığı oluşur
API çok “ağır” olur
Model bağımlılığı oluşur (kötü tasarım)

---

### ExaminationDrug

İlişki tablosu (örnek: Muayene + İlaç)

---

### Self-Referencing
bu aslında psikoloi teriminden geliyor. Bireylerin kendileriyle kişisel olarak ilgili bilgileri daha iyi hatırladıkları psikolojik bir olgudur
yazılımda ise;
Bir tablonun kendine bağlanması olarak açıklanabilir.

```csharp
class Employee {
    public int Id;
    public int? ManagerId;
}
```

---

# 🔹 EF Core & Veritabanı

### EF Core

Entity Framework Core:
Geliştiricilerin SQL sorguları yazmak yerine .NET (C#) nesnelerini kullanarak veritabanlarıyla etkileşim kurmasına olanak tanır, böylece .NET uygulamaları oluştururken veri erişimini daha basit ve esnek hale getirir.

C# ile veritabanı yönetmeni sağlar.

---

### Code-First

Önce kod yazılır → veritabanı oluşur.
Nasıl çalışır (3 adım)
Class yaz
Migration al
Database güncelle

Bitti.

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
Sen kodda değişiklik yaparsın (Entity değiştirirsin)
Ama database bunu kendiliğinden anlamaz

👉 İşte migration devreye girer:

“Kodda ne değiştiyse, database’e nasıl uygulanacağını söyler”

---

### EF Core CRUD
| Kısaltma | Anlamı | Ne yapar       |
| -------- | ------ | -------------- |
| C        | Create | Veri ekler     |
| R        | Read   | Veri okur      |
| U        | Update | Veri günceller |
| D        | Delete | Veri siler     |



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
Giriş yaptın → Authentication ✅
sen kimsin gibisinden kim girdi hesabı

### ASP.NET Identity

Hazır kullanıcı sistemi (login/register).
🧠 Ne yapar?

Senin yerine:

👤 Kullanıcı oluşturur (register)
🔑 Giriş yaptırır (login)
🔒 Şifreyi güvenli şekilde saklar (hash)
🛡️ Rol sistemi sağlar (admin, user)
🔄 Şifre sıfırlama işlemleri yapar

📦 Örnek düşün

Normalde kendin yazman gerekir:

şifreyi hashle
kullanıcıyı kontrol et
token üret
güvenlik açıklarını kapat

👉 Ama Identity ile:

“kullanıcı oluştur” dersin → gerisini o yapar

---

### JWT
JWT (JSON Web Token) = kullanıcı giriş yaptıktan sonra verilen kimlik kartı (token)


📌 Mantık:

* Login → token al
* Sonraki isteklerde gönder

---

### CustomAuthStateProvider

Blazor’da kullanıcı giriş kontrolü yapar.
🎯 Örnek senaryo

Kullanıcı login oldu → JWT aldın

👉 CustomAuthStateProvider:

token’ı okur
kullanıcıyı tanımlar
“bu user giriş yapmış” der
---

# 🔹 CRUD & Mantık

### CRUD

* Create
* Read
* Update
* Delete
CRUD = veri yönetiminin temeli

Backend → CRUD yapar
API → CRUD endpoint sunar
Frontend → CRUD kullanır

👉 Tüm sistem bunun üstüne kurulu

---

### Endpoint

API adresidir.
Frontend bir istek atar
👉 Bu istek belirli bir adrese gider
👉 İşte o adres = endpoint

📦 Örnek
GET /animals

👉 Bu bir endpoint’tir
→ “Tüm hayvanları getir” demek

📌 Örnek:

```
/api/users
```

---

# 🔹 Yazılım Prensipleri

### DRY

Aynı kodu tekrar yazma.
👉 DRY = Don’t Repeat Yourself (Kendini tekrar etme)

🧠 Ne demek?

Aynı kodu, aynı mantığı tekrar tekrar yazma.
Bir kere yaz, her yerde kullan.

---

### Clean Code

Okunabilir ve düzenli kod yaz.
📦 Kötü vs Temiz kod
❌ Kötü kod
int a = 10;
int b = 20;
int c = a + b;

👉 Ne olduğu anlaşılmıyor

✅ Clean Code
int firstNumber = 10;
int secondNumber = 20;

int sum = firstNumber + secondNumber;

👉 Değişkenler neyi temsil ettiği belli

---

# 🔹 Veri Yapıları
###⚖️ Dictionary vs List
List:
Sadece sıralı veri
İndeks ile erişilir (0,1,2)
Dictionary:
Anahtarla erişilir
Daha hızlı arama




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

# burada bunu yazmamızın sebebi nedir?

Bu repo, temel yazılım kavramlarını **karmaşıklaştırmadan öğretmek** için hazırlanmıştır.

---

