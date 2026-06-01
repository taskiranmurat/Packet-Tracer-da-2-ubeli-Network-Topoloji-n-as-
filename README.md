# Packet Tracer da 2 Şubeli NetworkTopoloji İnşası


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
* Her departman farklı bir VLAN’da ve farklı bir alt ağda  yer almalıdır.
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
* HSRP yapılandırın.
* Etherchannel yapılandırın.
* STP ve Port Securty yapılandırılmalı.



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
12. HSRP yapılandırılacak
13. Etherchannel yapılandırılacak
14. STP ve Port Security yapılandırılacak ve STP ve HSRP aligment yapılandırılacak


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
Bu komutlar ile sadece bütün access switchlere parola koyuldu sadece hostname değiştirilerek komutlara kopyala yapıştır yapıldı.
 Multilayer swithlere de aynı işlemi yapıyoruz bir de ssh ekliyoruz


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


### 6)  OSPF Yapılandırmaları

#### OSPF Nedir?

Routerların ağdaki en kısa ve en uygun yolu bulmak için kullandığı bir dinamik yönlendirme protokolüdür. En iyi yolu belirlemek için cost (maliyet) değerini kullanır. Ağ değişikliklerine hızlı adapte olur.

Önce l3 swithcleri ospf yapılandırılması yapılandırılacak daha sonra routerlar yapılandırılacaktır.

#### L3 swithlere ospf yapılandırması

Merkezdeki L3 switchin access swithclere olan ospf yapılandırılmaları olacak. Yani 7 departman ve bir de routera olan bağlantısı var.

**Merkez Multilayer Switch1**

<img width="728" height="480" alt="image" src="https://github.com/user-attachments/assets/384d2931-5043-4c27-a619-75b50a46ca74" />


**ip routing:** Komutu ile cihazın IP paketlerini yönlendirmesi  sağlanmıştır.Bu ağları OSPF ile l3 switchte tanıttık l3 switch bu bilgileri merkez router1 e söyler bu sayede bu vlanlar başka ağlara ulaşabilir serverlara ulaşabilir ve internete çıkabilir. 

**router ospf 10:** Komutu çalıştırılarak OSPF yönlendirme süreci (Process ID: 10) yerel olarak başlatılmıştır.

**Ağ Adresi ve Wildcard Mask Eşleşmesi:** Ekrandaki 192.168.100.0 0.0.0.63 ifadesi, /26 subnet maskesine (255.255.255.192) sahip olan yerel alt ağı temsil eder. OSPF geleneksel subnet mask yerine Wildcard Mask  kullanır. Cihaz bu maske yardımıyla hangi interfacelerin OSPF paketleri göndereceğini ve hangi ağ segmentlerini dışarıya ilan edeceğini belirler.

**ip route**: “Ip route  0.0.0.0 0.0.0.0 192.168.102.146” komutu ile switchin bilmediği tüm adresler için gideceği son kapıyı belirlemek içindir. Bir kullanıcı ağda tanımlı olmayan bir ip'ye gitmeye çalıştığında switch “bu adresi tanımıyorum” diyerek çöpe atar işte burada default route devreye girer. Default route switchin bilmediği ip'yi merkez router1'e gönderir. Yapılmazsa departmanlar kendi aralarında konuşur inter-vlan routing ile ama merkez router1'in arkasına ulaşamaz.


<img width="788" height="178" alt="image" src="https://github.com/user-attachments/assets/09bd1032-b37e-4cea-9fa7-98dbd044597b" />


**Router-id:** bir OSPF ağındaki her yönlendiricinin (veya L3 switch'in) sahip olduğu benzersiz bir kimlik numarasıdır. 

**passive-interface:** komutu ise vlanları pasif olarak işaretledik çünkü ospf hello paketleri göndermeyi durdurur ama interfascedeki ağ bilgisini diğer routerlara (merkez router1'e) duyurmaya devam eder. Kullanım nedeni gereksiz trafik oluşmasını durdurmak,güvenlik ve cpu yükünü azaltmaktır.

Aynı komutlar **merkez-switch2** ye aynısı yapılır sadece router-id ve routea bağlanan network değişir.

**Merkez Multilayer Switch2**

<img width="467" height="461" alt="image" src="https://github.com/user-attachments/assets/989d77ef-8139-4836-bec7-b07f44347f79" />


**Şube Multilayer Switch1**


<img width="756" height="323" alt="image" src="https://github.com/user-attachments/assets/1f395ffc-4e63-4af0-b831-8a6f166aaa13" />

Şube multilayer switcht1de  de bunları yazıyoruz


**Şube Multilayer Switch2**


<img width="457" height="433" alt="image" src="https://github.com/user-attachments/assets/1eb7d5d0-a7cf-4ff9-ba86-a7a6a84fca72" />

Şube multilayer switch2 de  aynısı yapılır sadece router-id ve routea bağlanan network değişir.


#### Routerlara OSPF Yapılandırmaları

**Merkez-router1 yapılandırması**

<img width="675" height="240" alt="image" src="https://github.com/user-attachments/assets/5436cfb8-8792-45da-a223-c16c3c014573" />

ISP leri ospf içine dahil etmiyoruz güvenlik sebebinden dolayı. Zaten ISP kabul etmez hello paketleri ve boşuna trafik akar cpu yükü artar.



**Merkez-router2 yapılandırması**


<img width="698" height="203" alt="image" src="https://github.com/user-attachments/assets/c47b200f-ef53-470d-ab4c-da1668e3cca0" />


**Şube-router1 yapılandırması**


<img width="689" height="266" alt="image" src="https://github.com/user-attachments/assets/ad9f6ae3-55b0-4a79-9776-5fd73be4e2c0" />


**Şube-router2 yapılandırması**


<img width="705" height="204" alt="image" src="https://github.com/user-attachments/assets/2339acba-5c9f-435b-9291-f9b9b865090f" />

### 7)  Server Cihazlarına Statik Ip Atama

Server tarafının networkü 192.168.102.28/28 tir.


| | Ipv4 Adres | Subnet Mask | Default Gateway | DNS Server |
| :--- | :--- | :--- | :--- | :--- |
| DHCP Server | 192.168.102.130 | 255.255.255.240 | 192.168.102.129 | 192.168.102.131 |
| DNS Server | 192.168.102.131 | 255.255.255.240 | 192.168.102.129 | |
| E-mail Server | 192.168.102.132 | 255.255.255.240 | 192.168.102.129 | 192.168.102.131 |
| File Server | 192.168.102.134 | 255.255.255.240 | 192.168.102.129 | 192.168.102.131 |
| Web Server | 192.168.102.133 | 255.255.255.240 | 192.168.102.129 | 192.168.102.131 |


<img width="388" height="514" alt="Screenshot 2026-05-30 234609" src="https://github.com/user-attachments/assets/1753651c-cbcc-4804-97ae-058e3507cdb0" />


### 8) DHCP Server da Pool Oluşturma

Merkez network ve Ş ube network toplam 13 tane pool oluşturduk. 13 tane departmana dinamik olarak Ip adresi verecek bu dhcp server. 
		

<img width="741" height="511" alt="image" src="https://github.com/user-attachments/assets/c89f680c-28fd-4856-ace3-a0244f5b5d7b" />


### 9) Inter-VLAN Routing ve İp dhcp Helper Adres 

#### Inter-VLAN Routing
Farklı VLAN'larda yer alan ve Katman 2'de  birbirinden tamamen izole edilmiş olan cihazların, birbirleriyle iletişim kurmasını sağlayan yönlendirme işlemidir. Temel olarak 3 farklı yönteme ayrılır:
##### 1. Geleneksel Inter-VLAN Routing (Legacy)
Bu yöntem, VLAN teknolojisinin ilk dönemlerinde kullanılan eski ve maliyetli bir yaklaşımdır.

* **Çalışma Mantığı:** Switch üzerindeki her bir VLAN için, Router üzerinde ayrı bir fiziksel port ayrılır. Örneğin, ağda 3 tane VLAN varsa, switch'ten router'a 3 ayrı fiziksel kablo çekilir.
* **Dezavantajı:** Ağdaki VLAN sayısı arttıkça router üzerindeki fiziksel portlar hızla tükenir ve kablo maliyeti çok ciddi oranda artar. Günümüz modern ağlarında neredeyse hiç kullanılmaz.

---

##### 2. Router-on-a-Stick (RoaS)
Geleneksel yöntemin port israfı ve maliyet sorununu çözmek için geliştirilen, orta ve küçük ölçekli ağlarda sıklıkla tercih edilen yöntemdir.

* **Çalışma Mantığı:** Switch ile Router arasında tek bir fiziksel kablo çekilir ve bu hat Trunk olarak ayarlanır. Router'ın o tek fiziksel portu, yazılımsal olarak her VLAN için subinterface (alt arayüz) adı verilen sanal parçalara bölünür.
* **Avantajı:** Router üzerinde sadece tek bir fiziksel port kullanıldığı için donanım maliyetini minimuma indirir.

---

##### 3. Katman 3 (Multilayer) Switch ile Yönlendirme (SVI)
Büyük kurumsal ağlarda, yüksek performans ve hız gereksinimleri için kullanılan en modern ve en yaygın yöntemdir.

* **Çalışma Mantığı:** Araya harici bir router koymak yerine, yönlendirme işlemi hem anahtarlama (switching) hem de yönlendirme (routing) yapabilen Layer 3 Switch üzerinde gerçekleştirilir. Her VLAN için switch içinde SVI (Switched Virtual Interface) adı verilen sanal yönlendirme arayüzleri oluşturulur ve IP'ler buralara tanımlanır.
* **Avantajı:** Veri trafiği harici bir cihaza (router'a) gidip gelmek zorunda kalmaz. Yönlendirme işlemi doğrudan switch'in donanımsal chipleri (ASIC) üzerinde, hat hızında (wire-speed) gerçekleştiği için performans maksimumdur ve darboğaz yaşanmaz.
  

#### Ip Helper Adres
DHCP isteklerini başka bir ağdaki DHCP sunucusuna yönlendirmek için kullanılır. DHCP isteği (broadcast) VLAN dışına çıkamaz. Router / L3 Switch bu isteği unicast olarak DHCP server’a yollar 

---

-Önce server tarafında routerı router-on-a-stick yapıcaz vlan 80 için çünkü bu dhcp ile iletişim kurup hostlar ip alabilsin.

<img width="673" height="608" alt="image" src="https://github.com/user-attachments/assets/55ea0d44-a159-408a-83b0-d9ca29409ee6" />

Routerın L2 switch tarafındanki interface gig0/0'dır. Bu interface'in fiziksel ip adresi olmamalı. Sub-interface yapılandırıcaz ve bu sub-interface ile routing yapılır.
	
<img width="791" height="398" alt="image" src="https://github.com/user-attachments/assets/23df1fdd-96c9-4f7b-94ef-dfa04a2d4732" />


* **no ip address:** Router-on-a-Stick mimarisinde, switch'e bağlanan ana fiziksel portun kendisine doğrudan bir IP adresi verilmez (varsa silinir). Çünkü bu port mantıksal olarak alt parçalara bölünecektir.

* **interface GigabitEthernet0/0:** İşlem yapılacak olan ana fiziksel arayüze (Gi0/0) geçiş yapılmıştır.

* **interface GigabitEthernet0/0.80:** Fiziksel portun arkasına .80 konularak sanal bir alt arayüz oluşturulmuş ve subinterface konfigürasyon moduna (config-subif) geçilmiştir. Buradaki 80 sayısı genellikle karışıklığı önlemek için hedef VLAN ID ile aynı seçilir.

* **encapsulation dot1q 80:** Bu alt arayüzün IEEE 802.1Q trunking protokolünü kullanacağı ve VLAN 80'e ait veri paketlerini sırtlayacağı (etiketleyeceğini/çözeceğini) belirtir.


* **ip address 192.168.102.129 255.255.255.240:** VLAN 80 alt ağında bulunan cihazların (ağdaki server'ların) iletişim kurabilmesi için varsayılan Ağ Geçidi (Default Gateway) IP adresi ve /28 subnet maskesi bu alt arayüze tanımlanmıştır


Routerın sub-interface yapılandırıldı ip adresi 192.168.102.129 255.255.255.240 ile routing yapılacak.

---


-Şimdi L3-switchin sub-interfacelerini oluşturacağız. Önce merkez tarafındaki L3-switchleri yapılandırıcağız.


**Merkez-multilayer switch 2**

<img width="447" height="619" alt="image" src="https://github.com/user-attachments/assets/c86bf8c3-7f7b-4626-b401-1c8d62fda9a1" />

* **interface vlan [10-70]:** Belirtilen VLAN numaraları için Katman 3 seviyesinde sanal arayüzler (SVI) oluşturulmuştur. Bu arayüzler, o VLAN'daki cihazların birbiriyle konuşmasını sağlayan Inter-VLAN Routing yapısının temelidir.


* **ip address ... 255.255.255.192:** Her bir VLAN arayüzüne, o alt ağın  Default Gateway IP adresi tanımlanmıştır.

* **ip helper-address 192.168.102.130:** Bu komut ilgili VLAN'lardan gelen DHCP isteklerini broadcast'ten çıkartıp Unicast paketine dönüştürür ve doğrudan 192.168.102.130 IP adresli merkezi DHCP Sunucusuna iletir


**Merkez-multilayer switch 1**

<img width="448" height="605" alt="image" src="https://github.com/user-attachments/assets/496b9e22-be8a-4ee5-abf0-a8ae0c7f9e55" />


**Şube-multilayer switch 1**


<img width="449" height="521" alt="image" src="https://github.com/user-attachments/assets/dae8b69c-d47e-4d98-9f58-893fd8f0bc42" />


**Şube-multilayer switch 2**


<img width="447" height="518" alt="image" src="https://github.com/user-attachments/assets/05a67139-e489-4e1e-9cb3-8571d21cc3e4" />



### 10) Access Pointlerin Yapılandırılması 

**Merkez Access Point Yapılandırması**

| | SSID | PASSWORD |
| :--- | :--- | :--- |
| Poliklinik Dept. | POL-AP | POL-AP12345 |
| Laboratuvar Dept. | LAB-AP | LAB-AP12345 |
| Medikal Cihazlar Dept. | MED-AP | MED-AP12345 |
| Yönetim-Finans Dept. | FINANS-AP | FINANS-AP12345 |
| IT Departman | IT-AP | IT-AP12345 |
| Hasta Kayıt Dept. | HASTA-K.AP | HASTA-K.AP1 |
| Misafir Dept. | MISAFIR-AP | MISAFIR-AP1 |


**Şube Access Point Yapılandırması**


| | SSID | PASSWORD |
| :--- | :--- | :--- |
| Poliklinik(Ank.) Dept. | POLANK-AP | POLANK-AP1 |
| Laboratuvar(Ank.) Dept. | LABANK-AP | LABANK-AP1 |
| Medikal Cihazlar(Ank.) Dep. | MEDANK-AP | MEDANK-AP1 |
| Yönetim Küçük(Ank.) Dept. | FINANK-AP | FINANK-AP1 |
| Hasta Kayıt(Ank.) Dept. | HASANK-AP | HASANK-AP1 |
| Misafir Dept.(Ank.) | MiSANK-AP | MiSANK-AP1 |



<img width="1337" height="657" alt="image" src="https://github.com/user-attachments/assets/5a9c6e8c-051c-4f02-8962-5f156db45527" />


Networkün genel hali bu şekildedir. Bütün AP'ler yapılandırıldı. Laptoplar ve smartphonelar kendi departmanındaki  AP'lere bağlanmıştır.


### 11) PAT ve ACL Yapılandırması


* **PAT (Port Address Translation - Port Adres Dönüştürme)**

Yerel bir ağda bulunan çok sayıda cihazın (rivate IP adresi kullanan sadece tek bir genel (public) IP adresi üzerinden internete çıkmasını sağlayan bir Network Address Translation (NAT) türüdür. İç ağdaki cihazların IP adresleri internette yönlendirilemez . PAT bu cihazlardan gelen paketlerin kaynak IP adresini dış bacakta bulunan tek public IP adresi ile değiştirir.

* **ACL (Access Control List - Erişim Kontrol Listesi)**

Router veya Layer 3 switch gibi ağ cihazları üzerinden geçen veri paketlerini filtrelemek (izin vermek veya engellemek) için kullanılan bir dizi kural tablosudur. Ağ güvenliğini sağlamak ve trafiği denetlemek amacıyla kurulan bir dijital kontrol noktasıdır. Laboratuvar ve Medikal Cihazlar departmanın internete çıkmasına gerek yok onlara acl uygulayacağız.


-Önce routerlar da outside ve inside portları belirliyeceğiz. ISP'ye bakan portlar outside multilayer switchlere bakan portlar da inside olacak.

**Merkez-Router1**

<img width="155" height="190" alt="image" src="https://github.com/user-attachments/assets/8450460b-2859-461f-b9d0-a17baed8a2c1" />

Daha sonra ip nat overload yapıcaz.

<img width="762" height="13" alt="image" src="https://github.com/user-attachments/assets/6e9f424c-ba1e-458b-9f3e-f1d06f067a58" />

Bu komut bize İç ağdan gelip internete çıkmak isteyen ve Access List 1 içindeki kurallara uyan tüm yerel cihazları al, hepsinin kaynak IP adresini dış bacağımız olan serial0/1/0 arayüzünün IP adresine dönüştür. Paketlerin birbirine karışmaması için de her birine benzersiz birer port numarası ata (overload) der.

---

Şimdi de Acl list 1 oluşturup hangi networklerin dışarı çıkmasını istediklerimizi belirliyeceğiz. Laboratuvar ve Medikal Cihazlar departmanın internete çıkmasına gerek yok onları list 1 eklemeyeceğiz. 


<img width="637" height="120" alt="image" src="https://github.com/user-attachments/assets/ed66d26a-d03e-4bb0-99cb-af3b9374bbde" />

Laboratuvar(192.168.100.64) ve Medikal Cihazlar(192.168.100.128) departmanını eklemedik. 


**Şube-Router1**


<img width="150" height="189" alt="image" src="https://github.com/user-attachments/assets/48225dfb-22e0-47dd-9d8b-bb9d64976548" />


<img width="590" height="20" alt="image" src="https://github.com/user-attachments/assets/70153084-bf4d-45b2-bfdb-aa1e90c50d15" />


En sonda ise acl list 1 oluşturup istediğimiz networklere izin vericez. Laboratuvar ve Medikal Cihazlar deparmanına izin vermicez.

<img width="665" height="116" alt="image" src="https://github.com/user-attachments/assets/372b42b3-77a0-498f-99e5-cd92788205d3" />


**Merkez-Router2**

<img width="156" height="251" alt="image" src="https://github.com/user-attachments/assets/47388fec-4b10-4c9d-a972-5219f3bd5c92" />


<img width="528" height="22" alt="image" src="https://github.com/user-attachments/assets/e326dc80-58e5-4612-b3d7-ebd8eb752755" />

Acl list 1 oluşturucaz ve merkez-router2'den Laboratuvar ve Medikal Cihazların departmanlarını internete çıkarmak istemiyoruz.

<img width="660" height="102" alt="image" src="https://github.com/user-attachments/assets/7fba5fbd-4b15-46b7-ae87-20361cb5d52e" />


**Şube-Router2**

<img width="160" height="185" alt="image" src="https://github.com/user-attachments/assets/05ccb0c8-4881-42da-afcc-c8fd58109fe4" />


<img width="529" height="19" alt="image" src="https://github.com/user-attachments/assets/649edb58-37ae-40fa-baa6-68f6978dece0" />


### 12) ETHERCHANNEL 

Birden fazla fiziksel Ethernet hattını (kabloyu) mantıksal olarak birleştirerek tek bir yüksek hızlı hat  gibi çalıştırma teknolojisidir

<img width="141" height="364" alt="Screenshot 2026-06-01 135540" src="https://github.com/user-attachments/assets/6dee40a9-3ff1-4a47-b635-72968f467962" />


İki multilayer switch arasına 4 fiziksel kablo çektim ethechannel oluşturmak için. 

<img width="370" height="237" alt="image" src="https://github.com/user-attachments/assets/a0be8e87-4fc9-4cbe-a154-c981e318020b" />

Şube multilayer ve şube multileyer switchlerde de aynı portlar da oluşturudum  ve etherchannel yapılandırıldı.


### 13) HSRP Yapılandırması	 

Bir Katman 3 yedeklilik protokolüdür. Ağdaki istemci cihazların (PC, Server vb.) internete veya farklı ağlara çıkarken kullandıkları Varsayılan Ağ Geçidini donanımsal olarak yedeklemek amacıyla kullanılır. Ana cihazın öncelik değerini (priority) yüksek tutarak onun "Active" rolünü üstlenmesini sağlarız.

#### HSRP Nasıl Çalışır ve Rolleri Nelerdir?
HSRP yapılandırmasında cihazlar kendi aralarında "Hello" paketleri göndererek belirli rollere bürünürler:

* **Active Router :** Sanal IP adresine gelen tüm veri trafiğini fiilen sırtlayan ve yönlendiren ana cihazdır.

* **Standby Router :** Aktif cihazı sürekli dinleyen yedek cihazdır. Aktif router'dan belirli bir süre (Hold Time - varsayılan 10 saniye) boyunca sinyal gelmezse, onun çöktüğünü anlar ve milisaniyeler içinde trafiği kesintisiz bir şekilde üzerine alır.

* **Virtual Router :** Fiziksel olarak var olmayan, tamamen yazılımsal olan yapıdır. Ağdaki istemcilere (PC'lere) gateway olarak bu sanal cihazın IP adresi girilir.


**Merkez tarafındaki stand by router**

<img width="331" height="642" alt="image" src="https://github.com/user-attachments/assets/6cceb76e-2862-43c5-bde7-e94208f507cf" />

Bu standby router için yaptık priority değerini 100 verdim active router da priority değeri 110 verildi.


**Şube tarafındaki active router**

<img width="362" height="641" alt="image" src="https://github.com/user-attachments/assets/a914db1c-9aed-4935-a7ac-db91486a9196" />

Bu active için yaptık priority değerini 110 verdim stand by router için  priority değeri 100 verildi.


### 14) STP ve Port Security Yapılandırması(HSRP STP aligment)


#### STP Nedir? 

STP (Spanning Tree Protocol) yerel ağlarda (LAN) yedekli kablolama yapıldığında meydana gelebilecek "Network Loop"  oluşumunu engellemek için geliştirilmiş bir Katman 2 protokolüdür.

Ağda kesintisiz bağlantı sağlamak amacıyla switch'ler birbirine birden fazla kablo ile (yedekli) bağlanır. Ancak Katman 2 seviyesindeki Ethernet paketlerinde (örneğin Broadcast paketlerinde) TTL (Time to Live) değeri bulunmaz. Bu yüzden döngüye giren bir paket ağ üzerinde sonsuza kadar dönmeye başlar. Bu durum Broadcast fırtınalarına , MAC adresi tablolarının altüst olmasına ve sonuç olarak tüm ağın kilitlenmesine yol açar.

* **Nasıl Çalışır?**
  
STP ağdaki switch'ler arasından bir adet lider switch seçer, buna Root Bridge denir. Root Bridge seçildikten sonra tüm switch'ler ona giden en kısa yolları hesaplar. Döngüye sebep olan alternatif (yedek) hatların portları yazılımsal olarak "Blocking" ( moduna alınarak kapatılır. Ana hatlardan biri koptuğunda engellenen port otomatik olarak "Forwarding" (İletim) moduna geçer ve ağ kesintisiz çalışmaya devam eder.


En hızlı olan spanning tree rapid-pvst bütün switchlere **“spanning-tree mode rapid-pvst”** komutunu aktif edildi.

Merkez-multilayersw1  vlan 10,20,30 vlanların geçmesini ve merkez-multilayersw2den' de vlan 40,50,60  ve 70 vlanlarının geçmesini istiyoruz hsrp stp aligment yapıyoruz.
Bunun için priorityleri değiştircez merkez-multilayersw1 de vlan 10,20.30 vlanlarının prioritylerini artırıcaz. Daha sonra

```bash
spanning-tree vlan 10,20,30 root primary
spanning-tree vlan 40,50,60,70 root secondary
```		

bu komutları yazıcaz.


<img width="261" height="213" alt="image" src="https://github.com/user-attachments/assets/6314b9f5-a6f8-4438-b270-e3bc1983fbcc" />



Şubede ise 90,100 ve 110 vlanları şube-sw1 den geçecek şekilde ayarladım 120,130,140 da şube sw2 den geçecek.

```bash
spanning-tree vlan 90,100,120 root primary
spanning-tree vlan 110,120,130 root secondary
```		

<img width="259" height="195" alt="image" src="https://github.com/user-attachments/assets/0c35a1d1-61e1-489d-97ec-4527e9d49ded" />

---

### Port Security Nedir?

Bir switch'in fiziksel portlarına hangi cihazların bağlanabileceğini MAC adreslerine bakarak kontrol eden bir Katman 2 güvenlik özelliğidir.Şirket içindeki açık bir network prizine yetkisiz bir kişinin kendi bilgisayarını takmasını veya bir porttan ağa binlerce sahte MAC adresi göndererek switch'in hafızasını kilitlemeyi amaçlayan saldırıları (MAC Flooding) engellemek için kullanılır.

```bash
interface range f0/3 - 24
 		switchport mode access
 		spanning-tree portfast
		 spanning-tree bpduguard enable
 		switchport port-security
 		switchport port-security maximum 1
 		switchport port-security mac-address sticky
 		switchport port-security violation shutdown
		end

```	
Tüm access switchlere bu komutlar yazılacaktır. Port Security sadece uç cihazların(Pc vb.) bağlı olduğu Access portlarında uygulanabilir. Trunk portlarında çalışmaz.

* **spanning-tree portfast:** Bilgisayar takıldığında portun 30-50 saniye beklemek yerine anında aktif (Forwarding) olmasını sağlar.

* **spanning-tree bpduguard enable:** Bu porta yanlışlıkla veya kaçak olarak başka bir switch takılıp ağda döngü (loop) yaratılmaya çalışılırsa, port bunu anlar ve kendini otomatik kapatır
* **switchport port-security:** Portta MAC adresi tabanlı güvenliği aktif eder.

* **switchport port-security maximum 1:** Porta aynı anda en fazla 1 cihaz bağlanmasına izin verir.

* **switchport port-security mac-address sticky:** Porta takılan ilk cihazın MAC adresini otomatik öğrenir ve hafızaya kaydederek o cihazı porta zimmetler.

* **switchport port-security violation shutdown:** İzinli cihaz sökülüp yerine yabancı bir cihaz takılırsa, switch güvenliği korumak için portu tamamen kapatır
