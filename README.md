# NAFDL_dataset_processing_modelling

Veriseti tanıtımı ve proje amacı
Bu projede, Kaggle'dan aldığımız "Non-Alcoholic Fatty Liver Disease" (NAFLD) veri setiyle çalıştık. Veri setimizde birden fazla hedef değişken vardı ve dengesiz dağılıma sahip bir veri setiydi. Amacımız, elimizdeki sağlık verilerini kullanarak hastanın “siroz olup olmadığını”, “ağır-hafif hasta olup olmadığını” veya “karaciğer hastalığını türünü” sınıflandırmaya çalışmaktı. Yani bir nevi, ilgili hastalık var mı yok mu ya da ne kadar ciddi bir durumda, bunu tahmin etmeye çalıştık. 
Veri seti, insanların yaşını, cinsiyetini, vücut kitle indeksi, kan basıncı, siroz hastası olup olmadığı, vücudundaki çeşitli maddelerin, bileşiklerin olup olmadığı gibi özellikleri içeriyordu. 
Veri setimizde birden fazla hedef değişken adayı bulunmaktaydı. 
“Type of Disease (Mild illness=1, Severe illness=2)”
“Cirrhosis (No=0, Yes=1) (If Fibrosis is 4, there is Cirrhosis)”
“Diagnosis according to SAF (NASH=1, NAFL=2)”
Gibi hedef değişken adayı olabilecek kolonlar için ayrı ayrı tahmin modelleri geliştirildi.
Ayrıca hedef değişken dediğimiz, karaciğer hastalığı durumunu ya da seviyesini, siroz hastalığı vb. belirten sınıflar var. Bu çalışmada, veriyi temizleyip güzelce analiz ederek, farklı sınıflandırma yöntemleriyle sonuçlara ulaşmayı hedefledik.
________________________________________
Veri Seti ve İlk İşlemler
Elimizde toplam 605 tane satır ve 62 tane farklı sütundan oluşmaktaydı. Tüm veriler nümerik olduğu için herhangi bir encoding işlemi yapmadık. 
İlk olarak, veri okuryazarlığı ile verisetinin hikayesini, verisetindeki kolonların anlamlarını anlamaya çalıştık.
Daha sonra eksik verileri tespit ettik. Bu “Null” değerleri doldurmak için Random Forest Regression algoritmasından yardım aldık. Ve tüm null değerleri null olmayan kolonlardan tahmin yapıp doldurduk.
Sonrasında, sınıflandırma için önemli olabilecek özelliklere odaklandık. Verileri normalize ettik ve uygun şekilde ölçeklendirdik. 
Model oluşturma ve değerlendirme
Projedeki hedef özelliklerimiz için VMG dersinde öğrendiğimiz, bildiğimiz tüm farklı sınıflandırma algoritmalarını denedik. Naive Bayes, KNN, CART, RF, GB, AdaB, XGB, CatB gibi.
Naive Bayes algoritması özelliklerin birbirinden bağımsız olduğunu varsayıyor ama bu her zaman geçerli olmuyor. Bu sebeple en düşük doğruluk değerini bu model verdi. KNN en yakın komşuluk algoritması da en düşük ikinci sonucu verdi. Karar Ağaçları veriyi, özelliklere göre ağaç yapısına yerleştiriyor. Anlaması ve yorumlaması kolay bir modeldir ama yine de orta bir seviye sonuç verdi. SVM algoritması da orta bir derecede sonuç verdi.En iyi accuracy recall precision f1 score değerlerini “ensemble learning( kolektif öğrenme) algoritmaları” verdi. Random forest( birçok karar ağacının tahminlerinin ortalamasını veya çoğunluk oylamasını alan bir model), Gradient Boosting( model sonuçlarının hata değerlerine odaklanıp her iterasyonda ceza parametresi uygulayarak hata azaltmaya çalışan bir model) “AdaBoost, XGBoost, CatBoost” gibi modeller en iyi sonucu verdi.
Ayrıca verisetine “n fold cross validation” işlemi uyguladın ve n değerini 5 aldık. Bu sayede dengesiz veri setimiz için daha iyi bir model sonucu almış olduk.
Kurulan modeller sonucunda “Activity”, “Type of Disease”, NAS score” gibi özellikler belirleyici özellikler olduğunu gösterdi.
Performansı ölçmek için doğruluk (accuracy), F1 skoru, precision, recall, classification report gibi metrikler kullandık.

Accuracy sonuçları:
KNN: %96.69				 Naive Bayes: %91.24
Karar Ağaçları: %98.35	                SVM: %98.51         Gradient Boosting: %98.84 	         Random Forest: %99.01                     AdaBoost: %99.17		
XGBoost: %99.17 		               CatBoost: %99.17 
En yüksek başarıyı CatBoost, AdaBoost, XGBoost, Random Forest gibi kolektif öğrenme modelleri yakaladı (%99 civarında doğruluk). Özellikle bu yöntemler, birden fazla modelin gücünü bir araya getirdiği için daha sağlam sonuçlar verdi.
Diğer hedef değişkenler üzerine yapılan model sonuçları da aynı şekilde %99 civarında oldu.

________________________________________

Bu projede, NAFLD veri seti üzerinde yaptığımız birden fazla değişkene yönelik sınıflandırma çalışmasında en iyi sonuçları Random Forest, AdaBoost, CatBoost ve XGBoost verdi. Bu da ansamble yöntemlerin ne kadar güçlü olduğunu gösteriyor.
Bazı başarısızlıklar, veri dengesizliği, veri kkısıtlılığı ya da eksik verilerin yanlış tamamlanması gibi şeylerden kaynaklanmış olabilir. Çeşitli yöntemlerle veri artırma ya da hiperparametre optimizasyonu yaparak bu sorunlar azaltılabilir.
Bu tarz tahmin projeleri birçok seneryoya uygulanabilir ve hayatımızı kolaylaştırabilir. 
________________________________________

![image](https://github.com/user-attachments/assets/0e7bab58-ea2e-477d-b7be-84df6d3b8099)

![image](https://github.com/user-attachments/assets/1d5fc331-02d3-4f24-986a-732e7f5de7e0)





 


