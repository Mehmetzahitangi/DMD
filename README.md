# ✈️ Dynamic Mode Decomposition (DMD)

Bu repo, otonom sistemler ve veri güdümlü kontrol (Data-Driven Control) alanında kullanılan **Dinamik Mod Ayrışımı (DMD)** algoritmalarının Python implementasyonlarını içermektedir. 

Kodlar, J. Nathan Kutz ve ekibinin *"Dynamic Mode Decomposition: Data-Driven Modeling of Complex Systems (2016)"* kitabındaki teorik temeller üzerine inşa edilmiştir. Bu çalışmalar, özellikle Derin Pekiştirmeli Öğrenme (Deep RL) ajanlarının doğrusal olmayan aerodinamik ortamları algılaması, rüzgar gürültüsünü filtrelemesi ve donanım limitlerini aşması için optimize edilmiştir.

## 🚀 Proje Bağlamı ve Otonom Havacılık

Klasik bir RL ajanı, karmaşık ortamları anlamak için milyonlarca deneme-yanılma (trial-and-error) yapar ve kara kutu (Black-box) sinir ağları kullanır. Bu repo, uçağın sensörlerinden gelen verileri (Pikseller, Hız, İrtifa) alıp, arka planda çalışan **Koopman Operatör Teorisi** ve **DMD** algoritmalarıyla doğrudan sistemin matematiksel "Fizik Kurallarını" (Özdeğerler ve Modlar) çıkaran beyaz kutu (White-box) çözümler sunar.

## 📂 İçerik ve Uygulanan Algoritmalar

Depodaki kodlar kitaptaki bölümlere göre modülerize edilmiştir:

### 🕰️ Bölüm 7: Gecikme Koordinatları (Delay Coordinates) ve ERA
* **Hankel DMD (Time-Delay Embedding):** Kısmi gözlemlenebilir ortamlarda (POMDP) ajanın "Frame Stacking" mantığıyla gizli dinamikleri (örn: Duran Dalga) bulması.
* **Eigensystem Realization Algorithm (ERA):** NASA'nın geliştirdiği, tek bir sensör verisinden (Dürtü Yanıtı) uçağın tam fizik modelini (`A, B, C` matrisleri) geri çatma algoritması.
* **Hidden Markov Models (HMM) & DMD:** Rastgele ve olasılıksal ortamlardan kararlı durum frekanslarını çıkarma.

### 🛡️ Bölüm 8: Gürültü Filtreleme (Noise & Power)
* **Optimal Singular Value Thresholding:** Gavish-Donoho eşikleme formülü ile sensör verisindeki gürültü denizini (Noise Floor) matematiksel olarak yararak uçağın gerçek aerodinamiğini bulma.
* **fbDMD (İleri/Geri DMD) & tlsDMD (Total Least-Squares):** Sensör gürültüsünün yarattığı "Yapay Sönümlenme" (Spurious Damping) hatasını sıfırlayan ortogonal regresyon teknikleri.

### 🗜️ Bölüm 9: Sıkıştırılmış Algılama (Sparsity & cDMD)
* **Compressed Sensing (CS) DMD:** Nyquist hız sınırının çok altında, rastgele ve çok az sensör ölçümüyle (örn: 100.000 piksel yerine 300 nokta sensörü) yüksek çözünürlüklü frekansları yakalama.
* **Sparsity-Promoting DMD (spDMD):** L1 Optimizasyonu (LASSO mantığı) kullanarak yüzlerce fiziksel kuralı çöpe atıp, uçağı yöneten en kritik 3-4 temel kuralı (Sparse Modları) seçme.

### 🌌 Bölüm 10: Doğrusal Olmayan Dinamikler ve Koopman Teorisi
* **Extended DMD (EDMD):** Uçağın doğrusal olmayan (Nonlinear) şok dalgalarını veya kaotik hareketlerini, Gözlem Sözlükleri (Observable Dictionaries) kullanarak yüksek boyutlu doğrusal (Linear) bir uzaya taşıma.
* **Kernel DMD:** Boyutluluk lanetini (Curse of Dimensionality) aşarak, devasa özellik uzaylarındaki Koopman matrisini sadece iç çarpım (Gram) matrisleri kullanarak saniyeler içinde çözme.

## 🛠️ Kurulum

Kodlar Python 3.8+ ortamında geliştirilmiş olup, ağır donanım gerektirmez (SVD işlemleri optimize edilmiştir). Gerekli kütüphaneleri yüklemek için:


## 📚 Referanslar

Bu depodaki matematiksel altyapı aşağıdaki temel esere dayanmaktadır:

Kutz, J. N., Brunton, S. L., Brunton, B. W., & Proctor, J. L. (2016). Dynamic Mode Decomposition: Data-Driven Modeling of Complex Systems. SIAM.
