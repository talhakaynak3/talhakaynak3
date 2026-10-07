<h1 align="center">Talha Kaynak</h1>

<p align="center">
  Yapay zekâ destekli sistemler kuruyorum — şu sıra <strong>Clévo AI</strong>:<br>
  Türkiye'nin HVAC teknik servis bilgi tabanı, sahada çalışan teknisyenler için.
</p>

---

### Projeler

| | Ne yapar |
|---|---|
| **[Clévo AI](https://github.com/talhakaynak3/clevo-ai)** | HVAC teknik servis RAG sistemi. 27 marka, 5607 arıza kaydı; teknisyen metin, fotoğraf veya sesle sorar. Hibrit arama: kod eşleşmesi + `bge-m3` vektör + Okapi BM25 (RRF). |
| **[Yapı Sağlığı](https://github.com/talhakaynak3/yapi-sagligi-projesi)** | Deprem riski ön tarama. İl/ilçe tehlike haritası + yapısal zafiyet puanlaması (yumuşak kat, kısa kolon, burulma, çarpışma) → gerekçeli risk seviyesi. FastAPI + RandomForest. |
| **[Pose + Depth Form Analizi](https://github.com/talhakaynak3/pose-depth-form-analizi)** | Videodan egzersiz formu analizi. MediaPipe Pose (eklem açıları) + MiDaS (göreli derinlik); eşik yazmak yerine doğru form videosundan öğrenir. |

### Nasıl çalışıyorum

**Bir sayı yoksa karar da yoktur.** Üç projenin ortak çizgisi bu:

- **Varsayım ölçülür.** Clévo'da dense embedding'lerin `E01` ile `E28`i ayırt
  edebileceğini varsaymak yerine ölçtüm: kod sorgularında recall@8 **0.188**. Ayrı bir
  tam eşleşme katmanı eklendi → **1.000**.
- **Eşik yazılmaz, öğrenilir.** Form analizinde "dirsek 70–135 derece olmalı" diye bir
  sayı koda girmiyor; aralıklar doğru formla çekilmiş videodan 15–85 persentil ile
  çıkarılıyor.
- **Ölçüm bir özelliği kapatabilir.** Clévo'nun cross-encoder yeniden sıralaması zor
  sorgularda recall@1'i 0.636 → **0.818** çıkardı, hiçbir sorguyu bozmadan — ama CPU'da
  7 sn/sorgu. Varsayılan olarak **kapalı**; kullanıcının bilerek açtığı bir kipin
  arkasında.
- **Sınır gizlenmez, yazılır.** Yapı Sağlığı'ndaki model kural motorunun kendi
  ürettiği sentetik veriyle eğitildi — yani öğrendiği şey saha sonucu değil kuralların
  kendisi. Bu, README'nin içinde yazılı.

Standart tavsiyeler de ölçümle sınanıyor: Clévo'yu dağıtırken yaygın öneri
`gunicorn -w 4`'tü; ölçtüm, bu projede belleği **dörde katlıyordu** (model işçi başına
yeniden yükleniyor). Doğrusu `--workers=1 --threads=8` çıktı — 4 eşzamanlı iplik
**+0 MB**, çünkü model paylaşılıyor.

### Kullandığım araçlar

<p>
  <img alt="Python" src="https://img.shields.io/badge/Python-3776ab?logo=python&logoColor=white">
  <img alt="Flask" src="https://img.shields.io/badge/Flask-000000?logo=flask&logoColor=white">
  <img alt="FastAPI" src="https://img.shields.io/badge/FastAPI-009688?logo=fastapi&logoColor=white">
  <img alt="PyTorch" src="https://img.shields.io/badge/PyTorch-ee4c2c?logo=pytorch&logoColor=white">
  <img alt="scikit-learn" src="https://img.shields.io/badge/scikit--learn-f7931e?logo=scikitlearn&logoColor=white">
  <img alt="OpenCV" src="https://img.shields.io/badge/OpenCV-5c3ee8?logo=opencv&logoColor=white">
  <img alt="React" src="https://img.shields.io/badge/React-61dafb?logo=react&logoColor=black">
  <img alt="Tailwind CSS" src="https://img.shields.io/badge/Tailwind-06b6d4?logo=tailwindcss&logoColor=white">
  <img alt="PostgreSQL" src="https://img.shields.io/badge/PostgreSQL-4169e1?logo=postgresql&logoColor=white">
</p>

<p align="center"><sub>RAG · bilgi getirme · bilgisayarlı görü · çok kiracılı SaaS</sub></p>
