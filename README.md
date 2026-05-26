# Packet-Tracer-da-2-Şubeli-Network-Topoloji-İnşası


### Proje Amacı

<img width="1287" height="676" alt="Screenshot 2026-05-24 021136" src="https://github.com/user-attachments/assets/07f2c130-823f-415a-b8d1-98573d49eab2" />


Bu projenin amacı, İstanbul (Merkez/HQ) ve Ankara (Şube) olmak üzere iki lokasyonda hizmet veren özel bir hastane zinciri için Cisco Packet Tracer ortamında yedekli, güvenli, ölçeklenebilir ve hiyerarşik bir ağ topolojisi tasarlamaktır. 

Hastanenin operasyonel sürekliliğini sağlamak adına çift ISP bağlantılı ve çift Core Router mimarili yedekli bir omurga kurulması hedeflenmiştir. Tıbbi cihazların, hasta kayıt süreçlerinin, yönetimsel verilerin güvenliğini sağlamak ve misafir ağını izole etmek amacıyla departman tabanlı VLAN segmentasyonu uygulanacaktır. Merkez şubede konumlandırılacak sunucular (DNS, DHCP, Web, Email) aracılığıyla tüm ağın temel servis altyapısı merkezi olarak yönetilecektir.

---

### Sistem Bileşenleri Tablosu

| Kategoriler | Ağ Bileşeni / Teknoloji | Açıklama / Görevi |
| :--- | :--- | :--- |
| **Ağ Donanımları** | **HQ Router (Merkez)** | İstanbul şubesinin ana çıkış kapısı ve sunucu bloğunun bağlı olduğu router. |
| | **Branch Router (Şube)** | Ankara şubesinin dış dünya ve merkez ile iletişimini sağlayan router. |
| | **Core Routers (Çift)** | Hiyerarşik modelde ağın merkez omurgasını oluşturan, ISP yedekliliğini yöneten router cihazları. |
| | **Layer 3 Switch (Multilayer)** | VLAN'lar arası yönlendirme (Inter-VLAN Routing) ve omurga anahtarlama işlemleri için. |
| | **Layer 2 Edge Switches** | Departmanlardaki son kullanıcı cihazlarını ağa bağlayan kenar anahtarlayıcılar. |
| | **Access Points (WAP)** | Misafir bekleme alanları ve personel için kablosuz ağ erişim noktaları. |
| **Merkezi Sunucular (HQ)** | **DHCP Server** | Tüm departmanlara ve şubeye dinamik IP adresi dağıtan servis. |
| | **DNS Server** | Ağ içi ve dışı isim-IP çözümlemesini gerçekleştiren servis. |
| | **HTTP/WEB Server** | Hastane içi web otomasyonu veya dış web sitesi simülasyonu. |
| | **Email Server** | Personel arası kurumsal e-posta iletişim altyapısı. |
| **İstanbul Departmanları (VLAN)** | **Poliklinikler** | Doktor odaları ve tıbbi muayene bilgisayarları ağı. |
| | **Laboratuvar** | Tetkik ve tahlil cihazlarının yer aldığı izole ağ. |
| | **Medikal Cihazlar** | Kritik tıbbi donanımların ve monitörlerin bağlı olduğu güvenli ağ. |
| | **Yönetim / Finans** | Hastane yönetimi ve muhasebe birimlerinin kritik veri ağı. |
| | **IT (Bilgi İşlem)** | Ağ yönetimi ve teknik personelin yer aldığı yetkili ağ. |
| | **Hasta Kayıt** | Giriş ve kabul işlemlerinin yapıldığı sekreterya ağı. |
| | **Misafir Bekleme Alanı** | Hastane iç ağından tamamen izole edilmiş internet erişim ağı (Wi-Fi). |
| **Ankara Departmanları (VLAN)** | **Poliklinikler** | Ankara şubesi muayene alanı ağı. |
| | **Laboratuvar** | Ankara şubesi tetkik üniteleri ağı. |
| | **Medikal Cihazlar** | Şubedeki tıbbi cihazların yer aldığı güvenli ağ. |
| | **Yönetim (Küçük)** | Şube yönetim birimi ağı. |
| | **Hasta Kayıt** | Şube hasta kabul ve kayıt ağı. |
| | **Misafir Bekleme Alanı** | Şube misafir izole internet ağı. |
| **Altyapı & Protokoller** | **Redundant ISP Connection** | İki ayrı internet servis sağlayıcı ile kesintisiz internet bağlantısı. |
| | **VLAN Trunking (802.1Q)** | Switchler arası VLAN taşınması ve hat optimizasyonu. |
| | **WAN Teknolojileri** | İstanbul ve Ankara şubelerini güvenli şekilde birbirine bağlayan hat altyapısı. |



### Gereksinimler

* Cisco Packet Tracer kullanarak ağ çözümünü tasarlanıp ve uygulayın.
* Ağda yedeklilik sağlayan hiyerarşik bir model kullanın. Hem Merkez (HQ) hem de Şube (Branch) yönlendiricilerinin seri bağlantı ile bağlanması beklenmektedir.
* Daha önce belirtildiği gibi, network maliyeti için her sitede bir adet core router iki adet multilayer switch ve her departmanı bağlayan access switch bulunması beklenmektedir.
* Her departmanın kullanıcılar için bir wireless network olması gerekmektedir.
* Merkezde (HQ) her departmanda yaklaşık 40-60 kullanıcı, şubede (Branch) ise yaklaşık 20-30 kullanıcı olduğu varsayılmaktadır.
* Her departman farklı bir VLAN’da ve farklı bir alt ağda (subnetwork) yer almalıdır.
* 192.168.100.0 temel ağı verilmiştir; her departmana doğru sayıda IP adresi tahsis edebilmek için subnetting işlemini gerçekleştirin.
* Hastane ağı, iki internet servis sağlayıcısına bağlı olan statik, genel IP adreslerine  sahiptir.
* Hostname ayarları, konsol parolası, enable parolası, banner mesajları gibi temel cihaz ayarlarını yapılandırın ve IP domain lookup özelliğini devre dışı bırakın.
* Tüm departmanlardaki cihazların inter-VLAN routing yapılandırılmış ilgili çok katmanlı anahtar üzerinden birbirleriyle haberleşmesi gerekmektedir.
* Multilayer anahtarların hem yönlendirme hem de anahtarlama işlevlerini yerine getirmesi beklenmektedir; bu nedenle IP adresleri atanacaktır.
* Ağdaki tüm cihazların, sunucu odasında bulunan özel DHCP sunucularından dinamik olarak IP adresi alması beklenmektedir.
* Sunucu odasındaki cihazlara statik IP adresleri atanacaktır.
* Hem routerlar da hem de multilayer anahtarlarda yönlendirme protokolü olarak OSPF kullanarak rotaları duyurun.
* Yönlendirme tablosundaki hiçbir kayıtla eşleşmeyen trafiğin routerlar ve multilayer anahtarlar tarafından iletilebilmesi için default static route yapılandırın.
* Uzaktan erişim için tüm yönlendiricilerde ve katman 3 anahtarlarda SSH yapılandırın.
* Sunucu departmanındaki access switch için port-security yapılandırın: bir switch portuna yalnızca bir cihazın bağlanmasına izin verin, MAC adresini sticky yöntemiyle öğrenin ve ihlal (violation) modu olarak shutdown kullanın.
* İlgili çıkış yönlendirici arayüzünün IPv4 adresini kullanacak şekilde PAT yapılandırın ve gerekli ACL kuralını uygulayın.
* İletişimi test edin ve yapılandırılan her şeyin beklendiği gibi çalıştığından emin olun.



### Konfigürasyon Adımları;

1. Network dizaynı oluşturulacak
2. Tüm cihazlara temel ayarlar ve routerlara ve katman 3 switche SSH yapılandırılacak.
3. Tüm switchlere access ve katman 3 de dahil vlan ataması ve trunk port yapılandırılacak.
4. Server tarafına swicthport security yapılandırılacak
5. Subnetting ve ıp adresleme
6. Tüm routerlara ve 13 swicthe ospf yapılandırılacak
7. Server cihazlarına static ıp verilecek
8. DHCP server yapılandırılacak
9. Inter-VLAN routing yapılandırılacak ve ip dhcp helper adresleme yapılandırılacak
10. Wireless network yapılandırılacak
11. PAT ve ACL yapılandırılacak


### 1) Network Dizaynı oluşturuldu. Bütün bağlantılar yapıldı.

<img width="1327" height="661" alt="image" src="https://github.com/user-attachments/assets/50ba0c2d-1e52-417f-a77d-969ec7951318" />


### 2) Switchlere user ve global konfigürasyonlara parola koyma ve ssh yapılandırılma

```bash
enable 
conf t
hostname POL-SW
enable password taskiran
banner motd #!!!Yetkisiz Kişiler Giremez!!!#
no ip domain lookup
line console 0
password taskiran
login
exit
service password-encrytion
```
#### Parola ve Banner Ekleme

* **enable secret taskiran:** Komutu ile global konfigürasyona girişte parola koyuldu.
* **banner motd:** Komutu ile banner yazıldı. 
* **line console 0:** Komutu konsol bağlantısı yapıldığında parola koyuldu.
* **no ip domain lookup:** Yanlış komut girildiğinde cihazın DNS sunucusuna isim sorgusu göndermesini engelleyen bir komut.
* **service password-encrytion:** running-config de clear-text olarak görünen tüm şifreleri şifrelenmiş bir formata dönüştürür.
* Bu komutlar ile sadece bütün access switchlere parola koyuldu sadece hostname değiştirilerek komutlara kopyala yapıştır yapıldı.
* Multilayer swithlere de aynı işlemi yapıyoruz bir de ssh ekliyoruz


#### SSH yapılandırılması:

```bash
ip domain-name taskiran.com
username admin password taskiran
crypto key generate rsa
1024 
line vty 0 4
login local
transport input ssh
exit

do wri
```

* **ip domain-name taskiran.com:** SSH için bir şifreleme anahtarı (key) oluşturmadan önce cihazın bir domain adına ihtiyacı vardır. Bu komutla cihaza bir kimlik alanı tanımlarsın.
* **username admin password taskiran:** Cihaza uzaktan bağlanacak kişi için yerel bir kullanıcı adı ve şifre oluşturur.
* **crypto key generate rsa:** Şifreleme için kullanılacak olan RSA anahtar çiftini oluşturur.
* **1024:** RSA anahtarının uzunluğunu bit cinsinden belirler. 
* **line vty 0 4:** Cihazın aynı anda 5 farklı uzak bağlantı (0'dan 4'e kadar hat) kabul edebileceğini belirtir.
* **login local:** Cihaza bağlanmaya çalışan kişiye "Seni tanımam için cihazın üzerinde tanımlı olan kullanıcı listesine (az önce oluşturduğumuz admin kullanıcısı gibi) bak" der.
* **transport input ssh:** Bu hatta sadece SSH bağlantısına izin verir. Telnet gibi diğer protokolleri kapattığı için güvenliği maksimize eder.

Bütün multilayer switchlere ve routerlara aynı komutları yazıldı sadece hostnameler değiştirildi.

### 3) Vlanları oluşturma,portlara vlanlari atama Multilayer switch ile access switch arası trunk yapılandırma

#### Vlan Nedir?

Bir fiziksel switch üzerindeki ağ portlarını mantıksal olarak küçük parçalara bölerek birbirinden tamamen bağımsız sanal ağlar oluşturma teknolojisidir. Amaç güvenliği artırmak.


#### Vlan Oluşturma ve Portlara Atama

```bash
Vlan oluşturma;
	vlan 10	
	name Poliklinik
```
Önce vlan sayısı yazılır ve ardından da vlanımıza isim verilir vlan oluşturma bu şekildedir.

```bash
	Acces Switchlere Vlan Atama;
	int range fa0/3-24
	switchport mode access
	swicthport access vlan 10

```

* **int range fa0/3-24:**
Switch üzerindeki FastEthernet 0/3 ile FastEthernet 0/24 arasındaki tüm portları (toplam 22 adet portu) tek seferde topluca seçmeyi sağlar.

* **switchport mode access:**
Seçilen bu portların çalışma modunu "Access (Erişim)" olarak belirler. Access portlar, sadece tek bir VLAN'a ait trafiği taşır ve bilgisayar, yazıcı, IP telefon veya sunucu gibi doğrudan son kullanıcı cihazlarının (end cihazlar) bağlanacağı portlar için kullanılır.

* **switchport access vlan 10:***
Seçilen ve access moduna alınan bu portların tamamını doğrudan VLAN 10 ağına üye yapar ve bağlar. Bu adımdan sonra, bu portlara takılan tüm cihazlar artık mantıksal olarak sadece VLAN 10 ağının birer parçası haline gelir.

#### Trunk Nedir?
Birden fazla VLAN'a ait ağ trafiğinin, tek bir fiziksel hat üzerinden switchler veya routerlar arasında taşınmasını sağlayan bağlantı türüdür. Amaç Her VLAN için switchler arasına ayrı ayrı kablo çekme maliyetini ortadan kaldırır. Trunk hattından geçen her veri paketine 802.1Q adı verilen bir protokol ile "bu veri VLAN 10'a aittir" veya "bu veri VLAN 20'ye aittir" şeklinde bir etiket (tag) eklenir. Karşıdaki switch bu etikete bakarak veriyi doğru VLAN'a ulaştırır. 

```bash
 Trunk oluşturma;
	int range fa0/1-2
	swicthport mode trunk
```
* **switchport mode trunk:***
Seçilen bu portların çalışma modunu "Trunk" olarak belirler. Bu komutla birlikte, bu portlar üzerinden artık sadece tek bir departmanın değil, ağdaki tüm VLAN'ların (VLAN 10, VLAN 20, vb.) trafiğinin tek bir kablo üzerinden etiketlenerek (802.1Q) taşınması sağlanır. Switch'ler arası veya switch-router arası bağlantılarda kullanılır.


<img width="497" height="282" alt="image" src="https://github.com/user-attachments/assets/cc43864c-4531-4e07-a76b-f82fe7adafe4" />

Topoloji de bu şekilde vlan oluşturuldu, switch ve router arasu trunk yapılandırıldı ve son kullanıcılara bakan tarafa vlanlar portlara atandı.Bu sadece merkez tarafındaki lab swithte yapılandırıldı diğer switchler de aynı bu şekilde yapılandırılır sadece isimleri ve vlan sayıları değiştirilir.


<img width="577" height="266" alt="image" src="https://github.com/user-attachments/assets/da65789c-c4dc-4bc1-ad68-6836c28a2a3c" />

Multilayer switchlere de vlanlar oluşuturulup trunk bağlantısı yapılandırılmıştır. Diğer merkez multilayer switchte de aynısı yapılandırıldı. Şube tarafındaki multilayer switchlere de aynı şekilde yapılandırıldı oradaki vlan 90-140 arası trunk yapıldı.

### 4) Ip subnetting Planlama

Networkümüz **192.168.100.0** bunu gereksinimlere göre böleceğiz.

* Merkez tarafında en az 60 kullanıcı olacak o yüzden /26 subnet mask kullanıldı.(2^6=64)
* Şube tarafında en az 30 kullanıcı olacak o yüzden /27 subnet mask kullanıldı.(2^5=32)
* Router-Router arası point to point olduğu /30 subnet mask kullanılır.
* Router- l3-Switch de aynı şekilde /30 subnet mask kullanılır.


#### İstanbul(Merkez) Hastanesi

Merkez tarafındaki ip planlaması aşağıdaki gibidir. 60 kullanıcılı olarak /27 subnetmask kullanılmıştır.

| Departmanlar | Network Adresleri | Subnet Mask | Host Adres Aralığı | Broadcast Adresleri |
| :--- | :--- | :--- | :--- | :--- |
| Poliklinik | 192.168.100.0 | 255.255.255.192/26 | 192.168.100.1-<br>192.168.100.62 | 192.168.100.63 |
| Laboratuvar | 192.168.100.64 | 255.255.255.192/26 | 192.168.100.64-<br>192.168.100.126 | 192.168.100.127 |
| Medikal Cİhazlar | 192.168.100.128 | 255.255.255.192/26 | 192.168.100.129-<br>192.168.100.190 | 192.168.100.191 |
| Yönetim/Finans | 192.168.100.192 | 255.255.255.192/26 | 192.168.100.193-<br>192.168.100.254 | 192.168.100.255 |
| IT | 192.168.101.0 | 255.255.255.192/26 | 192.168.101.1-<br>192.168.101.62 | 192.168.101.63 |
| Hasta Kayıt | 192.168.101.64 | 255.255.255.192/26 | 192.168.101.64-<br>192.168.101.126 | 192.168.101.127 |
| Misafir Bekleme Alanı | 192.168.101.128 | 255.255.255.192/26 | 192.168.101.129-<br>192.168.101.190 | 192.168.101.191 |


 #### Ankara(Şube) Hastanesi
 
Şube tarafı ip planlaması aşağıdaki gibidir. 30 kullanıcılı olarak /26 subnetmask kullanılmıştır.

| Departmanlar | Network Adresleri | Subnet Mask | Host Adres Aralığı | Broadcast Adresleri |
| :--- | :--- | :--- | :--- | :--- |
| Poliklinik(Ank) | 192.168.101.192 | 255.255.255.224/27 | 192.168.101.193-<br>192.168.101.222 | 192.168.101.223 |
| Laboratuvar(ank) | 192.168.101.224 | 255.255.255.224/27 | 192.168.101.225-<br>192.168.101.254 | 192.168.101.255 |
| Medikal Cİhazlar(ank) | 192.168.102.0 | 255.255.255.224/27 | 192.168.102.1-<br>192.168.102.30 | 192.168.102.31 |
| Yönetim(ank) | 192.168.102.32 | 255.255.255.224/27 | 192.168.102.33-<br>192.168.102.62 | 192.168.102.63 |
| Hasta Kayıt(ank) | 192.168.102.64 | 255.255.255.224/27 | 192.168.102.65-<br>192.168.102.94 | 192.168.102.95 |
| Misafir Bekleme Alanı(ank) | 192.168.102.96 | 255.255.255.224/27 | 192.168.102.97-<br>192.168.102.126 | 192.168.102.127 |


 #### Server Tarafı 
 
Server tarafı ip planlaması

| Departmanlar | Network Adresleri | Subnet Mask | Host Adres Aralığı | Broadcast Adresleri |
| :--- | :--- | :--- | :--- | :--- |
| Server | 192.168.102.128 | 255.255.255.240/28 | 192.168.102.129-<br>192.168.102.142 | 192.168.102.143 |



#### Router ve Layer-3 Sw Arası

|  |  Networkler|
| :--- | :--- |
| Merkez Router1 – Şube Router1 | 192.168.102.160/30 |
| Merkez Router1 – Merkez Router2 | 192.168.102.164/30 |
| Merkez Router2 – Şube Router2 | 192.168.102.168/30 |
| Şube Router2 – Şube Router1 | 192.168.102.172/30 |


#### ISP'ler ve Routerlar Arası


|  | Networkler |
| :--- | :--- |
| ISP1 – Merkez Router1 | 80.0.1.0/30 |
| ISP1 -  Şube Router1 | 80.0.1.4/30 |
| ISP2 -  Merkez Router1 | 90.0.1.0/30 |
| ISP2 -  Şube Router1 | 90.0.1.4/30 |



<img width="1346" height="661" alt="image" src="https://github.com/user-attachments/assets/77400fbd-f513-43d9-b3e9-d79afea8c57e" />

Networkler subnet maskları ile birlikte network dizayna eklendi son görüntü bu şekilde.


### 5)  İp Atama Yapılandırmaları

* **L3 Switchlere ip Atama**
L3 Switch ve router arası portlara ip ataması aşağıdaki gibi yapılır.

<img width="795" height="258" alt="image" src="https://github.com/user-attachments/assets/d555eca1-3c41-443b-b8d9-4199f888f4c2" />


L3 switchin portunu girdikten sonra “no swicthport” dedikten sonra ip adresi atayabiliriz. Switch artık bu porttan routing yapabilir vlan gerekmez.  Geriye kalan L3 switchlere de bu komutları yazar ve ip adresi atayabiliriz. 


* **Router Ip atamaları**

<img width="659" height="79" alt="image" src="https://github.com/user-attachments/assets/9847cfe5-7f0a-49c6-8c21-abf96e2a515a" />

Routerların bütün interfacelerine  sadece interface ve ip adreslerini değiştirerek ip ataması yapılmıştır.
















