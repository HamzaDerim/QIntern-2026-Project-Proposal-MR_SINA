# Proje Mr. Sina: Kuantum Görüntü İşleme ve Varyasyonel QML ile 3B Nörogörüntüleme Tabanlı Klinik Karar Destek Sistemi

[![Etkinlik: QIntern 2026](https://img.shields.io/badge/Etkinlik-QIntern_2026-blue.svg)](https://qworld.net/qintern-2026/)
[![Durum: Geliştirme Aşamasında](https://img.shields.io/badge/Durum-Proje_Teklifi_--_Ar--Ge-orange.svg)]()
[![Alan: Medikal Yapay Zekâ & Kuantum](https://img.shields.io/badge/Alan-QIP_%7C_QML_%7C_N%C3%B6rog%C3%B6r%C3%BCnt%C3%BCleme-green.svg)]()

## 📌 Proje Özeti (Abstract)

Proje Mr. Sina; Bipolar Bozukluk ve Şizofreni gibi kronik psikiyatrik hastalıkların objektif, erken ve kişiselleştirilmiş teşhisi için geliştirilmiş yapay zekâ destekli bir Klinik Karar Destek Sistemidir (KKDS). 

Bu araştırma deposu, mevcut asenkron ve otomatik klasik nörogörüntüleme boru hattımızı (dcm2niix, FSL, FreeSurfer); **Kuantum Görüntü İşleme (QIP)**, **Kuantum Makine Öğrenmesi (QML)** ve **Kuantum Yaklaşık Optimizasyon Algoritması (QAOA)** katmanlarıyla entegre ederek NISQ (Gürültülü Orta Ölçekli Kuantum) dönemine taşımayı hedeflemektedir. Proje, voksel düzeyinde kuantum görüntü iyileştirmeden başlayarak sürekli zamanlı kuantum dinamik sistem modellemesine kadar uçtan uca hibrit bir medikal mimari sunar.

## ⚙️ 1. Mevcut Klasik Altyapı (Completed Baseline Pipeline)

Projenin ilk fazında, ham beyin MR görüntülerinden (DICOM) yüksek boyutlu anatomik öznitelikler çıkaran otomatik bir Linux (Ubuntu/WSL) boru hattı başarıyla kurulmuştur:

| Aşama | Kullanılan Araç / Komut | Gerçekleştirilen İşlem |
| :--- | :--- | :--- |
| **Veri Dönüşümü** | `dcm2niix` | Ham hastane DICOM verilerinin tıbbi görüntüleme standardı olan 3B NIfTI (`.nii.gz`) formatına dönüştürülmesi. |
| **Kafası Temizleme** | FSL `bet` (Brain Extraction Tool) | Yapısal MR görüntülerinden kafatası, göz ve boyun gibi beyin dışı dokuların asenkron olarak temizlenmesi. |
| **Görüntü Hizalama** | FSL `flirt` | Görüntülerin standart bir anatomik şablona (MNI152) uzamsal olarak hizalanması ve tescili (registration). |
| **Segmentasyon** | FreeSurfer `recon-all` | Beyin kabuğunun (korteks) gri/beyaz madde sınırlarının ayrılması, kortikal kalınlık ölçümü ve derin beyin yapılarının (Amigdala, Hipokampus vb.) hacimsel segmentasyonu. |
| **Öznitelik Çıkarımı** | `asegstats2table` & `aparcstats2table` | Yüzlerce anatomik ölçümün, makine öğrenmesi modellerinde girdi olarak kullanılmak üzere sayısal matris tablolara dönüştürülmesi. |

## 🚀 2. Önerilen Kuantum Modülleri ve Metodoloji

Projenin ikinci fazında, klasik derin öğrenme yaklaşımlarındaki sınırları aşmak amacıyla üç temel kuantum katmanı sisteme entegre edilmektedir:

### A. Kuantum Görüntü İşleme (Quantum Image Processing - QIP)
* **Kuantum Durum Hazırlama:** 3 boyutlu yapısal MRG verileri, FRQI (Flexible Representation of Quantum Images) veya NEQR (Novel Enhanced Quantum Representation) algoritmaları kullanılarak kuantum durumlarına (genlik ve açı gömmeleriyle) kodlanacaktır.
* **Kuantum Voksel İyileştirme:** Klasik filtrelerin yetersiz kaldığı mikroyapısal gürültüleri bastırmak ve derin beyin yapılarındaki (Hipokampus, Amigdala) gri madde kontrastını artırmak için kuantum alanında çalışan özel voksel filtreleri tasarlanacaktır.

### B. Kuantum Makine Öğrenmesi (QML) ve Sürekli Zamanlı Modelleme
* **Kuantum Evrişimli Sinir Ağları (QCNN):** Boyutsallığı kuantum durum hazırlığı ile optimize edilmiş 3B MR görüntülerinden uzamsal öznitelikleri yakalamak için parametreli kuantum devreleri (PQC) içeren QCNN mimarileri geliştirilecektir.
* **Kuantum Neural ODE'ler (Q-ODEs):** Dinamik sistemlerdeki derin öğrenme deneyimlerimize dayanarak, psikiyatrik hastalıkların beyindeki boyutsal ve boylamsal (longitudinal) yapısal değişim yörüngelerini, diferansiyel denklemleri kuantum devreleriyle çözen sürekli zamanlı Kuantum Neural ODE'ler ile modelleyeceğiz.

### C. Matematiksel Biyobelirteç Seçimi için Kuantum Optimizasyonu
* **QUBO Formülasyonu:** FreeSurfer çıktılarından elde edilen yüksek boyutlu kortikal kalınlık ve hacim verileri arasından, tanısal hassasiyeti en yüksek olan klinik biyobelirteçlerin seçilmesi problemi Kısıtsız İkinci Dereceden İkili Optimizasyon (QUBO) modeline dönüştürülecektir.
* **QAOA Uygulaması:** Geleneksel MILP (Karışık Tam Sayılı Doğrusal Programlama) modellerinin işlem yükünü hafifletmek adına, QUBO matrisi QAOA algoritması kullanılarak çözülecek ve en optimum alt öznitelik seti belirlenecektir.

## 📂 Depo Mimarisi (Repository Structure)

* `pipeline/`: DICOM-NIfTI dönüşümü, FSL kafatası temizleme ve FreeSurfer `recon-all` otomasyon betikleri (`hepsini_isle.sh`).
* `qip/`: 3B MRG verilerinin kuantum genlik kodlama (amplitude encoding) ve kuantum kontrast filtreleme devreleri.
* `qml/`: QCNN mimarileri, Kuantum Fizik Bilgili Sinir Ağları (Q-PINNs) ve Kuantum Neural ODE prototipleri.
* `optimization/`: Klinik veriler için oluşturulan QUBO matrisleri ve QAOA optimizasyon betikleri.
* `docs/`: Projenin tıp ve kuantum matematiği temellerini açıklayan akademik raporlar, sunum dosyaları (Pitch Decks).

## 🛠️ Teknoloji Yığını (Tech Stack)

* **Nörogörüntüleme:** FreeSurfer, FSL (FMRIB Software Library), dcm2niix
* **Kuantum Hesaplama & Simülasyon:** PennyLane, Qiskit
* **Derin Öğrenme & Dinamik Sistemler:** PyTorch, Torchdiffeq
* **Veri Bilimi ve Altyapı:** Ubuntu/WSL, Python, NumPy, Pandas

## 👨‍💻 Araştırma Ekibi ve İletişim

* **Hamza Derim** - *Proje Kaptanı / Veri Bilimi ve Yapay Zekâ Uzmanı*
* **Doç. Dr. Çiğdem Özer** - *Radyoloji Uzmanı / Akademik Danışman*
* **Dr. Ekrem Furkan Uçak** - *Psikiyatrist / Klinik Danışman*

---
*Proje Mr. Sina, kuantum görüntü işleme ve uygulamalı matematiksel optimizasyon yöntemlerinin klinik psikiyatrideki dönüştürücü gücünü kanıtlamak adına QIntern 2026 kapsamında ileri düzey Ar-Ge çalışmalarına devam etmektedir.*
