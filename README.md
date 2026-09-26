# 📊 Analisis Penjualan & Operasional: Toko Fashion Gayanara

Proyek ini adalah studi kasus analisis data transaksi ritel fashion lokal di Indonesia. Tujuannya sederhana: mencari tahu kenapa pesanan yang masuk terlihat ramai, tapi pendapatan bersih di akhir bulan tidak optimal.

Semua pengolahan data dan visualisasi pada proyek ini dikerjakan menggunakan **Python di Google Colab**.

---

## 📌 Latar Belakang & Masalah Bisnis

Banyak bisnis e-commerce yang hanya berfokus pada **GMV (Gross Merchandise Value)** atau total pesanan kotor. Padahal dalam operasional harian, ada pesanan yang batal (*cancelled*), barang yang dikembalikan (*returned*), serta biaya diskon dan ongkir yang memakan margin.

Di proyek ini, saya memposisikan diri sebagai Data Analyst untuk **Gayanara (Toko Fashion Online)** guna menjawab beberapa pertanyaan kunci dari tim manajemen:

1. Dari seluruh transaksi yang masuk, berapa persen yang benar-benar menjadi uang kas masuk (*Net Revenue*)?
2. Apa penyebab utama tingginya angka pembatalan pesanan?
3. Apakah ada produk unggulan yang justru kehilangan potensi penjualan akibat manajemen stok yang telat?
4. Bagaimana efektivitas kode promo terhadap nilai keranjang belanja (*Average Order Value*) pelanggan?

---

## 🗂️ Dataset yang Digunakan

Data yang dianalisis merupakan data transaksi relasional yang mencakup:
* `orders.csv` — 3.000 riwayat transaksi pesanan, status order, metode pembayaran, kurir, dan diskon.
* `order_items.csv` — Rincian item di setiap pesanan (kuantitas dan subtotal harga).
* `products.csv` — Katalog 300 produk fashion, kategori, bahan, harga, dan sisa stok gudang.
* `customers.csv` — Profil 800 pelanggan (lokasi kota, provinsi, kelompok usia, dan gender).
* `reviews.csv` — Data ulasan, rating produk, dan sentimen pelanggan.

---

## 🔍 Temuan Utama (Key Insights)

### 1. Kebocoran Omzet (*Revenue Leakage*)
Dari total GMV yang masuk, sekitar **20–25% nilai transaksi menguap** akibat pesanan berstatus *Cancelled* dan *Returned*. Ini menunjukkan perlunya evaluasi pada alur *checkout* dan kejelasan deskripsi produk di etalase.

### 2. Metode Pembayaran & Risiko Batal
Tingkat pembatalan tertinggi terjadi pada transaksi dengan metode **Transfer Bank Manual**. Hal ini umum terjadi saat sistem tidak memiliki batas waktu bayar otomatis (*auto-cancel timer*), sehingga pelanggan membiarkan tagihan kedaluwarsa sementara stok barang tertahan.

### 3. Produk Laris tapi Stok Kosong (*Stockout Risk*)
Analisis cross-table antara riwayat penjualan dan stok fisik menemukan beberapa produk *Hero* (terutama kategori *Dress* dan *Atasan*) berstatus **Stok = 0**. Kondisi ini menyebabkan toko kehilangan potensi omzet harian ke kompetitor.

### 4. Efektivitas Promo & Demografi
Pelanggan yang memanfaatkan kode promo mencatatkan rata-rata nilai belanjaan (AOV) yang lebih tinggi dibanding yang tidak memakai promo. Kontributor pesanan terbesar terkonsentrasi pada kelompok usia **25–34 tahun**.

---

## 💡 Rekomendasi untuk Bisnis

* **Optimasi Checkout:** Terapkan sistem *payment gateway* instan (Virtual Account/QRIS) dengan batas bayar 15–30 menit agar stok tidak mengendap sia-sia.
* **Perbaikan Inventory Planning:** Lakukan *restock* berkala berbasis data penjualan berjalan (bukan sekadar perkiraan) untuk mencegah produk laris kehabisan stok.
* **Skema Promo Bersyarat:** Tetapkan batas minimal belanja (*minimum purchase threshold*) untuk penggunaan voucher promo agar margin keuntungan tidak tergerus ongkir luar pulau.

---

## 🛠️ Tech Stack & Library

* **Python 3.x** (Google Colab Environment)
* **Pandas** — Data wrangling, joining relational tables, agregasi metrik.
* **Matplotlib & Seaborn** — Visualisasi data dan pembuatan grafik bisnis.
* **NumPy** — Komputasi numerik.

---

## 📂 Struktur Repositori

```text
├── data/
│   ├── products.csv
│   ├── reviews.csv
│   ├── customers.csv
│   ├── order_items.csv
│   └── orders.csv
├── notebooks/
│   └── Gayanara_Ecommerce_Sales_Analytics.ipynb
└── README.md
