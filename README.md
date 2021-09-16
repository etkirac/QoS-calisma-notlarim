# QoS-calisma-notlarim
### Quality of Service
QoS, farklı IP trafik akışlarına, farklı öncelik seviyeleri atamak için bir dizi araç ve mekanizmaya dayanan ve daha yüksek öncelikli IP trafik akışlarına özel muamele sağlayan bir ağ altyapısı teknolojisidir. Daha yüksek öncelikli IP trafik akışları için, ağ tıkanıklığı zamanlarında paket kaybını azaltır, gecikmeyi (latency) ve gecikme değişimini (jitter) kontrol etmeye yardımcı olur.

Bir ağda QoS uygulamasının birincil hedefleri şunlardır:

 Gerçek zamanlı uygulamalar için teslimatı hızlandırma

 İş açısından kritik uygulamalar için iş sürekliliğinin sağlanması

 Tıkanıklık meydana geldiğinde iş açısından kritik olmayan uygulamalar için adalet sağlanması

QoS, hedeflerine ulaşmak için aşağıdaki araçları ve mekanizmaları kullanır:

 Sınıflandırma ve işaretleme (Classification and marking)

 Denetleme ve şekillendirme (Policing and shaping)

 Tıkanıklık yönetimi ve kaçınma (Congestion management and avoidance)


#### QoS İhtiyacı
IP telefon, video yayını ve Cisco Webex gibi gerçek zamanlı multimedya uygulamaları, teslimat gecikmelerine karşı son derece hassastır ve bir ağ üzerinde hizmet kalitesi (QoS) talepleri oluşturur. Paketler, best-effort modeli kullanılarak teslim edildiğinde, sırayla veya zamanında ulaşmayabilir, düşebilir. Video için bu, görüntünün pikselleşmesine, duraklatılmasına, videonun kesintiye uğramasına, ses ve videonun senkronize olmamasına veya hiç video olmamasına neden olabilir. Ses için ise ekoya, konuşmacı çakışmasına, anlaşılmaz ve bozuk konuşmaya, ses kesintilerine, uzun süren sessizlik boşluklarına ve çağrı kesintilerine neden olabilir.
Aşağıdakiler kalite sorunlarının önde gelen nedenleridir:
1. Bant genişliği eksikliği (Lack of Bandwidth)
2. Gecikme ve gecikme değişimi (Latency and jitter)
3. Paket kaybı (Packet loss)


1.Lack of Bandwidth

Bir kaynaktan bir hedefe giden veri yolundaki mevcut bant genişliği, en düşük bant genişliği bağlantısının kapasitesine eşittir. En düşük bant genişliğine sahip bağlantının maksimum kapasitesi aşıldığında, bağlantıda tıkanıklık meydana gelir ve bu da trafik düşmelerine neden olur. Bu tür sorunların çözümü, bağlantı bant genişliği kapasitesini artırmaktır. Ancak bu, bütçe veya teknolojik kısıtlamalar nedeniyle her zaman mümkün değildir. Diğer bir seçenek, trafiği önem düzeyine göre önceliklendirmek için denetleme ve kuyruğa alma (policing and queuing) gibi QoS mekanizmalarını uygulamaktır. Ses, video ve iş açısından kritik trafik, uygulama gereksinimlerini desteklemek için öncelikli yönlendirmeye ve yeterli bant genişliğine sahip olmalı ve kalan bant genişliği en az önemli trafiğe tahsis edilmelidir.

2.Latency and jitter

Ağ gecikmesi olarak da adlandırılan gecikme (latency) , paketlerin bir ağ üzerinde kaynaktan hedefe seyahat etmesi için geçen süredir. ITU (International Telecommunication Union) Tavsiyesi G.114, uygulama türünden bağımsız olarak 400 ms'lik bir ağ gecikmesinin aşılmamasını ve gerçek zamanlı trafik için ağ gecikmesinin 150 ms'den az olmasını önermektedir.

Ağ gecikmesi dörde bölünebilir:

 Yayılma gecikmesi (Propagation Delay) (sabit) : Bir paketin fiber optik kablolar veya bakır teller gibi bir ortam üzerinden ışık hızında kaynaktan hedefe gitmesi için geçen süredir.

 Serileştirme gecikmesi (Serialization Delay) (sabit) : Bir paketin tüm bitlerini bir bağlantıya yerleştirmek için geçen süredir. Bağlantı hızına bağlı olan sabit bir değerdir. Bağlantı hızı ne kadar yüksek olursa, gecikme o kadar düşük olur.

 İşlem gecikmesi (Processing Delay) (sabit) : Bir ağ cihazının paketi bir giriş arayüzünden alması ve paketi çıkış arayüzünün çıkış kuyruğuna yerleştirmesi için geçen sabit süredir.

 Gecikme değişimi (Delay Variation) (değişken) : Jitter olarak da adlandırılan gecikme değişimi, tek bir akışta paketler arasındaki gecikme farkıdır. Örneğin, bir paketin kaynaktan hedefe taşınması 40 ms sürerse ve sonraki paket 60 ms sürerse, jitter 20 ms'dir.


3.Packet Loss

Paket kaybı genellikle bir arabirimdeki tıkanıklığın bir sonucudur. Aşağıdaki adımlardan biri uygulanarak paket kaybı önlenebilir:

 Bağlantı hızını arttırmak.

 QoS tıkanıklık önleme ve tıkanıklık yönetim mekanizmalarını uygulamak

 Düşük öncelikli paketleri bırakmak ve yüksek öncelikli trafiğe izin vermek için trafiği denetlemek

 Trafik patlaması ve arabirim arabelleğinin kapasitesini aşması nedeniyle paketleri bırakmak yerine geciktirmek için trafik şekillendirme uygulamak. Gerçek zamanlı trafik için trafik şekillendirme önerilmez, çünkü jitter’a neden olabilir.


#### QoS Modelleri
Üç farklı QoS uygulama modeli vardır:
1. Best effort : Bu model için QoS etkinleştirilmemiştir. Herhangi bir özel işlem gerektirmeyen trafik için kullanılır.
2. Integrated Services (IntServ) : Uygulamalar, ağa bir bant genişliği rezervasyonu yapması ve özel QoS tedavisi gerektirdiklerini belirtmek için sinyal gönderir.
3. Differentiated Services (DiffServ): Ağ, özel QoS tedavisi gerektiren sınıfları tanımlar.

IntServ modeli, hem öngörülebilir hem de garantili hizmet seviyelerini sağlamak için bant genişliği, gecikme ve paket kaybı garantisi gerektiren ses ve video gibi gerçek zamanlı uygulamalar için oluşturulmuştur. Bu modelde uygulamalar, ihtiyaç duydukları uçtan uca kaynakları (bant genişliği gibi) rezerve etmek için gereksinimlerini ağa bildirir. IntServ, belirli bir uygulama için bir ağ boyunca kaynakları ayırmak ve başka hiçbir IP trafiğinin ayrılmış bant genişliğini kullanamayacağını garanti etmek için Kaynak Rezervasyon Protokolü'nü (Resource Reservation Protocol) (RSVP) kullanır.
Uçtan uca (end-to-end) QoS sağlayabilmek için, uygulamaları çalıştıran uç noktalar da dahil olmak üzere tüm düğümlerin her bir akış için RSVP yol durumunu desteklemesi, oluşturması ve sürdürmesi gerekir. Bu, IntServ'in en büyük dezavantajıdır, çünkü bakımı gereken çok sayıda RSVP akışı olması nedeniyle binlerce veya milyonlarca akışa sahip olabilecek büyük ağlarda iyi ölçeklenemez.

DiffServ, best-efort ve IntServ modellerinin sınırlamalarını ele almak için tasarlanmıştır. Bu modelle, bir sinyal protokolüne gerek yoktur yani her bir düğümde sürdürülecek RSVP akış durumu yoktur, bu da onu yüksek düzeyde ölçeklenebilir kılar. QoS özellikleri (bant genişliği ve gecikme gibi), ağdaki her cihazda bağımsız olarak tanımlanan QoS politikalarıyla hop-by-hop temelinde yönetilir. DiffServ, uçtan uca (end-to-end) QoS çözümü olarak kabul edilmez çünkü uçtan uca QoS garantileri uygulanamaz.
DiffServ, IP trafiğini sınıflara böler ve iş gereksinimlerine göre işaretler, böylece her sınıfa farklı bir hizmet düzeyi atanabilir. IP trafiği bir ağ üzerinden geçerken, ağ cihazlarının her biri kendi işaretlemesiyle paket sınıfını tanımlar ve bu sınıfa göre paketlere hizmet verir. DiffServ ile birçok hizmet seviyesi seçilebilir. Örneğin, IP telefon, ses trafiği gecikmeye ve jitter’a karşı çok hassastır, bu nedenle diğer tüm uygulama trafiğine göre her zaman öncelikli muamele görmelidir. Öte yandan e-posta, büyük bir gecikmeye dayanabilir ve best-effort ile hizmet verilebilir ve iş dışı, kritik olmayan trafiği (YouTube'dan gelen gibi) ya yüksek oranda sınırlandırılabilir veya tamamen engellenebilir. DiffServ modeli en popüler ve en yaygın olarak kullanılan QoS modelidir.

#### CLASSIFICATION AND MARKING
Herhangi bir QoS mekanizması uygulanmadan önce, IP trafiği iş gereksinimlerine göre tanımlanmalı ve farklı sınıflara ayrılmalıdır. Ağ cihazları, IP trafiğini belirli bir sınıfa ait olarak tanımlamak için “classification” kullanır. IP trafiği sınıflandırıldıktan sonra, diğer ağ cihazlarının ağı geçerken bu paketlere QoS mekanizmalarını uygulayabilmesi için bireysel paketleri işaretlemek için “marking” kullanılabilir.
##### CLASSIFICATION
Classification, farklı trafik akışları arasında ayrım yapmaktan sorumlu bir QoS mekanizmasıdır. Trafiğin kaynağına mümkün olduğunca yakın, ağ kenarında yapılmalıdır. Bir IP paketi sınıflandırıldıktan sonra, paketler daha sonra yeniden işaretlenebilir, sıraya alınabilir, denetlenebilir, şekillendirilebilir veya bunların ve diğer eylemlerin herhangi bir kombinasyonu yapılabilir.

Aşağıdaki trafik tanımlayıcıları genellikle classification için kullanılır:

Internal: QoS grupları

Layer 1: Fiziksel arayüz, alt arayüz veya port

Layer 2: MAC adresi ve 802.1Q/p Class of Service (CoS) bitleri

Layer 2.5: MPLS Experimental (EXP) bitleri

Layer 3: Differentiated Services Code Points (DSCP), IP Precedence (IPP) ve kaynak/hedef IP adresi

Layer 4: TCP veya UDP portları

Layer 7: Next Generation Network-Based Application Recognition (NBAR2)


###### Layer 7 Classification
NBAR2, Layer 3 ile Layer 7 verilerini kullanarak çeşitli protokolleri ve uygulamaları sınıflandırabilen ve tanımlayabilen bir paket inceleme mekanizmasıdır.
NBAR2'nin iki çalışma modu vardır:

1. Protocol Discovery: NBAR2'nin anlık olarak ağda çalışan uygulamalar hakkında gerçek zamanlı istatistikleri keşfetmesini ve almasını sağlar. Protocol Discovery modundaki bu istatistikler, MQC yapılandırmasını kullanarak QoS sınıflarını ve ilkelerini tanımlamak için kullanılabilir.

2. Modular QoS CLI (MQC): MQC kullanarak, Cisco Webex gibi belirli bir ağ protokolüyle eşleşen ağ trafiği bir trafik sınıfına yerleştirilebilirken, YouTube gibi farklı bir ağ protokolüyle eşleşen trafik başka bir trafik sınıfına yerleştirilebilir. Trafik bu şekilde sınıflandırıldıktan sonra, farklı trafik sınıflarına farklı QoS politikaları uygulanabilir.


##### MARKING
Marking (Paket işaretleme), bir paket içindeki bir alanı veya trafik tanımlayıcısı olan bir frame başlığını değiştirerek bir paketi renklendiren ve böylece diğer QoS mekanizmalarının uygulanması sırasında diğer paketlerden ayırt edilmesini sağlayan bir QoS mekanizmasıdır.

Trafiği işaretlemek (marking) için aşağıdaki trafik tanımlayıcıları kullanılır:

Internal: QoS grupları

Layer 2: 802.1Q/p Class of Service (CoS) bitleri

Layer 2.5: MPLS Experimental (EXP) bitleri

Layer 3: Differentiated Services Code Points (DSCP) and IP Precedence (IPP)


###### Layer 2 Marking
802.1Q standardı, Layer 2 ağlarda VLAN'ları uygulamak için geliştirilen bir IEEE özelliğidir. 802.1Q spesifikasyonu iki 2 byte’lık alan tanımlar. Bunlar, Tag Protocol Identifier (TPID) ve Tag Control Information (TCI)’dır.

TCI , aşağıdaki üç alandan oluşan 16 bitlik bir alandır:

1. Priority Code Point (PCP) alanı (3 bit)
2. Drop Eligible Indicator (DEI) alanı (1 bit)
3. VLAN Identifier (VLAN ID) alanı (12 bit)

1.Priority Code Point (PCP)
3 bit PCP alanının özellikleri, IEEE 802.1p spesifikasyonu tarafından tanımlanır. Bu alan, paketleri belirli bir CoS'a ait olarak işaretlemek için kullanılır. CoS işaretlemesi, bir Layer 2 Ethernet frame’inin, 0'dan 7'ye kadar sekiz farklı öncelik değeri düzeyiyle işaretlenmesini sağlar. Burada 0, en düşük öncelik ve 7 en yüksek önceliktir.


IEEE 802.1p CoS tanımları


    PCP Değeri -----    Trafik Türü

    0(en düşük) ----    Background

    1(default) -----    Best effort

    2          -----    Excellent effort

    3          -----    Critical Application

    4          -----    Video (100 ms gecikme ve jitter altında)

    5          -----    Voice (10 ms gecikme ve jitter altında)

    6          -----    Internetwork kontrol

    7(en yüksek) ---    Network kontrol


CoS işaretlerini kullanmanın bir dezavantajı, framelerin 802.1Q olmayan bir bağlantıyı veya bir Layer 3 ağını geçerken CoS işaretlerini kaybetmesidir. Bu nedenle, işaretleme değerlerinin uçtan uca korunabilmesi için paketler mümkün olduğunda diğer üst katman işaretleriyle de işaretlenmelidir.

2. Drop Eligible Indicator (DEI)

DEI alanı, tıkanıklık zamanlarında atılmaya uygun frameleri belirtmek için bağımsız olarak veya PCP ile birlikte kullanılabilen 1 bitlik bir alandır. Bu alan için varsayılan değer 0'dır ve bu frame’in atılmaya uygun olmadığını belirtir; frame’in atılmaya uygun olduğunu belirtmek için 1'e ayarlanabilir.

3. VLAN Identifier (VLAN Kimliği)

VLAN Identifier alanı, 802.1Q tarafından kullanılan VLAN'ı tanımlayan 12 bitlik bir alandır. Bu alan 12 bit olduğundan, 802.1Q tarafından desteklenen VLAN sayısını 4096 ile sınırlar, bu da büyük işletme veya servis sağlayıcı ağları için yeterli olmayabilir.

###### Layer 3 Marking
Bir paket, kaynağından hedefine giderken, CoS alanını desteklemeyen non-802.1Q trunked veya non-Ethernet bağlantılardan geçebilir. Layer 3'te marking kullanılması, uçtan uca korunan daha kalıcı bir marker (işaretçi) sağlamaktır.

ToS alanı, IP Precedence (IPP) olarak adlandırılan ToS alanının yalnızca ilk 3 bitinin marking (işaretleme) için kullanıldığı ve bitlerin geri kalanının kullanılmadığı 8 bitlik bir alandır. 0 ile 7 arasında değişen IPP değerleri, trafiğin altı adede kadar kullanılabilir CoS bölünmesine izin verir. IPP 6 ve 7, internal ağ kullanımı için ayrılmıştır.

IPv4 ToS ve IPv6 Trafik Sınıfı alanları, 8-bit Differentiated Services (DiffServ) alanı olarak yeniden tanımlamıştır. DiffServ alanı, daha önce IPv4 ToS ve IPv6 Trafik Sınıfı alanları için kullanılan aynı 8 biti kullanır ve bu, IP Precedence ile backward uyumlu olmasını sağlar. DiffServ alanı, 64 adede kadar (0 ila 63) sınıflandırılmasına izin veren 6 bitlik Differentiated Services Code Point (DSCP) alanından ve 2 bitlik Explicit Congestion Notification (ECN) alanından oluşur.

###### DSCP Per-Hop Behaviors (PHB)
Paketler, hedefe giden yol boyunca ağ düğümlerinde belirli bir Per-Hop davranışını alacak şekilde sınıflandırılır ve işaretlenir. PHB, DSCP değerine dayalı olarak, bir veya birden fazla QoS mekanizması tarafından bir paket koleksiyonunu hızlandırıp, geciktirip veya bırakabilir.

DiffServ alanı, paketleri sınıflandırmalarına göre DiffServ Behavior Aggregates (BA's) olarak işaretlemek için kullanılır. Bir DiffServ BA, belirli bir yönde bir bağlantıyı geçen aynı DiffServ değerine sahip paketlerin bir koleksiyonudur. Bir DiffServ BA, birden çok uygulama olabilir. Örneğin, tümü bir araya toplanmış ve aynı DSCP değeriyle işaretlenmiş SSH, Telnet ve SNMP olabilir. Bu şekilde, ağın çekirdeği, DiffServ BA'larına dayalı olarak yalnızca basit PHB gerçekleştirirken, ağ kenarı sınıflandırma, işaretleme, denetleme ve şekillendirme işlemlerini gerçekleştirir. Bu, DiffServ QoS modelini çok ölçeklenebilir kılar.

Genel kullanım için dört PHB tanımlanmıştır:

1. Class Selector (CS) PHB: DSCP alanının ilk 3 biti CS biti olarak kullanılır. CS bitleri, sınıfı belirlemek için IP Precedence gibi aynı 3 biti kullandığından, DSCP'yi IP Precedence ile uyumlu çalışır.

2. Default Forwarding (DF) PHB: Best-effort gerektiren hizmet için kullanılır.

3. Assured Forwarding (AF) PHB: Garantili bant genişliği hizmeti için kullanılır.

4. Expedited Forwarding (EF) PHB: Düşük gecikmeli servis için kullanılır.

AF PHB, bir AF sınıfı için belirli bir bant genişliği miktarını garanti eder ve varsa ekstra bant genişliğine erişim sağlar. AF PHB gerektiren paketler DSCP değeri aaaadd0 ile işaretlenmelidir. Burada aaa, AF sınıfının binary değeridir ve dd, drop probability olarak adlandırılan, kullanılmayan ve her zaman 0 olarak ayarlanan düşme olasılığıdır.

Dört standart tanımlı AF sınıfı vardır. Bunlar; AF1, AF2, AF3 ve AF4. AF sınıf numarası, önceliği temsil etmez. Örneğin, AF4, AF1'e göre herhangi bir ayrıcalıklı muamele görmez. Her sınıf bağımsız olarak ele alınır ve farklı sıralara yerleştirilir. AF Adı (AFxy), AF IP Precedence değerinden (x) ve Drop Probability değerinden (y) oluşur. Örneğin, AF31, IP Precedence değeri 3 olan ve Drop Probability değeri 1 olan bir birleşimdir. AF adını hızlı bir şekilde decimal olarak bir DSCP değerine dönüştürmek için 8x + 2y formülünü kullanılır. Örneğin, AF31 için DSCP değeri 8(3) + 2(1) = 26'dır.


EF PHB, düşük kayıplı, düşük gecikme süreli, garantili bant genişliği, uçtan uca hizmet oluşturmak için kullanılabilir. EF PHB, bant genişliğini garanti eder ve düşük gecikmeli queuing uygulayarak gecikmeye duyarlı uygulamalar için mümkün olan en düşük gecikmeyi sağlar. EF gerektiren paketler, DSCP binary değeri 101110 (ondalık olarak 46) ile işaretlenmelidir.

###### Trust Boundary
Uçtan uca ve ölçeklenebilir bir QoS sağlamak için paketler, uç nokta tarafından veya uç noktaya mümkün olduğunca yakın olarak işaretlenmelidir. Bir uç nokta, bir frame’i veya bir paketi CoS veya DSCP değeriyle işaretlediğinde, bağlı olduğu switch, CoS veya DSCP değerlerini kabul edecek veya reddedecek şekilde yapılandırılabilir. Switch, değerleri kabul ederse, uç noktaya güvendiği ve alınan uç nokta paketleri için herhangi bir paketi yeniden sınıflandırması ve yeniden işaretleme yapmasının gerekmediği anlamına gelir. Switch uç noktaya güvenmiyorsa, işaretleri reddeder ve alınan paketleri uygun CoS veya DSCP değeriyle yeniden sınıflandırır ve bildirir.

###### Wireless QoS
Örneğin, bir kablosuz LAN denetleyicisi (WLC), kablosuz ve kablolu ağlar arasındaki sınırda bulunur, bu nedenle QoS trust boundary için gerekli hale gelir. WLC'ye giren ve çıkan trafik, kablosuz ve kablolu ağ üzerinden iletilirken uygun şekilde ele alınabilmesi için sınıflandırılabilir ve işaretlenebilir. Wireless QoS, aşağıda listelenen dört trafik kategorisi kullanılarak her wireless LAN'da (WLAN) benzersiz bir şekilde tanımlanabilir.

    QoS Kategori Trafik Tipi    802.1p Tag  DSCP değeri
    Platinum     Voice          5           46(EF)
    Gold         Video          4           34(AF41)
    Silver       Best effort    0           0
    Bronze       Background     1           10(AF11)

Mesela yeni bir WLAN oluşturduğumuzda, QoS politikası varsayılan olarak Silver veya best effort ile ele alınabilir ya da ses trafiğini taşımak için 'voice' adlı bir WLAN oluşturulur ve QoS politikası Platinum olarak ayarlanmalıdır.

##### POLICING AND SHAPING
Trafik polisleri (policers) ve şekillendiriciler (shapers), trafiği sınıflandırmak ve hız sınırlama gibi QoS mekanizmalarını uygulamak için kullanılan trafik koşullandırma QoS mekanizmalarıdır. Trafiği aynı şekilde sınıflandırırlar ancak uygulamalarında farklılık gösterirler:
Traffic Policers, istenen trafik oranını aşan gelen veya giden trafiği bırakır veya yeniden işaretler. İstenen trafik hızı aşıldığında, bir policer aşağıdaki eylemlerden birini gerçekleştirebilir:
- Trafiği bırakmak
- Fazla trafiği daha düşük bir öncelikle işaretlemek

Fazla trafik işaretlenirken, paketlerin daha düşük öncelikli bir sınıf değeriyle yeniden işaretlenmesine dikkat edilir. Örneğin, AFx1 ile işaretlenen fazla trafik, AFx2'ye işaretlenmelidir.

Policerları konumlandırırken, gelen trafik için trafiğin ağın çekirdeğindeki değerli bant genişliğini boşa harcamasını önlemek için en uygun şekilde ağın kenarında policerlar konumlandırılır. Giden trafik için polisler en uygun şekilde ağın kenarında veya ağ ucu cihazlarındaki core’a bakan arabirimlerde konumlandırılır. Policer’ın bir dezavantajı, trafiği düşürdüğünde TCP retransmission’a neden olmasıdır. 

Traffic Shaping, belirli türdeki ağ paketlerinin akışını geciktiren bant genişliği yönetimi tekniğidir. Trafik şekillendirme, belirli uygulama türleri tarafından tüketilebilecek bant genişliği miktarını sınırlar.
Şekillendiriciler, çıkış trafiği için kullanılır ve genellikle kurumsal ağlar tarafından hizmet sağlayıcıya (Service Provider (SP)) bakan arabirimlerde konumlandırılır. Şekillendirme, SP'lerin gelen trafiği denetlediği ve SP'lerin trafiği denetledikten sonra ihlal durumunda para cezalarına neden olabilecek maksimum trafik oranı SLA'sına sahip olduğu durumlarda yararlıdır. Trafiği şekillendirmek, trafiği düşürmek yerine geciktirir ve bu, denetlemeye kıyasla daha az TCP retransmission’a neden olur.

###### Token Bucket Algoritması
Cisco IOS policer ve shaperlar token bucket algoritmasına dayanarak çalışır. Token bucket algoritmasında kullanılan bazı terminolojiler aşağıda tanımlanmıştır.

Commited Information Rate (CIR): Trafik sözleşmesinde tanımlanan bit/saniye (bps) cinsinden denetlenen trafik hızıdır.

Commited Time Interval (Tc): Üzerinde taahhüt edilen trafiğin (Bc) gönderildiği milisaniye (ms) cinsinden zaman aralığı.
Tc = (Bc [bits] / CIR [bps]) × 1000 formülü ile hesaplanabilir.

Committed Burst Size (Bc): Bir Tc içinde gönderilebilecek maksimum trafik miktarıdır.
Bc = CIR × (Tc / 1000) formülü ile hesaplanabilir.

Token: Tek bir token 1 byte veya 8 biti temsil eder.

Token Bucket: Önceden tanımlanmış maksimum token sayısına ulaşılana kadar tokenları biriktiren bir bölümdür. Bu tokenlar, sabit bir oranda (CIR) eklenir. Her paket, tanımlanan orana uygunluk açısından kontrol edilir ve paket boyutuna eşit paketten tokenlar alır; örneğin paket boyutu 1500 byte ise buckettan 12.000 bit (1500 × 8) alır.

Bc değerinin bir trafik akışındaki olası en büyük IP paketinin boyutundan büyük veya ona eşit olması önerilir. Aksi takdirde, daha büyük paketler için token bucketta asla yeterli token olmayacak ve bunlar her zaman tanımlanan oranı aşacaktır. Bucket maksimum kapasiteye kadar dolarsa, yeni eklenen tokenlar atılır.

##### Congestion Management (Tıkanıklık Yönetimi)
Tıkanıklık yönetimi, queuing (kuyruğa alma) ve scheduling (çizelgeleme) mekanizmalarının kombinasyonunu içerir. Queuing, fazla paketlerin geçici olarak depolanmasıdır. Queuing, bir çıkış arabiriminde tıkanıklık yaşandığında etkinleştirilir ve tıkanıklık giderildiğinde devre dışı bırakılır. Tıkanıklık şu iki nedenden biri nedeniyle ortaya çıkabilir:

- Giriş arabirimi, çıkış arabiriminden daha hızlıdır.

- Çıkış arabirimi, çoklu giriş arabiriminden paketleri alıyordur.

Tıkanıklık meydana geldiğinde, kuyruklar dolar ve paketler bazı kuyruklama algoritmaları tarafından yeniden sıralanabilir, böylece yüksek öncelikli paketler çıkış arabiriminden düşük öncelikli paketlerden daha çabuk çıkar. Bu noktada, bir scheduling algoritması hangi paketin daha sonra iletileceğine karar verir.

MQC mimarisinden önce gelen eski queuing algoritmaları şunlardır:

First-in First-out queuing (FIFO): FIFO, çıkış arabirimi kuyruğuna yerleştirilecek ilk paketin arabirimden ayrılan ilk paket olduğu queuing mekanizmasıdır. (ilk gelene ilk hizmet) FIFO kuyruğunda, tüm trafik aynı sınıfa aittir.

Round robin: Round robin ile, birbiri ardına hizmet verilir ve her sıra yalnızca bir paketi işler. Yani her sıra her turda bir paket gönderme fırsatına sahiptir. Round robin'in dezanvantajı, trafiğe öncelik vermek için bir mekanizma içermemesidir.

Weighted round robin (WRR): WRR, round robin için öncelik belirleme sağlamak üzere geliştirilmiştir. Her kuyruğa bir ağırlık atanmasına izin verir ve bu ağırlığa dayalı olarak öncelik belirleme sağlanır.

Custom Queuing (CQ): CQ, WRR'nin Cisco uygulamasıdır. Her kuyruk, seçilen her trafik türü için bant genişliğinin bir kısmı ile özelleştirilebilir. Belirli bir trafik türü kendisine ayrılan bant genişliğini kullanmıyorsa, diğer trafik türleri kullanılmayan bant genişliğini kullanabilir. CQ uzun gecikmelere neden olur ve ayrıca trafik sınıflandırması için kullandığı 16 sıranın her birinde FIFO ile aynı sorunlara sahiptir.

Priority Queuing (PQ): PQ ile, her sıra içinde öncelik sırasına göre dört sıra (yüksek, orta, normal ve düşük) belirlenir. Yüksek öncelikli sıraya her zaman önce hizmet verilir ve düşük öncelikli sıralara yalnızca tüm yüksek öncelikli sıralar boş olduğunda hizmet verilir.

Weighted Fair Queuing (WFQ): WFQ algoritması, bant genişliğini tüm akışlar arasında adil bir şekilde tahsis etmek için arayüzün bant genişliğini akış sayısına (IP Önceliğine göre ağırlıklı olarak) otomatik olarak böler. Bu yöntem, yüksek öncelikli gerçek zamanlı akışlar için daha iyi hizmet sağlar ancak belirli bir akış için sabit bant genişliği garantisi sağlayamaz.

Yeni queuing algoritmaları şunlardır:

Class Based Weighted Fair Queuing (CBWFQ): CBWFQ, 256'ya kadar trafik sınıfına hizmet verip 256'ya kadar kuyruk oluşturulmasına olanak tanır. Her kuyruğa, o sınıfa atanan bant genişliğine göre hizmet verilir. Bir paket belirli bir sınıfa ait olarak sınıflandırıldıktan sonra, ona bant genişliği, ağırlık, kuyruk limiti ve maksimum paket limiti atanabilir. Bir sınıfa atanan bant genişliği, tıkanıklık sırasında sınıfa verilen minimum bant genişliğidir. Bu sınıf için kuyruk sınırı, sınıf kuyruğunda arabelleğe alınmasına izin verilen maksimum paket sayısıdır. Bir kuyruk, yapılandırılan kuyruk sınırına ulaştıktan sonra, fazla paketler drop edilir. CBWFQ tek başına bir gecikme garantisi sağlamaz ve sadece gerçek zamanlı olmayan veri trafiği için uygundur.

Low Latency Queuing (LLQ): LLQ, Priority Queuing (PQ) ile birleştirilmiş CBWFQ'dur ve ses gibi gerçek zamanlı trafiğin gereksinimlerini karşılamak için geliştirilmiştir. Tüm gerçek zamanlı trafik, priority queue tarafından hizmet verilecek şekilde yapılandırılmalıdır. Birden çok gerçek zamanlı trafik sınıfı tanımlanabilir ve her birine ayrı bant genişliği garantileri verilebilir, ancak tek bir priority queue tüm trafiği planlar. Bir trafik sınıfı kendisine atanan bant genişliğini kullanmıyorsa, diğer sınıflar arasında paylaşılır. Bu algoritma, gerçek zamanlı ve gerçek zamanlı olmayan trafik kombinasyonları için uygundur. Yüksek öncelikli gerçek zamanlı trafiğe hem gecikme hem de bant genişliği garantileri sağlar.

##### Congestion-Avoidance Tools (Tıkanıklıktan Kaçınma Teknikleri)

Tıkanıklıktan kaçınma teknikleri, paketleri bırakarak tıkanıklığı önlemek için ağ trafiğini izlemektedir. Varsayılan paket bırakma mekanizması ‘tail drop’ adı verilen bir mekanizmadır. Tail drop, tüm trafiğe eşit davranır ve hizmet sınıfları arasında ayrım yapmaz. Tail drop ile, çıkış arabellekleri dolduğunda, sıraya girmeye çalışan tüm paketler, önceliklerine bakılmaksızın, tıkanıklık ortadan kalkana ve sıra artık boş olana kadar bırakılır. TCP trafiği için tail droptan kaçınılmalıdır, çünkü TCP global senkronizasyonuna neden olur ve bu da bağlantının yetersiz kullanımına sebep olabilir.
Bu durumun çözümlenebilmesi için Random Early Detection (RED) olarak bilinen bir mekanizma kullanmaktır. RED, kuyruk arabellekleri dolmadan paketleri rastgele bırakarak tıkanıklık önleme sağlar. Tail dropta olduğu gibi hepsini bir kerede bırakmak yerine paketleri rastgele bırakır. Böylece TCP akışlarının global senkronizasyonunu önler.
RED'in Cisco uygulaması, weighted RED (WRED) olarak bilinir. RED ve WRED arasındaki fark, paket düşüşlerinin rastgele olması yerine, IP Önceliği (IPP) veya DSCP ile gösterilen trafik ağırlıkları tarafından sağlanmasıdır.
