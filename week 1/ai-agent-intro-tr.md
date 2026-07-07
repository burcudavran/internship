# Hafta 1: Temel Kavramlar ve Microsoft Agent Framework'e Giriş

## AI Agent Nedir?

Karmaşık görevleri ve belirli hedefleri yerine getirmek için yapay zeka kullanılan, müdahale gerektirmeden kendi başına karar alabilen (özerk) yazılımlardır. Karar verme, problem çözme, dış ortamlarla etkileşime girme ve hedefe yönelik eylemleri gerçekleştirme gibi geniş kapsamlı yeteneklere sahiptir.

Temelinde Büyük Dil Modellerini (LLM) barındırır. Bu sayede metin, ses, video, kod gibi çok modlu verileri işleyebilir. Ancak geleneksel LLM'ler statiktir; yalnızca eğitildikleri veriler ile sınırlıdırlar. Canlı veri veya otonom eyleme geçemezler.

AI Agentler ise dinamik yapıya sahiptirler; LLM'in akıl yürütme becerisini arka planda araç çağırma (tool/function calling), hafıza (memory) ve dinamik iş akışları (workflow) ile birleştirir ve eğitildiği verilerin ötesine geçer. Bu sayede otonom ve karmaşık verileri yerine getirebilirler.

**Tool Calling:** Yapay zeka araçlarının kapasitelerini genişletmek, çevreleriyle etkileşime girmek ve görevleri yerine getirmek amacıyla harici sistemlere veya kaynaklara otonom başvurmasıdır.

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

- **Ortak Hafıza:** Çoklu ajan mimarilerinde (multi-agent) mimarilerinde, farklı ajanların birbirleriyle paylaştıkları ortak bilgi havuzu.

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

- **Yüzey Ajanları / Etkileşimli Ortaklar:** Kullanıcıyla doğrudan konuşan, genellikle kullanıcı tetiklenmesiyle çalışan ajanlar.

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
