# Employee Attrition Prediction Model

> **Note:** This documentation is provided in both English and Turkish. English version comes first, followed by the Turkish translation.
> 
> **Not:** Bu dokümantasyon hem İngilizce hem de Türkçe olarak hazırlanmıştır. Önce İngilizce versiyon, ardından Türkçe çevirisi yer almaktadır.

---

# 🇬🇧 English Version

## 📋 Project Overview

Hi, I'm **Emre**! This is my graduation project for the **Tech Istanbul Machine Learning Bootcamp**. The goal of this project is to predict employee attrition (whether an employee will leave the company or not) using various machine learning techniques. I wanted to build something that could actually be useful in a real HR department, so I focused on making the model not just accurate, but also interpretable and deployable.

Employee turnover is a significant challenge for companies - it costs time, money, and institutional knowledge. By predicting which employees are at risk of leaving, HR teams can take proactive measures to improve retention. That's the real-world problem I'm trying to solve here.

## 🎯 Problem Statement

The objective is to develop a binary classification model that predicts whether an employee will leave the company (Attrition = "Yes") or stay (Attrition = "No"). The dataset comes from IBM HR Analytics, containing information about 1,470 employees with 35 different features covering demographics, job characteristics, and satisfaction metrics.

**Key Challenges:**
- Class imbalance (~16% attrition rate)
- Mix of numerical and categorical features
- Need for interpretable results (HR teams need to understand WHY)

## 🛠️ Technologies Used

### Core Libraries

| Library | Version | Why I Chose It |
|---------|---------|----------------|
| **Python** | 3.10 | Stable version with great ML ecosystem support |
| **pandas** | 2.3.3 | Industry standard for data manipulation. The DataFrame structure makes EDA intuitive |
| **numpy** | 2.2.6 | Foundation for numerical computing. Essential for array operations |
| **scikit-learn** | 1.7.2 | The go-to library for classical ML. Has everything from preprocessing to model evaluation |
| **matplotlib** | 3.10.8 | Flexible plotting library. When I need full control over visualizations |
| **seaborn** | 0.13.2 | Built on matplotlib but makes statistical visualizations much easier |

### Advanced ML Libraries

| Library | Version | Why I Chose It |
|---------|---------|----------------|
| **XGBoost** | 3.1.2 | Gradient boosting powerhouse. Often wins Kaggle competitions. Great for tabular data |
| **LightGBM** | 4.6.0 | Faster training than XGBoost with similar performance. Uses histogram-based algorithms |
| **CatBoost** | 1.2.8 | Handles categorical features natively. No need for manual encoding |
| **imbalanced-learn** | 0.14.1 | Essential for handling class imbalance. SMOTE implementation is excellent |
| **SHAP** | 0.49.1 | Model interpretability is crucial for HR. SHAP values explain individual predictions |

### Why These Specific Choices?

1. **Multiple Boosting Libraries (XGBoost, LightGBM, CatBoost):** I wanted to compare different gradient boosting implementations. Each has its strengths - XGBoost is well-documented, LightGBM is fast, and CatBoost handles categories elegantly.

2. **SHAP for Interpretability:** In HR, you can't just say "the model predicts this person will leave." You need to explain WHY. SHAP provides local explanations for each prediction.

3. **imbalanced-learn:** With only 16% positive class, standard algorithms would be biased. SMOTE helps create a balanced training set.

## 📊 Dataset Description

**Source:** IBM HR Analytics Employee Attrition Dataset  
**Size:** 1,470 employees × 35 features  
**Target Variable:** Attrition (Yes/No)

### Feature Categories

- **Demographics:** Age, Gender, MaritalStatus, Education
- **Job Characteristics:** Department, JobRole, JobLevel, YearsAtCompany
- **Compensation:** MonthlyIncome, StockOptionLevel, PercentSalaryHike
- **Satisfaction Metrics:** JobSatisfaction, EnvironmentSatisfaction, WorkLifeBalance
- **Work Patterns:** OverTime, BusinessTravel, DistanceFromHome

## 🔧 Project Pipeline

```
1. Data Loading & Initial Exploration
         ↓
2. Exploratory Data Analysis (EDA)
   - Univariate Analysis
   - Bivariate Analysis
   - Correlation Analysis
   - Statistical Significance Tests
         ↓
3. Feature Engineering (25 new features created!)
   - Tenure ratios
   - Satisfaction indices
   - Career progression metrics
   - Risk indicators
         ↓
4. Preprocessing Pipeline
   - Numerical: StandardScaler
   - Nominal Categorical: OneHotEncoder
   - Ordinal Categorical: OrdinalEncoder
         ↓
5. Handling Class Imbalance (SMOTE)
         ↓
6. Model Development (12 algorithms tested)
         ↓
7. Hyperparameter Tuning (RandomizedSearchCV)
         ↓
8. Model Evaluation & Selection
         ↓
9. Ensemble Methods (Voting, Stacking)
         ↓
10. Model Interpretation (SHAP)
         ↓
11. Business Insights & Recommendations
         ↓
12. Model Export for Deployment
```

## 📈 Models Evaluated

I tested 12 different classification algorithms:

1. Logistic Regression
2. Random Forest
3. XGBoost
4. LightGBM
5. CatBoost
6. Gradient Boosting
7. AdaBoost
8. Support Vector Machine (SVM)
9. K-Nearest Neighbors (KNN)
10. Naive Bayes
11. Decision Tree
12. Extra Trees

### Evaluation Metrics

Since we have class imbalance, accuracy alone isn't enough. I focused on:

- **ROC-AUC:** Overall discriminative ability
- **Recall:** Important because missing an employee who will leave is costly
- **Precision:** Avoiding false alarms that waste HR resources
- **F1-Score:** Balance between precision and recall

## 🚀 How to Run

### Prerequisites

```bash
# Create virtual environment
python -m venv venv

# Activate (Windows)
.\venv\Scripts\Activate.ps1

# Activate (Linux/Mac)
source venv/bin/activate
```

### Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost lightgbm catboost imbalanced-learn shap jupyter ipykernel jinja2
```

### Run the Notebook

```bash
jupyter notebook Project.ipynb
```

Or open directly in VS Code with the Jupyter extension.

## 📁 Project Structure

```
KaggleProject/
├── Project.ipynb              # Main notebook with full analysis
├── README.md                  # This documentation
├── WA_Fn-UseC_-HR-Employee-Attrition.csv  # Dataset
├── attrition_model.joblib     # Trained model (for deployment)
├── preprocessor.joblib        # Fitted preprocessing pipeline
├── feature_importance.csv     # Feature importance rankings
├── model_metadata.json        # Model configuration and metrics
├── AI.MD                      # AI assistant notes
├── catboost_info/             # CatBoost training logs
└── venv/                      # Python virtual environment
```

## 📊 Key Findings

Based on my analysis:

1. **OverTime** is the strongest predictor - employees working overtime are much more likely to leave
2. **Job Satisfaction** and **Environment Satisfaction** matter significantly
3. **Years at Company** shows a non-linear relationship - very new and very senior employees behave differently
4. **Monthly Income** relative to job level affects attrition risk
5. **Work-Life Balance** is crucial, especially combined with overtime

## 💡 Business Recommendations

1. **Monitor Overtime:** Implement policies to prevent burnout
2. **Regular Satisfaction Surveys:** Track job and environment satisfaction
3. **Career Development:** Clear progression paths reduce attrition
4. **Competitive Compensation:** Especially for high-performers at risk
5. **Early Warning System:** Use this model to flag at-risk employees

## 🔮 Future Improvements

- [ ] Deploy as a web application (Flask/FastAPI)
- [ ] Add real-time prediction API
- [ ] Implement model monitoring for drift detection
- [ ] A/B test HR interventions suggested by the model
- [ ] Collect more data to improve predictions

## 📜 License

This project is created for educational purposes as part of Tech Istanbul Machine Learning Bootcamp.

## 🙏 Acknowledgments

- **Tech Istanbul** for the excellent machine learning bootcamp
- **IBM** for providing the HR Analytics dataset
- The open-source community for the amazing libraries

---

# 🇹🇷 Türkçe Versiyon

## 📋 Proje Özeti

Merhaba, ben **Emre**! Bu proje, **Tech Istanbul Makine Öğrenmesi Bootcamp** bitirme projem. Projenin amacı, çeşitli makine öğrenmesi teknikleri kullanarak çalışan kaybını (bir çalışanın şirketten ayrılıp ayrılmayacağını) tahmin etmek. Gerçek bir İK departmanında kullanılabilecek bir şey yapmak istedim, bu yüzden modelin sadece doğru değil, aynı zamanda yorumlanabilir ve üretime alınabilir olmasına odaklandım.

Çalışan devir hızı şirketler için önemli bir zorluk - zaman, para ve kurumsal bilgi kaybına neden oluyor. Hangi çalışanların ayrılma riski altında olduğunu tahmin ederek, İK ekipleri elde tutmayı iyileştirmek için proaktif önlemler alabilir. İşte çözmeye çalıştığım gerçek dünya problemi bu.

## 🎯 Problem Tanımı

Amaç, bir çalışanın şirketten ayrılıp (Attrition = "Yes") ayrılmayacağını (Attrition = "No") tahmin eden bir ikili sınıflandırma modeli geliştirmek. Veri seti IBM İK Analitik'ten geliyor ve demografik bilgiler, iş özellikleri ve memnuniyet metrikleri dahil 35 farklı özelliğe sahip 1.470 çalışan hakkında bilgi içeriyor.

**Temel Zorluklar:**
- Sınıf dengesizliği (~%16 işten ayrılma oranı)
- Sayısal ve kategorik özelliklerin karışımı
- Yorumlanabilir sonuçlara ihtiyaç (İK ekipleri NEDEN'i anlamak istiyor)

## 🛠️ Kullanılan Teknolojiler

### Temel Kütüphaneler

| Kütüphane | Versiyon | Neden Seçtim |
|-----------|----------|--------------|
| **Python** | 3.10 | ML ekosistemi desteği mükemmel olan kararlı versiyon |
| **pandas** | 2.3.3 | Veri manipülasyonu için endüstri standardı. DataFrame yapısı EDA'yı sezgisel yapıyor |
| **numpy** | 2.2.6 | Sayısal hesaplama temeli. Dizi işlemleri için şart |
| **scikit-learn** | 1.7.2 | Klasik ML için başvuru kütüphanesi. Ön işlemeden model değerlendirmeye her şey var |
| **matplotlib** | 3.10.8 | Esnek çizim kütüphanesi. Görselleştirmeler üzerinde tam kontrol gerektiğinde |
| **seaborn** | 0.13.2 | matplotlib üzerine kurulu ama istatistiksel görselleştirmeleri çok daha kolay yapıyor |

### İleri ML Kütüphaneleri

| Kütüphane | Versiyon | Neden Seçtim |
|-----------|----------|--------------|
| **XGBoost** | 3.1.2 | Gradient boosting gücü. Kaggle yarışmalarını sık kazanır. Tablo verisi için harika |
| **LightGBM** | 4.6.0 | XGBoost'tan daha hızlı eğitim, benzer performans. Histogram tabanlı algoritmalar kullanıyor |
| **CatBoost** | 1.2.8 | Kategorik özellikleri doğal olarak işliyor. Manuel kodlama gerek yok |
| **imbalanced-learn** | 0.14.1 | Sınıf dengesizliğini ele almak için şart. SMOTE implementasyonu mükemmel |
| **SHAP** | 0.49.1 | Model yorumlanabilirliği İK için kritik. SHAP değerleri bireysel tahminleri açıklıyor |

### Neden Bu Özel Seçimler?

1. **Birden Fazla Boosting Kütüphanesi (XGBoost, LightGBM, CatBoost):** Farklı gradient boosting implementasyonlarını karşılaştırmak istedim. Her birinin güçlü yanları var - XGBoost iyi dokümante edilmiş, LightGBM hızlı, CatBoost kategorileri zarif şekilde işliyor.

2. **Yorumlanabilirlik için SHAP:** İK'da sadece "model bu kişinin ayrılacağını tahmin ediyor" diyemezsiniz. NEDEN'i açıklamanız gerekiyor. SHAP her tahmin için yerel açıklamalar sağlıyor.

3. **imbalanced-learn:** Sadece %16 pozitif sınıfla, standart algoritmalar önyargılı olurdu. SMOTE dengeli bir eğitim seti oluşturmaya yardımcı oluyor.

## 📊 Veri Seti Açıklaması

**Kaynak:** IBM İK Analitik Çalışan Kaybı Veri Seti  
**Boyut:** 1.470 çalışan × 35 özellik  
**Hedef Değişken:** Attrition (Evet/Hayır)

### Özellik Kategorileri

- **Demografik:** Yaş, Cinsiyet, MedeniDurum, Eğitim
- **İş Özellikleri:** Departman, İşRolü, İşSeviyesi, ŞirkettekiYıllar
- **Ücret:** AylıkGelir, HisseSenediSeçenekSeviyesi, MaaşArtışYüzdesi
- **Memnuniyet Metrikleri:** İşMemnuniyeti, OrtamMemnuniyeti, İşYaşamDengesi
- **Çalışma Düzenleri:** FazlaMesai, İşSeyahati, EvdenUzaklık

## 🔧 Proje İş Akışı

```
1. Veri Yükleme & İlk Keşif
         ↓
2. Keşifsel Veri Analizi (EDA)
   - Tek Değişkenli Analiz
   - İki Değişkenli Analiz
   - Korelasyon Analizi
   - İstatistiksel Anlamlılık Testleri
         ↓
3. Özellik Mühendisliği (25 yeni özellik oluşturuldu!)
   - Görev süresi oranları
   - Memnuniyet endeksleri
   - Kariyer ilerleme metrikleri
   - Risk göstergeleri
         ↓
4. Ön İşleme Pipeline'ı
   - Sayısal: StandardScaler
   - Nominal Kategorik: OneHotEncoder
   - Ordinal Kategorik: OrdinalEncoder
         ↓
5. Sınıf Dengesizliğini Ele Alma (SMOTE)
         ↓
6. Model Geliştirme (12 algoritma test edildi)
         ↓
7. Hiperparametre Ayarlama (RandomizedSearchCV)
         ↓
8. Model Değerlendirme & Seçim
         ↓
9. Topluluk Yöntemleri (Voting, Stacking)
         ↓
10. Model Yorumlama (SHAP)
         ↓
11. İş İçgörüleri & Öneriler
         ↓
12. Dağıtım için Model Dışa Aktarma
```

## 📈 Değerlendirilen Modeller

12 farklı sınıflandırma algoritması test ettim:

1. Lojistik Regresyon
2. Random Forest
3. XGBoost
4. LightGBM
5. CatBoost
6. Gradient Boosting
7. AdaBoost
8. Destek Vektör Makinesi (SVM)
9. K-En Yakın Komşu (KNN)
10. Naive Bayes
11. Karar Ağacı
12. Extra Trees

### Değerlendirme Metrikleri

Sınıf dengesizliği olduğundan sadece doğruluk yeterli değil. Odaklandığım metrikler:

- **ROC-AUC:** Genel ayırt edici yetenek
- **Recall:** Ayrılacak bir çalışanı kaçırmak maliyetli olduğu için önemli
- **Precision:** İK kaynaklarını boşa harcayan yanlış alarmlardan kaçınmak
- **F1-Score:** Precision ve recall arasında denge

## 🚀 Nasıl Çalıştırılır

### Ön Koşullar

```bash
# Sanal ortam oluştur
python -m venv venv

# Aktifleştir (Windows)
.\venv\Scripts\Activate.ps1

# Aktifleştir (Linux/Mac)
source venv/bin/activate
```

### Bağımlılıkları Yükle

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost lightgbm catboost imbalanced-learn shap jupyter ipykernel jinja2
```

### Notebook'u Çalıştır

```bash
jupyter notebook Project.ipynb
```

Veya VS Code'da Jupyter eklentisiyle doğrudan açabilirsiniz.

## 📁 Proje Yapısı

```
KaggleProject/
├── Project.ipynb              # Tam analizli ana notebook
├── README.md                  # Bu dokümantasyon
├── WA_Fn-UseC_-HR-Employee-Attrition.csv  # Veri seti
├── attrition_model.joblib     # Eğitilmiş model (dağıtım için)
├── preprocessor.joblib        # Fit edilmiş ön işleme pipeline'ı
├── feature_importance.csv     # Özellik önem sıralamaları
├── model_metadata.json        # Model konfigürasyonu ve metrikleri
├── AI.MD                      # AI asistan notları
├── catboost_info/             # CatBoost eğitim logları
└── venv/                      # Python sanal ortamı
```

## 📊 Temel Bulgular

Analizime göre:

1. **FazlaMesai** en güçlü tahmin edici - fazla mesai yapan çalışanların ayrılma olasılığı çok daha yüksek
2. **İş Memnuniyeti** ve **Ortam Memnuniyeti** önemli ölçüde etkili
3. **Şirketteki Yıllar** doğrusal olmayan bir ilişki gösteriyor - çok yeni ve çok kıdemli çalışanlar farklı davranıyor
4. İş seviyesine göre **Aylık Gelir** işten ayrılma riskini etkiliyor
5. **İş-Yaşam Dengesi** kritik, özellikle fazla mesaiyle birleştiğinde

## 💡 İş Önerileri

1. **Fazla Mesaiyi İzle:** Tükenmişliği önlemek için politikalar uygula
2. **Düzenli Memnuniyet Anketleri:** İş ve ortam memnuniyetini takip et
3. **Kariyer Gelişimi:** Net ilerleme yolları işten ayrılmayı azaltır
4. **Rekabetçi Ücret:** Özellikle risk altındaki yüksek performanslılar için
5. **Erken Uyarı Sistemi:** Risk altındaki çalışanları işaretlemek için bu modeli kullan

## 🔮 Gelecek İyileştirmeler

- [ ] Web uygulaması olarak dağıtım (Flask/FastAPI)
- [ ] Gerçek zamanlı tahmin API'si ekle
- [ ] Drift tespiti için model izleme uygula
- [ ] Modelin önerdiği İK müdahalelerini A/B test et
- [ ] Tahminleri iyileştirmek için daha fazla veri topla

## 📜 Lisans

Bu proje, Tech Istanbul Makine Öğrenmesi Bootcamp kapsamında eğitim amaçlı oluşturulmuştur.

## 🙏 Teşekkürler

- Mükemmel makine öğrenmesi bootcamp'i için **Tech Istanbul**
- İK Analitik veri setini sağladığı için **IBM**
- Harika kütüphaneler için açık kaynak topluluğu

---

**Author / Yazar:** Emre  
**Project:** Tech Istanbul Machine Learning Bootcamp - Graduation Project  
**Proje:** Tech Istanbul Makine Öğrenmesi Bootcamp - Bitirme Projesi  
**Date / Tarih:** 2026
