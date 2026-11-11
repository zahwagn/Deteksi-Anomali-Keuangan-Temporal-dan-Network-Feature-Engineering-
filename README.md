# Deteksi Anomali Keuangan dengan Temporal dan Network Feature Engineering

Repositori ini menyimpan notebook eksperimen untuk menguji penggunaan informasi temporal dan hubungan antarentitas dalam deteksi anomali transaksi keuangan. Eksperimen menggunakan dua dataset publik, IBM AML dan PaySim, dan dijalankan melalui Google Colab.

## Notebook

Notebook utama berada di `notebooks/Deteksi_Anomali_Keuangan_dengan_Temporal_dan_Network_Feature_Engineering.ipynb`.

Notebook disimpan tanpa output eksekusi agar ukuran file tetap wajar dan tidak menyertakan cuplikan data transaksi pada output. Jalankan ulang sel dari awal untuk menghasilkan tabel, grafik, dan berkas hasil eksperimen.

## Ringkasan eksperimen

Empat konfigurasi fitur dibandingkan:

| Konfigurasi | Fitur |
|---|---|
| E1 | Baseline |
| E2 | Baseline + temporal features |
| E3 | Baseline + network features |
| E4 | Baseline + temporal dan network features |

Isolation Forest menjadi detektor utama. Notebook juga memuat perbandingan detektor sekunder, evaluasi kronologis, serta expanding-window evaluation.

Fitur historis dibentuk berdasarkan urutan waktu. Informasi dari timestamp yang sama atau waktu setelah observasi tidak digunakan sebagai histori. Pembagian data dilakukan secara kronologis dengan menjaga agar transaksi pada timestamp yang sama tetap berada pada subset yang sama.

## Dataset

Notebook mengunduh dataset melalui KaggleHub:

- [IBM Transactions for Anti-Money Laundering (AML)](https://www.kaggle.com/datasets/ealtman2019/ibm-transactions-for-anti-money-laundering-aml)
- [PaySim](https://www.kaggle.com/datasets/ealaxi/paysim1)

Akun Kaggle dan akses terhadap dataset perlu tersedia saat proses download dijalankan. Dataset mentah tidak disimpan di repositori ini.

## Menjalankan di Google Colab

1. Buka notebook dari folder `notebooks` melalui GitHub, lalu pilih **Open in Colab** (atau unggah notebook ke Colab).
2. Jalankan sel secara berurutan dari bagian pertama.
3. Ikuti proses instalasi dependensi dan pengunduhan dataset.
4. Tunggu proses pembentukan fitur historis dan eksperimen selesai. Waktu eksekusi bergantung pada ukuran data dan resource runtime.

Dependensi utama tersedia di `requirements.txt`. Sel instalasi pada notebook juga memasang paket yang dibutuhkan untuk Google Colab.

## Struktur repositori

```text
.
├── README.md
├── requirements.txt
├── .gitignore
└── notebooks/
    └── Deteksi_Anomali_Keuangan_dengan_Temporal_dan_Network_Feature_Engineering.ipynb
```

## Catatan

- IBM AML dan PaySim digunakan sebagai benchmark publik. Eksperimen ini bukan validasi langsung pada data transaksi BI-FAST.
- Pada PaySim, `step` adalah indeks waktu simulasi, bukan timestamp kalender.
- Label fraud/AML digunakan untuk evaluasi, bukan sebagai fitur untuk melatih model unsupervised.
- Skor anomali bukan probabilitas fraud. Threshold alert perlu dinilai sesuai kapasitas pemeriksaan dan kebutuhan operasional.
- Dataset, file hasil eksperimen berukuran besar, serta model tersimpan tidak dimasukkan ke repositori. Berkas tersebut dihasilkan saat notebook dijalankan.

Untuk menjaga keterulangan eksperimen, catat tanggal eksekusi, versi dataset, versi library, dan jenis runtime Google Colab yang digunakan.
