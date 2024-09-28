## İçindekiler

- [Önsöz](#%C3%B6nsöz)
- [Teşekkür](#te%C5%9Fekkür)
- [Belgenin Yapısı ve Kullanımı](#Belgenin-Yapısı-ve-Kullanımı)
- [Giriş](#Giri%C5%9F)
- [Active Directory Nedir?](#Active-Directory-Nedir)
- [Active Directory Kavramları](#Active-Directory-Kavramları)

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
**Domain** <br>
Domain ortamından önce küçük bilgisayar gruplarından oluşan Workgroup ortamından bahsetmek gerekir. <br>
Workgroup ortamları aynı ağda bulunan birkaç bilgisayar gruplarından oluşan bir çalışma ağıdır. <br>
Workgroup içindeki bilgisayarlar arasında dosya ve yazıcı paylaşımları yapılır ve kaynakları ortak kullanabilirler. Fakat Workgroup ortamındaki bilgisayarlara merkezi bir politika uygulanmaz ve her kaynağın erişimi o kaynağı sunan workgroup üyesi bilgisayar tarafından yapılan ayarla bilgisayar üzerinde tutulur. <br>
<br>
Domain ortamı ise workgroup kavramından daha büyük bilgisayar ortamlarında kimin nereye bağlanacağı ve buna benzer politikaların merkezi olarak kontrol edilebildiği bir ortamdır. <br>

[wikipedia.org/Workgroup](https://en.wikipedia.org/wiki/Workgroup_(computer_networking)) <br>
[wikipedia.org/WindowsDomain](https://en.wikipedia.org/wiki/Windows_domain) <br>
<br>
**Domain Controller** <br>
Domain Controller, domain ortamının kurulduğu bilgisayardır. <br>
Domain Controller, Active Directory veritabanını barındırır ve bu veritabanı ile domain ortamını
kullanıcı, bilgisayar, grup ve diğer kaynakları yönetir. <br>
<br>
Domain Controller temel olarak aşağıdaki işleri yapar; <br>
            ▪ Kimlik Doğrulama <br>
            ▪ Yetkilendirme <br>
            ▪ Replikasyon <br>
            ▪ FSMO Rolleri <br>
            ▪ Grup Politika Yönetimi <br>
<br>

**Domain Join** <br>
Domain Join, bir bilgisayarın veya cihazın, Active Directory (AD) domain ortamına dahil edilmesi sürecidir. <br>
Join kavramı genel olarak üye olmayı ifade etmekte kullanılır. <br>
Yani domain ortamına yeni bir bileşeni üye yapma işleminde kulanılan bir kavramdır. <br>
<br>
Bir organizasyonda domain ortamından bahsetmemiz için ortamda en az bir tane Domain Controller bilgisayar olması gerekir. <br>
Organizasyondaki Domain Controller dışındaki bilgisayarlar Domain Controller tarafından çalıştırılan domain ortamına join olurlar. <br>
Böylece Domain Controller tarafından işletilen güvenlik kurallarına ve politikalara tabi olurlar. <br>
Domain Controller bilgisayar, join işlemini ve join olmuş bilgisayarın kaynaklara erişim ve domain ortamında çalışma ilkelerini yönetir. <br>
<br>
Örneğin domain ortamında bir dosya sunucusu ve paylaşımları olsun. <br>
Bu paylaşımlara erişmek isteyen bir domain üyesi bilgisayarın erişim talebi, dosya sunucusu tarafından Domain Controller bilgisayara sorulur ve Domain Controller bilgisayarın cevabına göre talep yanıtlanır.
<br>

**Domain Member** <br>
Bir domain ortamına join olmuş (katılmış) bir makineyi ifade eder. <br>
<br>

**Domain Users Account** <br>
Bir kullanıcı için AD'de tanımlanan ve ağ kaynaklarına erişim sağlayan hesaptır. <br>
Her kullanıcı hesabı, belirli izinler ve kimlik doğrulama bilgileri içerir. <br>
<br>
Kullanıcı hesapları, domain politikalarına göre üye cihazlardan kimlik doğrulama yapıp oturum açar ve kaynaklara erişim yetkileri alır.<br>

**Domain Groups, Organization OU (OU)** <br>
Bir domain ortamındaki kaynakları organize etmek için kullanılan objelerdir. <br>
Kullanıcı hesapları ve bilgisayarların üye oldukları, taşındıkları alanları ifade eder. <br>
OU nesneleri, yönetimsel amaçlarla kullanılır ve her bir OU’ya farklı politikalar ve izinler atanabilir. <br>
<br>
**Group Policy Object (GPO)** <br>
Domain içindeki bilgisayarlar ve kullanıcılar üzerinde politika uygulamak için kullanılan bir araçtır. <br>
GPO ile domain ortamına, kullanıcı ayarları, güvenlik politikaları ve bunun gibi yönetimsel görevler merkezi olarak uygulanır. <br>
<br>
**FSMO Roles (Flexible Single Master Operations Roles)** <br>
AD içinde bazı belirli görevlerin merkezi olarak yönetilmesi için atanmış olan rollerdir. <br>
Beş temel FSMO rolü vardır; <br>
Schema Master, Domain Naming Master, RID Master, PDC Emulator ve Infrastructure Master <br>
Bu roller, Forest ve Domain düzeyinde Domain Controller sunucular tarafından çalıştırılır.<br>
<br>
