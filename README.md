SQL Veri Tabanlı ToDoList (Günlük Planlama) – Kurulum ve Yapılandırma

## Teknolojiler

| Teknoloji | Açıklama |
|---|---|
| **Backend** | ASP.NET Core 8.0 |
| **Veritabanı** | Microsoft SQL Server (MS SQL) |
| **ORM** | Entity Framework Core (kullanılıyorsa) |

## Kurulum ve Çalıştırma

Projeyi çalıştırmadan önce aşağıdaki kurulum adımlarını sırasıyla tamamlayın.

### 1. Veritabanı Yedeğini Yükleme

- Proje içerisinde bulunan veritabanı yedek dosyasını (`.bak`) kendi bilgisayarınıza indirin.
- SQL Server Management Studio (SSMS) uygulamasını açın.
- SQL Server sunucunuza bağlanın.
- Veritabanı yedeğini kullanarak `DB_ToDoList` isimli veritabanını geri yükleyin.

**Önemli:** Veritabanının başarıyla geri yüklendiğinden ve SQL Server üzerinde erişilebilir olduğundan emin olun.

### 2. Bağlantı Dizesini Yapılandırma

Projenin kök dizininde bulunan `appsettings.json` dosyasını açın.

`ConnectionStrings` bölümündeki `DefaultConnection` değerini kendi SQL Server bağlantı bilgilerinize göre güncelleyin.

Örnek bağlantı dizesi:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=.\\SQLEXPRESS;Database=DB_ToDoList;User Id=sa;Password=YOUR_PASSWORD;TrustServerCertificate=True;"
  }
}
```

**Bağlantı dizesi parametreleri:**

| Parametre | Açıklama |
|---|---|
| `Server` | SQL Server sunucu adresi ve instance adı |
| `Database` | Kullanılacak veritabanının adı |
| `User Id` | SQL Server kullanıcı adı |
| `Password` | SQL Server kullanıcı parolası |
| `TrustServerCertificate` | Geliştirme ortamında sertifika doğrulamasını atlar |

> **Not:** Yukarıdaki bağlantı dizesi örnek olarak verilmiştir. SQL Server kurulumunuza göre sunucu adresini ve kimlik doğrulama bilgilerini güncellemeniz gerekir.

### 3. Projeyi Derleme ve Çalıştırma

Veritabanı ve bağlantı yapılandırmasını tamamladıktan sonra projeyi Visual Studio üzerinden açın.

1. Projenin NuGet paketlerinin geri yüklendiğinden emin olun.
2. `appsettings.json` dosyasındaki bağlantı bilgilerini kontrol edin.
3. Projeyi derleyin (**Build**).
4. Herhangi bir derleme hatası bulunmuyorsa projeyi çalıştırın (**Run**).

## Gereksinimler

- .NET 8.0 SDK
- Microsoft SQL Server
- SQL Server Management Studio (SSMS)
- Visual Studio 2022 veya uyumlu bir geliştirme ortamı

## Önemli Güvenlik Notları

- Gerçek SQL Server parolanızı GitHub üzerinde herkese açık olarak paylaşmayın.
- Üretim ortamında bağlantı bilgilerini `appsettings.json` yerine Environment Variables veya .NET User Secrets üzerinden yönetin.
- `TrustServerCertificate=True` ayarını üretim ortamında bilinçsizce kullanmayın.
- Veritabanı bağlantısı için mümkünse `sa` hesabı yerine yalnızca gerekli yetkilere sahip ayrı bir SQL Server kullanıcısı tercih edin.

---

**Proje Altyapısı:** ASP.NET Core 8.0 Web Uygulaması  
**Veritabanı:** Microsoft SQL Server (MS SQL)