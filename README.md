
# FinFlex

FinFlex kurumsal bir döviz alım-satım uygulamasıdır. Arka taraf uygulaması Spring Boot frameworkünde Java diliyle yazılmıştır. Verileri saklamak için Microsoft SQL Server kullanılmıştır.
Ön taraf uygulamasında React,JS frameworkünde   JavaScript dili kullanılarak yazılmıştır.
Ayrıca Material UI ve Ant Design'dan yararlanılmıştır.


## Bilgisayarınızda Çalıştırın

 Projeyi klonlayın

```bash
git clone https://github.com/arshmed/finflex.git
```

Microsoft SQL Server Kurulumu ve Veritabanı Konfigürasyonu

1. SQL Server'ı Yerel Olarak Ayağa Kaldırma  
   Uygulamanızda Microsoft SQL Server kullanılmaktadır. SQL Server'ı kendi bilgisayarınızda yerel olarak ayağa kaldırmak için aşağıdaki adımları takip edin:

    1. SQL Server Yükleme: SQL Server'ın ilgili sürümünü Microsoft'un resmi sitesinden indirip yükleyin.
    2. SQL Server Management Studio (SSMS) Yükleme: SSMS'yi kullanarak SQL Server'ı yönetebilirsiniz.
2. SSMS Kullanarak Veritabanı Oluşturma  
   SSMS'yi Başlatın ve sunucuya bağlanın:

Server name: (local) veya localhost  
Authentication: SQL Server Authentication  
Login: SA
Password: Kurulum sırasında belirlediğiniz şifre.  
Sol menüde Databases üzerine sağ tıklayın ve New Database seçeneğini seçin.

Açılan pencerede Database name alanına finflex yazın ve OK butonuna tıklayın.

Bu adımla finflex veritabanı oluşturulmuş olacaktır.

3. Uygulama Yapılandırması  
   Veritabanınızı oluşturduktan sonra, uygulamanızın veritabanına bağlanabilmesi için application.yml dosyasındaki konfigürasyonu aşağıdaki gibi düzenleyin:

```yaml
   spring:
    datasource:
    url: jdbc:sqlserver://localhost:1433;databaseName=finflex;Encrypt=False;
    username: Kullanıcı Adınız
    password: Şifreniz
    driver-class-name: com.microsoft.sqlserver.jdbc.SQLServerDriver
```

4. Her Servis İçin Ayrı Konfigürasyon  
   Uygulamanızda bulunan üç farklı servis için de aynı veritabanı konfigürasyonunu yapmalısınız. Farklı bir port veya kullanıcı adı/şifre kullanıyorsanız, ilgili alanları buna göre güncellemelisiniz:

Port Değişikliği: Eğer SQL Server'ı varsayılan 1433 portu yerine başka bir portta çalıştırıyorsanız, url kısmındaki port numarasını değiştirin.  
Kullanıcı Adı ve Şifre: SQL Server kurulumunda oluşturduğunuz kullanıcı adı ve şifreyi username ve password alanlarına yazın.

Kafka Konfigürasyonu

```bash
$ cd FinFlex
$ cd Kafka
$ docker-compose up -d
```

İstemci için gerekli paketleri yükleyin

```bash
$ cd FinFlex-fe
$ npm install
```

İstemciyi çalıştırın

```bash
npm start
```

  
## Kullanılan Teknolojiler

**İstemci:** React

**Sunucu:** Spring Boot

**Messaging Queue:** Apache Kafka

**Veritabanı:** Microsoft SQL Server

  
## Ortam Değişkenleri

**Windows için**

Açık verilerimizin saklanması için environment variables kullanıyoruz. Bunun için öncelikle "Sistem ortam değişkenlerini düzenleyin" aratıp tıklayın.

Ortam Değişkenleri  butonuna tıklayın karşınıza çıkan sayfada Sistem Değişkenleri tablosunun altındaki Yeni butonuna basınız

Sonrasında karşımıza gelen ekranda bu bilgileri ekleyip tamam tuşuna basıyoruz. Artık url imiz enviroment variablesta tutuluyor olacak.
```bash
Değişken Adı: RATES_URL
Değişken Değeri: https://v6.exchangerate-api.com/v6/{API_KEY}/pair/
```

**MacOS**

**For macOS Catalina (10.15) or newer (zsh is the default shell)** 

Terminale giriş yapın aşağıdaki komutu çalıştırın

```zsh
$ nano ~/.zshrc
```
Bu kodu dosyaya yapıştırın 
```zsh
$ export RATES_URL="https://v6.exchangerate-api.com/v6/{API_KEY}/pair/"
```
Sonrasında dosyayı kaydetmek için CTRL+X ve ardından Y tuşlarına basın ve Enter'a basın.

Daha sonra terminali yenilemek için aşağıdaki komutu çalıştırın

```zsh
$ source ~/.zshrc
```
Aşağıdaki komutu çalıştırarak ortam değişkenini ekrana basarak kontrol edebilirsiniz

```zsh
$ echo $RATES_URL
```

**For macOS Mojave (10.14) or earlier (bash is the default shell)**

Terminale giriş yapın aşağıdaki komutu çalıştırın

```bash
$ nano ~/.bash_profile
```

Bu kodu dosyaya yapıştırın
```bash
$ export RATES_URL="https://v6.exchangerate-api.com/v6/{API_KEY}/pair/"
```

Sonrasında dosyayı kaydetmek için CTRL+X ve ardından Y tuşlarına basın ve Enter'a basın.

Daha sonra terminali yenilemek için aşağıdaki komutu çalıştırın

```bash
$ source ~/.bash_profile
```


## API Kullanımı

https://app.exchangerate-api.com/

  