# ⚽ Premier League Maç Sonucu Tahmini (Veri Odaklı Futbol Analitiği)

Bu proje, İngiltere Premier Lig maçlarındaki ev sahibi takımların oyun içi istatistiklerini (şut üretkenliği ve agresiflik) kullanarak maç sonucunu makine öğrenmesi algoritmalarıyla tahmin eden bir sınıflandırma uygulamasıdır. 

**Software Persona** eğitim programı kapsamında geliştirilen bu çalışma, ham futbol verilerinin temizlenip analiz edilerek canlı tahmin üreten bir yapay zeka aracına dönüştürülmesini amaçlamaktadır.

---

## 🎯 Problem Tanımı ve Amaç
Futbolda maç sonuçları genellikle sezgilere ve öznel yorumlara dayalı olarak tahmin edilir. Bu projenin amacı, ev sahibi takımın temel maç içi istatistiklerini kullanarak maç sonucunu veri odaklı bir yaklaşımla öngörmek ve maç öncesi senaryo analizlerine katkı sağlamaktır.

## 📊 Veri Seti ve Ön İşleme
Projede Kaggle üzerinden elde edilen **2000–2025 English Premier League Match Data** (`epl_final.csv`) veri seti kullanılmıştır (toplam **9.380** maç kaydı).

* **Bağımsız Değişkenler (X):**
  * `HomeShotsOnTarget`: Ev sahibi takımın isabetli şut sayısı
  * `HomeCorners`: Ev sahibi takımın korner sayısı
  * `HomeFouls`: Ev sahibi takımın faul sayısı
* **Hedef Değişken (y):**
  * `FullTimeResult`: Maç sonucu (`H`: Ev Sahibi Galibiyeti, `D`: Beraberlik, `A`: Deplasman Galibiyeti)
* **Veri Temizleme:** Veri kaybını önlemek adına eksik sayısal değerler ilgili sütunun ortalaması (`mean`) ile, eksik sonuç değerleri ise nötr sınıf olan `'D'` (Beraberlik) ile doldurulmuştur.

## 🛠️ Kullanılan Teknolojiler ve Kütüphaneler
* **Python 3**
* **Pandas & NumPy:** Veri işleme ve istatistiksel analiz
* **Matplotlib:** Keşifçi veri analizi (EDA) ve görselleştirme (Bar Chart & Scatter Plot)
* **Scikit-Learn:** Model kurma, veri bölme ve doğruluk değerlendirmesi

## 🤖 Model ve Performans
Çıktı kategorik bir değişken olduğu için sınıflandırma algoritması olarak **Decision Tree (Karar Ağacı)** tercih edilmiştir.

* **Veri Bölme:** %80 Eğitim / %20 Test (`random_state=42`)
* **Hiperparametre:** Ezberlemeyi (overfitting) önlemek amacıyla `max_depth=5` kullanılmıştır.
* **Test Doğruluk Oranı (Accuracy):** **%50.32**

> *Not: Futbol gibi yüksek belirsizlik ve rastgelelik içeren bir sporda, yalnızca üç ev sahibi istatistiği ile elde edilen bu oran, özellikle isabetli şut üretkenliğinin maç sonucu üzerindeki doğrudan etkisini ortaya koymaktadır.*

## 🚀 İnteraktif Tahmin Aracı
Notebook içerisinde yer alan `tahmin_et()` fonksiyonu sayesinde kullanıcıdan anlık olarak beklenen isabetli şut, korner ve faul sayıları alınarak canlı maç sonucu tahmini üretilebilmektedir.

```text
Ev sahibi takımın beklenen isabetli şut sayısı: 5
Ev sahibi takımın beklenen korner sayısı: 3
Ev sahibi takımın beklenen faul sayısı: 8

=> Analiz Sonucu: Girdiğiniz istatistiklere göre bu maç yüksek ihtimalle Ev Sahibi Kazanır!
