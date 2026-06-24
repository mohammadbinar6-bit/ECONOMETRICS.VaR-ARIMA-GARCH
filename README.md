# 📊 Analisis Risiko Saham BEI dengan Pendekatan ARMA–GARCH

**Tim STAVANTS** · Data Analytics Competition (DAC) · Matematika Fair UNIMED 2026

Proyek ini mengukur **risiko kerugian harian (*Value at Risk*)** dari 28 saham unggulan Bursa Efek Indonesia (BEI) menggunakan model time series **ARMA–GARCH**, baik pada level saham individual maupun pada level portofolio.

🔗 **Dashboard interaktif:** [Cek Risiko Saham BEI](https://bei-dashboard-gamma.vercel.app/) — lihat hasil analisis secara visual dan umum, lengkap dengan kalkulator simulasi risiko modal.

---

## 🧠 Tentang Proyek

Berapa potensi kerugian maksimal harian dari sebuah saham di BEI, dan apakah menyebar modal ke banyak saham benar-benar mengurangi risiko? Proyek ini menjawab pertanyaan tersebut secara kuantitatif menggunakan:

- **28 saham blue-chip** BEI dari berbagai sektor (perbankan, *consumer goods*, energi, infrastruktur)
- **2.497 hari data perdagangan** (periode 2014–2024)
- **Model ARMA–GARCH** dengan distribusi inovasi Normal dan Student-t (untuk menangkap *fat tails*)
- **Value at Risk (VaR)** pada tingkat keyakinan 95% dan 99%
- **Validasi statistik** menggunakan uji ADF (stasioneritas), ARCH-LM (heteroskedastisitas), dan Ljung-Box (autokorelasi residual)
- **Analisis efek diversifikasi portofolio** lewat dua metode independen: Varians-Kovarians (parametrik) dan simulasi Monte Carlo (10.000 skenario)

## 📁 Isi Repository

| File | Deskripsi |
|---|---|
| [`DAC_Tim_STAVANTS_Dokumentasi_Rapi.ipynb`](./DAC_Tim_STAVANTS_Dokumentasi_Rapi.ipynb) | Notebook dokumentasi lengkap: data preparation, imputasi missing value, uji asumsi, pemodelan ARMA–GARCH, hingga estimasi VaR individual & portofolio |

## 🔬 Metodologi Singkat

1. **Persiapan Data** — pembersihan data harga, penyamaan rentang waktu antar-saham, transformasi ke *log-return*.
2. **Imputasi Missing Value** — pipeline lima tahap (*rolling smoothing* → *volatility-aware fill* → *seasonal decomposition* → interpolasi polinomial → *final clean-up*) yang menjaga karakteristik statistik data asli.
3. **Uji Asumsi** — stasioneritas (ADF) dan efek ARCH pada setiap saham sebelum pemodelan.
4. **Pemilihan Ordo ARMA** — *grid search* berbasis AIC untuk setiap saham.
5. **Pemodelan ARMA–GARCH** — dua pipeline (*sequential* dan *simultaneous/joint*, termasuk varian EGARCH & GJR-GARCH), dipilih model terbaik secara hibrida berdasarkan kelolosan uji diagnostik dan AIC.
6. **Estimasi VaR** — dihitung untuk tiap saham (95% & 99%), lalu dikonversi ke estimasi kerugian nominal (Rupiah).
7. **Analisis Portofolio** — efek diversifikasi diukur lewat pendekatan Varians-Kovarians dan disilangvalidasi dengan simulasi Monte Carlo.

Detail lengkap setiap langkah, termasuk justifikasi metodologis dan rumus yang digunakan, dapat dilihat langsung di dalam notebook.

## 🛠️ Tools & Library

`pandas` · `numpy` · `statsmodels` · `arch` · `scipy` · `matplotlib` · `seaborn`

## ▶️ Menjalankan Notebook

```bash
pip install pandas numpy statsmodels arch scipy matplotlib seaborn gdown
jupyter notebook DAC_Tim_STAVANTS_Dokumentasi_Rapi.ipynb
```

Notebook akan mengunduh dataset secara otomatis dari Google Drive pada cell pertama.

## ⚠️ Disclaimer

Proyek ini dibuat untuk keperluan **edukasi dan penelitian akademis**, bukan rekomendasi investasi. Selalu konsultasikan keputusan finansial dengan penasihat keuangan profesional.

## 👥 Tim

**STAVANTS** — Data Analytics Competition, Matematika Fair, Universitas Negeri Medan 2026
