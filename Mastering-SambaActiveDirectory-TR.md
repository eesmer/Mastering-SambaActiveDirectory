## İçindekiler

- [Önsöz](#%C3%B6nsöz)
- [Teşekkür](#te%C5%9Fekkür)
- [Belgenin Yapısı ve Kullanımı](#Belgenin-Yapısı-ve-Kullanımı)
- [Giriş](#Giri%C5%9F)
- [Active Directory Nedir?](#Active-Directory-Nedir)

## Önsöz
Samba yazılım paketi ile kurulan SambaAD, Microsoft Active Directory hizmetlerini sunmak üzere geliştirilen ve  GPLv3 lisansı ile dağıtılan bir açık kaynak yazılımdır. <br>
SambaAD, bir Etki Alanı ve Active Directory ortamının kurulması ve yönetilmesini sağlar. <br>
<br>
1991 yılında Windows ve UNIX/Linux ortamlarının birlikte çalışmaya olanak sağlaması hedefiyle geliştirilmeye başlanan Samba yazılımı projesi; <br>
Samba1 ile LANManager ve Workgroup ortamlarına uyum sağladı. <br>
Samba2 ile Windows istemciler için NT4-Style Domain Controller hizmetlerini sağladı. <br>
Samba3 ile dosya ve yazıcı paylaşımlarının yönetimi ve FileServer hizmetini sağladı. <br>
Ve Samba4 ile bir Domain ve Active Directory ortamı kurulum ve yönetim hizmeti sağladı. <br>
Adını dosya ve yazıcı paylaşım protokolü SMB’den alan Samba, Andrew Triggel ve Samba Team ekibinin eşsiz çalışmalarıyla bizim için harika bir araç olmuştur. <br>
<br>
Ve bugün büyük üretim ortamlarında Domain ve Active Directory ortamının kurulumu ve yönetimi için kullanabileceğimiz mükemmel bir seçeneğimiz var. <br>
<br>
**Paradigma Değişikliğine Dair** <br>
Bu çalışma konusunda paradigma örneği ne kadar uygun olur, bilmiyorum. <br>
Paradigma, bir alandaki geçerli modeli ifade ediyorsa eğer Samba yazılımı, alternatif sunduğu çözüm için tipik bir paradigma değiştiricisidir. <br>
Paradigma değişimi, tarihte ve bilimde her zaman olumlu değişimleri örneklemiştir. <br>
Geçerli modele fazlasıyla bağlılık, yeni modeli kabul edip geçmeye engel oluşturabilir. <br> 
Ne öğrenmeye ve gelişime engel olan paradigma felcine ne de bu konu için paradigma değişimi örneğinin uygun olup olmadığına bakmaksızın günümüzde IT dünyasındaki açık kaynak alternatiflerin gücüne ve bize kattıklarına odaklanarak; <br>
bunları anlama eğilimi ile bu çalışmayı değerlendirebilirsiniz.. <br>
O zaman başlayabiliriz.. <br>
<br>
Bu çalışma; <br>
Active Directory kavramlarına temel olarak değinecek olsa da asıl amaç; <br>
Üretim ortamı senaryoları ile kurulum, yapılandırma, bakım ve problem giderme gereksinimleri için SambaAD incelemesi ve pratik çalışmalarını yapmaktır. <br>
Bu çalışma ile baştan Active Directory öğrenme ve Samba ile Active Directory ortamını kullanmayı tüm yönleriyle elde edeceksiniz. <br>
<br>
#### Teşekkür
Bu çalışmada bu satırları yazmazsak olmaz. <br>
Özellikle Samba proje ekibi ve Andrew Triggel’e böylesine harika bir çalışma için çok teşekkürler.. <br>
Samba4 çok büyük bir iş ve büyük bir başarıdır. <br>
Bu çalışmadaki amaç; Samba kullanıcılarına ve tanıyıp kullanmak isteyenlere doküman ve düzenli çalışma notları verebilmektir. <br>

#### Belgenin Yapısı ve Kullanımı
Bu çalışma, bu repoda elektronik olarak tutulacaktır. <br>
Türkçe, İngilizce ve indirilebilir PDF dosyası formatları da buradan erişilebilir olacaktır. <br>
<br>
Yapılan çalışmalar buradan güncellenecektir. <br>
<br>
**Güncelleme:** 28 Eylül 2024

---
<br>

## Giriş
Bu bölümde temel olarak Active Directory ve kavramlarından bahsedeceğiz. <br>
Bu bölüm ile AD ve AD ortamı hakkında detaylı bilgi sahibi olacağız.

<br>

## Active Directory Nedir?
Active Directory, ağ kullanıcıları için kaynak dizini görevi gören bir dizin hizmetidir. <br>
Bu dizin hizmeti ile bir veritabanında kullanıcılar, bilgisayarlar, yazıcılar gibi organizasyonun tüm bilgileri saklanır. <br>
Organizasyondaki tüm bileşenlere (bu esasında bir kimliktir) yönetimsel kısıtlamalar oluşturulabilir ve ihtiyaçlar doğrultusunda kurallar işletilebilir.
Active Directory, bir DC makinesi kurularak çalıştırılır. <br>
<br>
Bir kullanıcı hesabı, domain ortamındaki bir bilgisayarda oturum açtığında; <br>
Active Directory, girilen kullanıcı adı ve parolayı kontrol eder. <br>
Oturum açabilen bir giriş bilgisi sağlandıysa AD politikaları ile yetkilendirilir ve aldığı yetkiye göre ağ kaynaklarına erişim sağlar. <br>
<br>
Active Directory ilk olarak Windows 2000 Server ile yayınladı. <br>
Windows 2003 sürümünde önemli revizeler ile geliştirildi. <br>
Windows 2008 ve sonraki sürümlerdeki geliştirmelerle bugünkü yeteneklerini aldı. <br>
Sonuç olarak; kimlikle ilgili her iş, AD altında toplandı ve yönetildi. <br>
<br>
[wikipedia.org/Active Directory](https://en.wikipedia.org/wiki/Active_Directory)

## Active Directory Kavramları
Active Directory (AD) veya Samba Active Directory ortamlarında, temel kavramların anlaşılması ortamın genel yapısının kavranması için oldukça önemlidir. <br>
<br>
**Forest** <br>
Forest, Active Directory ortamının en üst düzeydeki mantıksal yapısıdır. <br>
Bir forest, birden fazla Domain içerebilir ve bunlar birbirine güven ilişkisi (trust) ile bağlıdır. <br>
Forest içindeki tüm domain ortamları, ortak bir Global Catalog ve Schema paylaşır. <br>
<br>
**Schema** <br>
Schema, Forset düzeyinde paylaşılan ve tüm Domain ortamlarında kullanılan nesne türlerini ve bunların özelliklerini tanımlar. <br>
<br>
**Global Catalog** <br>
Forest içindeki tüm Domain ortamı nesnelerin bir kopyasını içerir ve arama yapıldığında hızlı erişim sağlar. <br>
<br>
**Site** <br>
Site, bir Active Directory ortamındaki fiziksel ağ yapısını ifade eden bir kavramdır. <br>
Genellikle, farklı coğrafi konumlara sahip olan ağlar, birer Site olarak tanımlanır. <br>
**Site Link:** Her bir Site arasındaki replikasyon trafiği için bağlantı kurma aracıdır. <br>
<br>
