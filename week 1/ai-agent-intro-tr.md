# Hafta 1: Temel Kavramlar ve Microsoft Agent Framework'e Giriş

## AI Agent Nedir?

Karmaşık görevleri ve belirli hedefleri yerine getirmek için yapay zeka kullanılan, müdahale gerektirmeden kendi başına karar alabilen (özerk) yazılımlardır. Karar verme, problem çözme, dış ortamlarla etkileşime girme ve hedefe yönelik eylemleri gerçekleştirme gibi geniş kapsamlı yeteneklere sahiptir.

Temelinde Büyük Dil Modellerini (LLM) barındırır ve gerektiğinde multimodal modeller ile desteklenerek metin, ses, video, kod gibi çok modlu verileri işleyebilir. Ancak geleneksel LLM'ler statiktir; yalnızca eğitildikleri veriler ile sınırlıdırlar. Canlı veri veya otonom eyleme geçemezler.

AI Agentler ise dinamik yapıya sahiptirler; LLM'in akıl yürütme becerisini arka planda araç çağırma (tool/function calling), hafıza (memory) ve dinamik iş akışları (workflow) ile birleştirir ve eğitildiği verilerin ötesine geçer. Bu sayede otonom ve karmaşık görevleri yerine getirebilirler.

**Tool Calling:** Yapay zeka araçlarının kapasitelerini genişletmek, çevreleriyle etkileşime girmek ve görevleri yerine getirmek amacıyla harici sistemlere veya kaynaklara otonom başvurmasıdır.

## LLM (Büyük Dil Modeli) Nedir?

Büyük Dil Modelleri (LLM) en temel tanımıyla devasa miktarda metin verisi kullanılarak eğitilmiş ve insan benzeri dili anlayıp üretebilen derin öğrenme tabanlı yapay zeka sistemleridir.

LLM'ler aslında işin özünde devasa birer istatistiksel tahmin makineleridir. Modele bir prompt verildiğinde model bunu önceden kurgulamaz. Eğitiminde kullanılan metinler sayesinde öğrendiği dil kurallarını kullanarak bağlama en uygun şekilde, bir sonraki kelimenin (token'ın) ne olması gerektiğini tahmin eder.

İsmindeki "büyük" kelimesi hem milyarlarca kelimeden oluşan veri kümeleriyle eğitildiğini hem de modelin kendi içerisinde karar vermek için kullandığı ve milyarlarca hatta trilyonlarca sayıya ulaşabilen matematiksel ağırlıklara sahip olmasıdır. Model ne kadar büyükse insan dilini taklit etme ve isabetli yanıtlar verme kapasitesi de o kadar yüksek olur.

### LLM Çalışma Süreci

Büyük Dil Modellerinin arka plandaki çalışma süreci, ham verinin alınıp kullanıcının karşısına akıcı bir metin olarak çıkmasına kadar uzanan çok katmanlı ve karmaşık aşamalardan oluşur.

#### Tokenization

Modeller kelimeleri doğrudan okuyamaz. Girilen metinler (promptlar) token adı verilen, makinenin algılayabileceği küçük, anlamlı parçalara (kelime veya hece) bölünür.

#### Embedding

Dil modelleri kelimeleri okuyamaz, sadece sayıları algılayabilir. Bu nedenle elde edilen token'lar, "embedding" adı verilen çok boyutlu sayısal vektörlere dönüştürülür. Anlamca birbirine benzeyen kelimeler matematiksel uzayda birbirlerine yakın konumlandırılırlar.

#### Transformer ve Öz-Dikkat (Self-Attention)

Bu aşamada devreye transformer mimarisi ve öz-dikkat (self-attention) girer.

2017 yılında Google araştırmacıları tarafından yayınlanan "Attention Is All You Need" isimli makaleyle tanıtılan Transformer mimarisi günümüzdeki Büyük Dil Modellerinin temelini oluşturan bir sinir ağı yapısıdır. Büyük Dil Modellerinin insan dilini anlamasını ve üretmesini sağlar.

Eski nesil yapay zeka sistemleri bir metni okurken kelimeleri tıpkı insanların kitap okuduğu gibi sırayla, sekansiyel olarak işlemek zorundaydı. Bu durum hem sistem hızını yavaşlatıyor hem de modelin cümle başındaki bir kelimenin cümle sonundaki bir kelimeyle olan ilişkisini akılda tutmasını zorlaştırıyordu.

Transformer mimarisi bu sorunu iki aşama ile ortadan kaldırdı:

1. **Paralel İşleme:** Transformerlar kelimeleri sırayla okumak yerine metnin veya kelime dizisinin tamamını aynı anda, paralel olarak işler. Bu durum modellerin yeni donanımlı cihazlarda cihazın gücünü tam kapasite kullanarak devasa miktardaki verilerle çok daha kısa sürede eğitilebilir hale getirmiştir.

2. **Öz-Dikkat (Self-Attention):** Transformer mimarisinin en büyük inovasyonudur. Öz-dikkat modelin uzun bir cümleyi okurken aralarında ne kadar mesafe olursa olsun hangi kelimelerin birbiriyle ilişkili olduğunu eşzamanlı olarak hesaplamasını sağlar.

##### Nasıl Çalışır?

Modele bir soru sorulduğunda transformer, metni makinenin algılayabileceği gibi "token" adı verilen küçük parçalara, ardından da vektörlere dönüştürür. Sonra öz-dikkat mekanizması sayesinde tüm cümlenin bağlam haritasını ve kelimeler arası ilişkileri çıkarır. Son adımda da öğrendiği bu bağlama göre diziye eklenecek bir sonraki en mantıklı kelimenin ne olması gerektiğini hesaplar ve üretir.

Sistem öğrenilmiş istatistiksel olasılıkları kullanarak diziye eklenecek bir sonraki en mantıklı kelimeyi tahmin eder. Üretilen kelime tekrar sisteme dahil edilir ve cevap tamamen bitene kadar sistem bir sonraki kelimeyi tahmin etmeye devam eder.

## AI Ajanlarını Güçlü Kılan Temel Özellikler

### Akıl Yürütme (Reasoning)

Ajanın girdi olarak aldığı verileri ve bağlamı mantık süzgecinden geçirerek anlamlandırma kabiliyeti.

Chain-of-Thought (Düşünce Zinciri) veya ReAct (Reason + Act) şablonları kullanılarak, yapay zekanın eyleme geçmeden önce kendi içinde mantıksal bir çıkarım döngüsü işletmesi sağlanır.

**ReAct (reason + act):** Yapay zekanın düşünme ve eyleme geçme yeteneklerinin bir araya getirildiği bir çerçeve. ReAct paradigmasıyla ajanlara aldıkları her bir araç (tools) yanıtından ve yaptıkları her bir eylemden sonra düşünmeleri ve bir sonraki adımda hangi aracı kullanacaklarına dair plan yapmaları için talimat verilir.

Düşün - Eyleme Geç - Gözlemle adı verilen döngüler halinde çalışır. Bu sayede ajanlar problemleri adım adım çözerek oluşturdukları yanıtları kademeli olarak iyileştirirler.

**Chain-of-Thought:** Ajanların verilen komut sayesinde yavaşça akıl yürütmeleri ve her bir düşünceyi açıkça sergilemeleri yaklaşımıdır.

Ajanın bir soruya nasıl yaklaştığı ve yanıtlarını nasıl formüle ettiği şeffaf bir şekilde görülerek içgörü elde edilebilir.

**Özetle:** ReAct, ajanın dış dünyayla (araçlarla) etkileşime girip sonuçları gözlemlediği eylem döngüsünü sağlarken, Chain-of-Thought bu adımlar atılırken ajanın arka planda "sesli düşünmesini" ve adım adım mantık yürütmesini sağlayan mekanizmadır. İkisi birlikte, ajanların tıpkı bir insan gibi araştırma yapıp sorunları çözmesini mümkün kılar.

### Planlama (Planning)

Verilen karmaşık bir amaca ulaşmak için stratejik bir plan oluşturur, gerekli adımları belirler ve eylemleri daha küçük alt görevlere (subtasks) böler.

Ajan karmaşık bir problemi aldığında tek adımda çözmeye çalışmaz. Adım adım planlama yapar ve bir engelle karşılaştığında planında değişiklik yapabilir.

### Araç Kullanımı (Tool/Function Calling)

Ajanın statik LLM dünyasından çıkıp, dış dünyayla etkileşime girmesi ve destek alması.

### Hafıza (Memory)

Ajanın geçmiş etkileşimleri, kullanıcı tercihlerini ve görev sırasında elde ettiği ara sonuçları saklama ve ihtiyaç anında tekrar çağırma yeteneği.

- **Kısa Süreli Hafıza:** Ajanın o an içinde bulunduğu konuşmanın veya görevin anlık akışını aklında tutma becerisi. Yapay Zeka modellerinin context window (bağlam penceresi) alanını ifade eder. Kullanıcıyla o an yapılan sohbet geçmişi her yeni istekte modele geri beslenir. Bu sayede bir önceki cümlede ne olduğu unutulmaz.

- **Uzun Süreli Hafıza:** Görevler veya oturumlar kapansa bile, ajanın geçmişte öğrendiği bilgileri, kullanıcı tercihlerini ve tarihsel verileri uzun zaman geçse bile hatırlayabilmesi. Veriler vektörel veya ilişkisel veri tabanlarında tutulur. Ajan yeni bir görev aldığında veri tabanında semantik arama yaparak geçmiş bilgileri hafızasına çağırır.

- **Anısal Hafıza:** Ajanın geçmişte gerçekleştirdiği belirli eylemleri, senaryoları ve bu senaryolardan çıkardığı dersleri (başarı veya başarısızlık) birer anı gibi saklaması.

- **Ortak Hafıza:** Çoklu ajan mimarilerinde (multi-agent), farklı ajanların birbirleriyle paylaştıkları ortak bilgi havuzu.

### Otonom Eylem (Autonomy)

Ajanın verilen görevler doğrultusunda insan müdahalesine ve her adımda onay mekanizmasına ihtiyaç duymadan kararlar alıp uygulayabilme özgürlüğüdür.

## Yapay Zeka Ajanı Türleri

Yapay Zeka Ajanları, kapasitelerine, çalışma yapılarına ve kullanıcıyla etkileşim biçimlerine göre çeşitlere ayrılır.

### Kapasite ve Karmaşıklık Düzeylerine Göre

- **Basit Refleks Ajanları:** En basit yapılı ajan türü. Hafızaları yoktur. "Şu an ne görüyorum" sorusuna cevap verirler. Diğer ajanlarla etkileşime girmezler ve sadece anlık algılarına dayanarak belirlenmiş kurallara göre hareket ederler. Beklenmedik durumlara tepki vermezler.

- **Model Tabanlı Refleks Ajanları:** Mevcut algılarını ve hafızalarını kullanarak dış dünyada neler olduğuna dair durum takibi yapabilir, dış dünyanın dahili bir modelini oluşturup güncelleyebilirler. Durum yönetim mekanizması ve hafıza barındırır.

- **Fayda Tabanlı Ajanlar:** Hedefe ulaşmaya değil hedefe en yüksek verimlilik ve faydayla nasıl ulaşabileceğine odaklanır. Bir fayda fonksiyonu işletir. İş akışlarında belirlenmiş sabit kriterlere göre karar verirler.

- **Hedef Tabanlı Ajanlar:** Bir hedef tanımları vardır. Hedefe ulaşmak için eylem dizilerini araştırır ve planlamalar yapar. Planlama yeteneğinin doğduğu yer. Ajan arama ve planlama algoritmalarıyla hedefe giden alternatif yolları hesaplar.

- **Öğrenen Ajanlar:** Kendi başlarına yeni deneyimlerden öğrenerek bilgilerini genişletir ve deneyim kazandıkça performanslarını arttırırlar.

### Etkileşim Biçimine Göre

Ajanlar kullanıcıyla iletişim kurma becerisine göre 2'ye ayrılır:

- **Etkileşimli Ajanlar (Interactive Agents):** Kullanıcıyla doğrudan konuşan, genellikle kullanıcı tetiklenmesiyle çalışan ajanlar.

- **Otonom Arka Plan Süreçleri:** Doğrudan bir girdisi olmadan arka planda çalışan, olaylar veya görevlerle tetiklenen ajanlar.

### Çalışma ve Mimari Yapılarına Göre

- **Tekli Ajanlar:** Belirli bir hedefe ulaşmak için dış kaynakları ve araçları kendi başlarına kullanarak bağımsız ajanlardır. İş birliği gerektirmeyen ve sınırları net çizilmiş görevler için uygundur.

- **Çoklu Ajanlar:** Çok adımlı, büyük görev ve projeler için uygundur. Ortak bir hedef veya rekabet için birbirleriyle iletişim kuran ve uzmanlıklarını birleştiren birden fazla ajandan oluşan sistemlerdir.

## Chatbot ile AI Agent Arasındaki Farklar

Yapay zeka ajanları (AI agents) ile standart sohbet botları (chatbots) arasındaki temel farklar; otonomi seviyeleri, karmaşık görevleri yönetme kapasiteleri, öğrenme yetenekleri ve sistemlerin hedeflere yaklaşım biçimlerinde yatmaktadır.

### Özerklik ve Etkileşim Biçimi

- **Chatbot:** Düşük Otonomi. Reaktif çalışırlar. Eyleme geçmek için önceden programlanmış komutlara, tetikleyicilere veya kullanıcı girdilerine ihtiyaç vardır.
- **AI Agent:** Otonom ve proaktiftirler. Nihai bir hedef doğrultusunda herhangi bir insanın adım adım süreç planlamasına veya müdahale etmesine gerek kalmadan görevleri tamamlamak için bağımsız kararlar alabilir, eyleme geçebilirler.

### Akıl Yürütme ve Görev Planlama

- **Chatbot:** Kural tabanlı veya senaryolaştırılmış mantıkla çalışırlar. Gelen metne en uygun, istatistiksel olarak en mantıklı kelimeleri sıraya dizerek cevap verir. Uzun vadeli planı yoktur.
- **AI Agent:** Gelişmiş akıl yürütme ve stratejik planlama yeteneklerine sahiptir. Düşünce şablonları (ReAct) kullanır. Kendisine verilen karmaşık bir görevi alt parçalara böler ve dış çevreleriyle etkileşime girip değişen durumlara göre esnek şekilde adapte olabilirler.

### Hafıza, Öğrenme ve Kişiselleştirme

- **Chatbot:** Genellikle hafızaları yoktur ve öğrenme kabiliyetleri kısıtlıdır. Bu eksiklik kullanıcı deneyimini kişiselleştirememelerine ve hatalarından ders çıkaramamalarına sebebiyet verir.
- **AI Agent:** Geçmiş etkileşimleri saklayabilen 4 tür hafızaya sahiptir. Bu sayede performanslarını kendi kendilerine iyileştirebilir, kullanıcı davranışlarından öğrenebilir ve zaman geçtikçe çok daha yüksek düzeyde kişiselleştirilmiş deneyimler sunarlar.

### Araç Kullanımı (Tool Calling)

- **Chatbot:** Bilgi eksikliklerini kapatabilecek dış araçlara veya sistemlere erişim sağlayamazlar.
- **AI Agent:** Dış dünyayla etkileşime girmek ve kendilerini güncellemek için otonom şekilde dış araç veya sistemlere erişim sağlayabilirler.

## Agent Neden Sadece Prompt Yazan Bir Sistem Değildir?

Yapay zeka araçlarının yalnızca prompt yazan sistemler olmamasının temel nedeni, promptun sadece tek seferlik ve pasif bir talimat olması, ajanın ise kendi hedeflerini gerçekleştirebilen, kararlar alan, dış araçları kullanabilen ve çevreyle iletişime geçebilen otonom bir mimari olmasıdır.

Bir yapay zeka ajanını basit bir prompt tabanlı sistemden ayıran temel özellikler:

En önemli farklardan biri, prompt oluşturma ve işlemenin, ajan mimarisinin tamamı değil, sadece alt bir parçası olmasıdır. Hedef odaklı çalışan bir ajan, dışarıdan prompt beklemek yerine gerekli promptları kendisi üretir.

Prompt modele sadece belirli bir anda ne yapması gerektiğini söyleyen ve insan müdahalesine bağımlı bir komuttur. Ajanlar ise tamamen otonomdur ve hedeflerine ulaşmak için alınması gereken kararları kendileri alırlar ve uygularlar.

Prompt tabanlı etkileşimler yapıları gereği genellikle durumsuzdur, yani sistemin geçmişi hatırlama zorunluluğu yoktur. Her komut sisteme ilk kez görülüyormuş gibi işlenir. Yapay zeka ajanları ise 4 tür hafıza olmak üzere çok yapılı bellek yapılarına sahiptir. Bu sayede bir görev gerçekleştirildiği süre boyunca bağlamı korurlar, geçmiş eylemlerden ders çıkarırlar ve güncel duruma göre hareket edebilirler.

Bir prompt yalnızca dil modelinin içerisine hapsolmuş bir metin dizisidir, dış dünyadan etkilenemez. Ajanlar ise dış uygulamalara ve sistemlere bağlanmış otonom yapılardır.

Prompt tekil ve anlıktır. Verilen komuta tek bir cevap üretilir ve işlem sonlandırılır. Ajanlar ise ReAct gibi paradigmalar sayesinde sürekli olarak algılama, karar verme ve eylem döngüsü içinde çalışırlar.

Özetle prompt; bir modele ne yapması gerektiğini anlatan metin tabanlı statik bir komutken, yapay zeka ajanı; bu komutları kendi başına organize eden, durumunu güncelleyen, dış dünyayla veri alışverişi yapan kompleks bir yazılımdır.

## Agent Mimarisinin Temel Parçaları

**Agent:** Belirli bir hedefi gerçekleştirmek için çevresini algılayabilen, kararlar alabilen ve dış dünyada eyleme geçebilen otonom bir sistemdir. Her ajanın kendine ait bir rolü, içsel durumu ve ulaşmak istediği hedefi vardır.

**Tool:** Ajanların dış çevreyle etkileşime girmek ve kapasitelerini arttırmak için kullandıkları dış kaynaklar veya işlevlerdir. Güncel bilgilere ulaşmak veya dijital eylemler gerçekleştirmek için veritabanları, web aramaları, API'ler, grafiksel veya program tabanlı arayüzler veya diğer ajanlar gibi araçları kullanabilirler. Bu araçların otonom bir şekilde çağrılması ve kullanılması (tool calling) ajanların gerçek dünyadaki problemleri çözmesini mümkün kılar.

**Memory:** Ajanların görev süresince bağlamı korumasını, geçmiş deneyimlerden öğrenmesini ve zamanla uyum sağlayarak kendini geliştirmesini sağlayan temel bileşendir. Bu mekanizma sayesinde ajanlar hatalarını tekrarlamaz, kullanıcı tercihlerine adapte olur ve çok daha isabetli, kişiselleştirilmiş davranışlar gerçekleştirir.

**Workflow:** İş akışları, ajanın karmaşık bir problemi çözmek ve amaca ulaşmak için tasarladığı ve sıraya koyduğu otonom görev adımları. Süreç; bir planın oluşturulması, görevin alt görevlere ayrılması ve eyleme geçilmesi ile başlar. İş akışları akıl yürütme paradigmaları ile yönetilebilir. İş akışları aynı zamanda çoklu ajan sistemlerini de kapsayabilir.

**MCP:** Yapay zeka uygulamalarının dış sistemlere, veri kaynaklarına ve araçlara bağlanmasını sağlayan açık kaynaklı ve standartlaştırılmış bir iletişim protokolüdür.

## MCP (Model Context Protocol)

Elektronik cihazları birbirine bağlayan evrensel bir USB-C gibi çalışır. Yapay zeka modellerinin dış sistemlerle standart bir yolla etkileşime girmesini sağlar.

Büyük dil modellerinin (LLM) en büyük kısıtlaması, statik olmaları yani eğitildikleri bilgilerle sınırlı kalmaları ve dış dünyayla otonom olarak iletişime geçememeleridir. MCP bu kısıtlamaları ortadan kaldıran bir köprü görevi görür.

Yapay zekanın eğitildiği tarihte kalan statik bilgilere bağımlı olmaktan kurtulup, dış kaynaklardan gerçek zamanlı veriler çekerek bilgi eksikliklerini tamamlamasını ve kendini güncellemesini sağlayan önemli standartlardan biri MCP'dir. Ancak MCP, sadece büyük dil modelleriyle sınırlı kapalı bir kutu değildir; tamamen açık kaynaklı ve evrensel bir protokoldür.

### Temel Mimari ve Çalışma Prensibi

3 temel bileşenden oluşur:

**MCP Host (Ana Sistem):** Modelin ve kullanıcının etkileşime girdiği katmandır. LLM'i ve kullanıcının etkileşime geçtiği arayüzü barındırır. Arka planda bir veya daha fazla MCP Client çalıştırır.

**MCP Client (İstemci):** Host içinde çalışır. Modelin isteklerini MCP'nin anlayacağı formata, MCP'nin isteklerini modelin anlayacağı formata çevirir. Ayrıca kullanılabilir MCP sunucularını bulur. Genellikle kullanılan agent framework'ünün içine gömülü bir kütüphane veya SDK olarak çalışır.

**MCP Server (Sunucu):** LLM'e bağlam, veri veya dış araç yetenekleri sağlayan harici hizmettir. Dış dünyadaki veri kaynaklarını veya araçları, protokolün anladığı ortak dile çeviren küçük, izole edilmiş servislerdir.

### Neler Sağlar ve Neden Önemlidir

- Güvenilir ve gerçek zamanlı dış veri kaynaklarına bağlanmalarını sağlayarak, LLM'lerin sadece eğitim verilerine dayanarak halüsinasyon yaşamasını engeller.
- Yapay zekayı sadece soru metin üreten bir sohbet botu olmaktan çıkarıp, gerçek otonomiyi mümkün kılar.
- Tek ve standart bir protokol sunarak dağınık entegrasyon süresini ortadan kaldırır. Bu sayede geliştirme süresi, maliyetler ve karmaşıklık azaltılır.
- Standart ve açık kaynaklı olduğu için ana sistemde büyük değişiklikler yapılmadan model değişikliğini mümkün kılar.
