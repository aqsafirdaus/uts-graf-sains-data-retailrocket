# uts-graf-sains-data-retailrocket

Repository ini berisi dokumentasi pengerjaan Ujian Tengah Semester (UTS) mata kuliah **Graf Sains Data** menggunakan dataset e-commerce RetailRocket. Pengerjaan mencakup pengolahan data interaksi pengguna dengan item serta penerapan metode *K-Nearest Neighbors* (KNN) untuk menghasilkan rekomendasi item.

## Tujuan

1. Mengolah data interaksi pengguna dan item dari dataset RetailRocket.
2. Membagi data berdasarkan periode waktu menjadi data P1 dan P2.
3. Membangun rekomendasi item menggunakan metode KNN berdasarkan kemiripan interaksi antar pengguna.
4. Mengevaluasi hasil rekomendasi menggunakan metrik Hit@5 dan NDCG@5.

## Dataset

Dataset yang digunakan adalah **RetailRocket e-commerce dataset** khususnya events.csv yang berisi catatan aktivitas pengguna terhadap item.

Kolom utama yang digunakan:

| Kolom | Deskripsi |
|---|---|
| `timestamp` | Waktu terjadinya aktivitas pengguna |
| `visitorid` | ID pengguna atau pengunjung |
| `event` | Jenis aktivitas, seperti `view`, `addtocart`, dan `transaction` |
| `itemid` | ID item yang berinteraksi dengan pengguna |
| `transactionid` | ID transaksi, jika tersedia |

### Pembagian Data

Data dibagi menjadi dua periode berdasarkan timestamp:

- **P1 — Data pelatihan:** 3 Mei 2015 sampai 23 Mei 2015.
- **P2 — Data pengujian:** 25 Agustus 2015 sampai 14 September 2015.

P1 digunakan untuk membentuk matriks interaksi pengguna-item dan mencari tetangga terdekat. P2 digunakan untuk memeriksa relevansi item rekomendasi berdasarkan interaksi aktual pengguna pada periode pengujian.

## Metode

### 1. User-Item Interaction Matrix

Data interaksi diubah menjadi matriks pengguna-item berbentuk sparse matrix. Nilai matriks menunjukkan apakah pengguna pernah berinteraksi dengan suatu item pada periode pelatihan.

### 2. K-Nearest Neighbors (KNN)

KNN digunakan untuk mencari lima pengguna yang memiliki pola interaksi paling mirip dengan pengguna target. Kemiripan dihitung menggunakan *cosine distance*. Item yang telah dimiliki atau pernah diinteraksikan oleh pengguna target dikeluarkan dari kandidat rekomendasi.

### 3. Evaluasi Rekomendasi

Evaluasi dilakukan menggunakan dua metrik:

- **Hit@5:** mengukur apakah setidaknya satu item relevan muncul dalam lima rekomendasi teratas.
- **NDCG@5:** mengukur kualitas urutan rekomendasi berdasarkan posisi item relevan.

Item relevan ditentukan dengan membandingkan rekomendasi dengan interaksi aktual pengguna pada periode P2.

## Struktur Repository

```text
uts-graf-sains-data-retailrocket/
├── notebook_uts.ipynb
├── retailrocket_P1.csv
├── retailrocket_P2.csv
└── README.md
```

## Sumber Dataset

RetailRocket e-commerce dataset: https://www.kaggle.com/api/v1/datasets/download/retailrocket/ecommerce-dataset

---

Repository ini dibuat untuk keperluan dokumentasi tugas UTS mata kuliah Graf Sains Data.
