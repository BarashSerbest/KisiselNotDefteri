Kişisel Not Defteri Uygulaması 
Bu proje, kullanıcıların notlarını güvenli bir şekilde yönetmelerine olanak tanıyan bir not defteri Uygulamasıdır. Kullanıcılar giriş yapabilir, 
not ekleyebilir, düzenleyebilir ve silebilir. Uygulama, farklı kullanıcı rolleri (admin ve user) için özelleştirilmiş özellikler sunar.

Özellikler
Kullanıcı Girişi: Kullanıcılar, hesaplarına giriş yaparak kişisel notlarına erişebilir.
Admin Paneli: Admin yetkisine sahip kullanıcılar, uygulamayı yönetmek için özel bir panele erişebilir.
Not Yönetimi: Kullanıcılar yeni notlar oluşturabilir, var olan notlarını düzenleyebilir veya silebilir.
Rol Tabanlı Yetkilendirme:
Admin: Yönetici yetkisine sahip kullanıcılar. Veritabanı yönetimi ve diğer kullanıcıları yönetme yetkisine sahiptir.
User: Standart kullanıcılar. Sadece kendi notlarını görebilir ve yönetebilir.
Observer Design Pattern: Kullanıcı rolleri değiştiğinde, ilgili gözlemciler anında bilgilendirilir.
MySQL Veritabanı Entegrasyonu: Tüm veriler bir MySQL veritabanında güvenli bir şekilde saklanır.

Kullanılan Teknolojiler
Programlama Dili: Java
GUI: Swing
Veritabanı: MySQL
Tasarım Desenleri:
Singleton
Observer
Strategy
Factory
State
IDE: IntelliJ IDEA veya NetBeans (isteğe bağlı)

Kurulum Adımları
Aşama 1)
git clone https://github.com/BarashSerbest/KisiselNotDefteri.git
cd KisiselNotDefteri
Aşama2)
Gerekli Bağımlılıkları İndirin: Projenin bağımlılıkları IDE'nizde yapılandırılmış olmalıdır. Gerekirse, harici kütüphaneleri manuel olarak ekleyin.
Aşama3) 
Veritabanını Yapılandırın:
Proje dosyası içerisinde yer alan "KisiselNotDefteriDB.sql" ile veritabanını oluşturabilirsiniz veya aşağıda yazdığım kod ile veritabanını oluşturunuz: 
CREATE DATABASE notdefteridb;
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(255) NOT NULL,
    password VARCHAR(255) NOT NULL,
    authority INT NOT NULL
);

CREATE TABLE notes (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    title VARCHAR(255) NOT NULL,
    content TEXT NOT NULL,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
Aşama 4) 
Veritabanı Bağlantısını Güncelleyin: MySQLConnection sınıfında url, username ve password bilgilerini kendi ortamınıza uygun şekilde güncelleyin:
private static final String URL = "jdbc:mysql://localhost:3306/notebook_app";
private static final String USER = "root";
private static final String PASSWORD = "password";
Aşama 5)
Projeyi Çalıştırın:
Uygulamayı IDE üzerinden başlatın.
Varsayılan bir kullanıcı veya admin oluşturun.

Kullanım
Giriş Yapın:
Kullanıcı hesabınızla giriş yapın veya yeni bir hesap oluşturun.
Admin yetkisine sahipseniz, "Admin Girişi" butonunu kullanarak giriş yapabilirsiniz.

Notlarınızı Yönetin:
Kullanıcı hesabınıza giriş yaptıktan sonra, yeni notlar ekleyebilir, var olan notları görüntüleyebilir ve düzenleyebilirsiniz.
Admin Panelini Kullanın:

Admin giriş yaptıktan sonra diğer kullanıcıları görebilir ve silebilir.

Geliştirme Planı
Testler: Uygulama için JUnit testleri eklenmesi.
Hata Yönetimi: Daha kapsamlı hata yönetimi mekanizmaları eklenmesi.
Yeni Özellikler: Kategori bazlı not yönetimi, paylaşım özellikleri, tema desteği ve grup sohbetleri oluşturulması.