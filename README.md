# NAFDL_dataset_processing_modelling

Veriseti tanıtımı ve proje amacı
Bu projede, Kaggle'dan aldığımız "Non-Alcoholic Fatty Liver Disease" (NAFLD) veri setiyle çalıştık. Veri setimizde birden fazla hedef değişken vardı. Dengesiz dağılıma ve bolca Null değere sahip bir veri setiydi. Veri setimizde birden fazla hedef değişken adayı bulunmaktaydı. Amacımız, elimizdeki sağlık verilerini kullanarak hastanın “siroz olup olmadığını”, “ağır-hafif hasta olup olmadığını” veya “karaciğer hastalığını türünü” sınıflandırmaya çalışmaktı.
Veri seti, insanların yaşını, cinsiyetini, vücut kitle indeksi, kan basıncı, siroz hastası olup olmadığı, vücudundaki çeşitli maddelerin, bileşiklerin olup olmadığı gibi özellikleri içeriyordu. 

________________________________________
Veri Seti ve İlk İşlemler
Veri seti toplam 605 index ve 62 tane farklı özellikten oluşmaktaydı. Tüm veriler nümerik olduğu için herhangi bir encoding işlemi yapılmadı. 
İlk olarak, veri okuryazarlığı ile verisetinin hikayesini, verisetindeki kolonların anlamlarını anlamaya çalışıldı.
Daha sonra eksik veriler tespit edildi. “Null” değerleri doldurmak için Random Forest Regression algoritması kullanıldı. Ve tüm null değerleri null olmayan kolonlardan tahmin yapıp dolduruldu.
Sonrasında, sınıflandırma için önemli olabilecek özelliklere odaklanıldı. Verileri normalize ettik ve uygun şekilde ölçeklendirildi. 

________________________________________
Model oluşturma ve değerlendirme
Projedeki hedef özelliklerimiz için Naive Bayes, KNN, CART, RF, GB, AdaB, XGB, CatB gibi farklı modeller denendi.
Naive Bayes algoritması özelliklerin birbirinden bağımsız olduğunu varsayıyor ama bu her zaman geçerli olmuyor. Bu sebeple en düşük doğruluk değerini bu model verdi. KNN en yakın komşuluk algoritması da en düşük ikinci sonucu verdi. Karar Ağaçları veriyi, özelliklere göre ağaç yapısına yerleştiriyor. Anlaması ve yorumlaması kolay bir modeldir ama yine de orta bir seviye sonuç verdi. SVM algoritması da orta bir derecede sonuç verdi.En iyi accuracy recall precision f1 score değerlerini “ensemble learning(kolektif öğrenme) algoritmaları” verdi. Random forest( birçok karar ağacının tahminlerinin ortalamasını veya çoğunluk oylamasını alan bir model), Gradient Boosting( model sonuçlarının hata değerlerine odaklanıp her iterasyonda ceza parametresi uygulayarak hata azaltmaya çalışan bir model) “AdaBoost, XGBoost, CatBoost” gibi modeller en iyi sonucu verdi.
Ayrıca verisetine “Stratified K-Fold Cross-Validation” işlemi uygulandı. Bu sayede dengesiz veri setimiz için daha iyi bir model sonucu almış olduk.
Kurulan modeller sonucunda “Activity”, “Type of Disease”, NAS score” gibi özellikler belirleyici özellikler olduğunu gösterdi.
Performansı ölçmek için doğruluk, F1 skoru, precision, recall, classification report tablosuyla kıyaslandı.

Stratified K-Fold Cross-Validation F1 score sonuçları:
KNN: %96.69				 Naive Bayes: %91.24
Karar Ağaçları: %98.35	                SVM: %98.51         Gradient Boosting: %98.84 	         Random Forest: %99.01                     AdaBoost: %99.17		
XGBoost: %99.17 		               CatBoost: %99.17 
En yüksek başarıyı CatBoost, AdaBoost, XGBoost, Random Forest gibi kolektif öğrenme modelleri yakaladı (%99 civarında doğruluk). Özellikle bu yöntemler, birden fazla modelin gücünü bir araya getirdiği için daha sağlam sonuçlar verdi.

________________________________________

Bu projede, NAFLD veri seti üzerinde yaptığımız birden fazla değişkene yönelik sınıflandırma çalışmasında en iyi sonuçları Random Forest, AdaBoost, CatBoost ve XGBoost gibi ensemble learning yöntemleri verdi. 
Bazı başarısızlıklar; veri dengesizliği, veri kısıtlılığı ya da eksik verilerin yanlış tamamlanması gibi sebeplerden kaynaklanmış olabilir. Çeşitli yöntemlerle veri artırma ya da hiperparametre optimizasyonu yaparak bu sorunlar azaltılabilir.
________________________________________

![image](https://github.com/user-attachments/assets/0e7bab58-ea2e-477d-b7be-84df6d3b8099)

![image](https://github.com/user-attachments/assets/1d5fc331-02d3-4f24-986a-732e7f5de7e0)





 


