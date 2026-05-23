# Packet-Tracer-da-2-ubeli-Network-Topoloji-n-as-


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

















