# 📦 Analisis Sentimen & Opini Publik Terhadap Regulasi Pembatasan Diskon Ongkir (Permen Komdigi No. 8/2025)
### Analisis Opini Komentar TikTok Menggunakan NLP, WordLink Network, dan Pemodelan Topik BERTopic

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter Notebook](https://img.shields.io/badge/Notebook-Jupyter-orange?logo=jupyter&logoColor=white)](code_capstone1_ams.ipynb)
[![Dataset](https://img.shields.io/badge/Dataset-5.967%20TikTok%20Comments-black?logo=tiktok&logoColor=white)](tiktok-ams-capstone1.csv)
[![Topic Modeling](https://img.shields.io/badge/Model-BERTopic%20(PyTorch)-red)]()
[![Network Analysis](https://img.shields.io/badge/Network-WordLink%20Graph-green)]()

---

## 📌 Ringkasan Proyek (Business & Policy Understanding)

Pemerintah melalui Kementerian Komunikasi dan Digital (Komdigi) menerbitkan **Permen Komdigi No. 8 Tahun 2025** tentang Layanan Pos Komersial. Salah satu substansi utama dalam kebijakan ini adalah **pembatasan promo gratis ongkos kirim (ongkir) menjadi maksimal 3 hari per bulan**. Kebijakan ini dirancang dengan tujuan mencegah perang tarif logistik yang tidak sehat, melindungi kurir serta pelaku industri logistik skala kecil, serta mendorong pemerataan ke pasar fisik/toko lokal.

Namun, kebijakan ini memicu gelombang diskursus publik yang masif di media sosial, terutama dari konsumen *e-commerce*, pedagang *online*, hingga para mitra kurir pengiriman.

Repositori ini menyajikan analisis komprehensif terhadap **5.967 komentar publik di platform TikTok** (periode Mei–Juni 2025) untuk mengukur reaksi masyarakat, memetakan topik perbincangan, dan mengevaluasi efektivitas sosialisasi kebijakan menggunakan pendekatan mutakhir:
1. **Natural Language Processing (NLP):** Normalisasi bahasa gaul TikTok (`slang_GratisOngkir.txt`), pembersihan teks, dan klasifikasi sentimen 3 kelas (Positif, Netral, Negatif).
2. **WordLink / Bigram Network Analysis:** Memetakan asosiasi kata kunci dan derajat sentralitas graf percakapan menggunakan `NetworkX`.
3. **Advanced Topic Modeling (BERTopic):** Ekstraksi topik berbasis transformer (BERT) yang diperkuat reduksi dimensi UMAP, klastering HDBSCAN, dan representasi c-TF-IDF pada GPU PyTorch.
4. **Analisis Tren Temporal & Influencer Engagement:** Melacak dinamika lonjakan opini harian dan pemengaruh (*key opinion leaders*) paling vokal di TikTok.

---

## 🎯 Tujuan Analisis

1. Mengidentifikasi proporsi sentimen publik (penolakan vs penerimaan) terhadap regulasi pembatasan diskon ongkir.
2. Mengekstraksi klaster narasi utama dari komentar negatif, netral, dan positif secara otomatis menggunakan **BERTopic**.
3. Mengetahui dinamika lonjakan percakapan (*peak trend*) dan akun pemengaruh (*influencer*) yang memicu eskalasi diskusi.
4. Merumuskan rekomendasi kebijakan strategis serta mitigasi komunikasi publik bagi regulator dan pemangku kepentingan industri.

---

## 🔬 Metodologi Analisis Data

- **Sumber Data:** 5.967 komentar TikTok terkait pengumuman Permen Komdigi No. 8/2025 (periode Mei–Juni 2025).
- **Text Preprocessing & Normalization:**
  - Pembersihan URL, mention, emoji, karakter khusus, dan tanda baca.
  - Normalisasi bahasa gaul dan singkatan khas komentar TikTok menggunakan kamus khusus `slang_GratisOngkir.txt`.
  - Tokenisasi dan eliminasi *stopwords* bahasa Indonesia menggunakan pustaka `Sastrawi`.
- **Pemodelan Topik (BERTopic):**
  - Menggunakan embedding multibahasa/Indonesia dengan pemrosesan tensor PyTorch (GPU).
  - Reduksi dimensi manifold dengan `UMAP` dan klastering densitas berbasis `HDBSCAN` untuk menghasilkan klaster topik alami tanpa asumsi distribusi kaku.
- **Analisis Jaringan Kata (WordLink Graph):**
  - Pembuatan graf relasi pasangan kata (*bigram network*) untuk melihat struktur semantik perbincangan pada setiap kelas sentimen.

---

## 🏆 Temuan Utama (Key Findings)

### 1. Proporsi Sentimen Publik
Dari **5.967 komentar** yang dianalisis:

| Sentimen | Proporsi | Karakteristik Narasi Utama |
| :--- | :---: | :--- |
| **Negatif** 🔴 | **55%** | Penolakan luas terhadap pembatasan gratis ongkir; kekhawatiran naiknya pengeluaran belanja harian, potensi sepinya pesanan online, ancaman berkurangnya pendapatan kurir, serta kritik bahwa kebijakan memberatkan masyarakat di luar Pulau Jawa yang bergantung pada pengiriman online. |
| **Netral** ⚪ | **38%** | Diskusi seputar tarif ongkir reguler, respons kebingungan atau belum memahami detail regulasi, ide berlangganan paket e-commerce VIP/berbayar sebagai alternatif gratis ongkir, serta komentar terdistraksi topik hiburan harian. |
| **Positif** 🟢 | **6%** | Dukungan dari pelaku toko fisik/pasar tradisional yang berharap pembeli kembali berbelanja langsung, dorongan mengerem perilaku konsumtif, serta apresiasi dari sudut pandang perlindungan upah pekerja logistik. |

---

### 2. Klaster Topik Utama Hasil BERTopic

| Kategori Sentimen | Klaster Topik yang Terbentuk | Rangkuman Narasi & Kata Kunci Kunci |
| :--- | :--- | :--- |
| **Topik Negatif** | • Dampak Ekonomi & Daya Beli<br>• Nasib & Pendapatan Kurir<br>• Kritik terhadap Regulasi Pemerintah<br>• Kesenjangan Wilayah Luar Jawa | Kekhawatiran penurunan aktivitas jual-beli daring, ketakutan gaji kurir terpotong karena pesanan berkurang, persepsi regulasi tidak realistis bagi wilayah luar Jawa yang memiliki tarif ongkir mahal. |
| **Topik Positif** | • Momentum Belanja Toko Fisik<br>• Pengendalian Pengeluaran Pribadi<br>• Perlindungan Kesejahteraan Kurir | Harapan pasar tradisional dan UMKM lokal kembali ramai, peluang masyarakat menghemat anggaran belanja impulsif, dukungan atas tarif logistik yang adil bagi kurir. |
| **Topik Netral** | • Pertimbangan Biaya Transaksi<br>• Alternatif Paket VIP / Langganan<br>• Komentar Umum & Interaksi Komunitas | Diskusi opsi fitur berbayar (misal: paket VIP e-commerce), kebingungan teknis apakah aturan berlaku ke promo toko atau platform, serta komentar interaksi umum. |

---

### 3. Analisis Tren Waktu & Lonjakan Percakapan
- **Puncak Perhatian Publik (*Peak Day*):** Terjadi lonjakan dramatis pada **20–21 Mei 2025** dengan volume mencapai **hampir 3.000 interaksi dalam sehari**.
- **Dominasi Sentimen Puncak:** Pada puncak percakapan (21 Mei), sentimen negatif mendominasi dengan **1.750 komentar**, diiringi **1.000 komentar netral**, sementara sentimen positif hanya berada di kisaran 250 komentar.
- **Pascalonjakan:** Perbincangan menyusut cepat dan kembali stabil di bawah 100 komentar harian per awal Juni 2025, menandakan reaksi publik bersifat spontan dan reaktif terhadap rilis pemberitaan.

---

### 4. Top Akun Pemengaruh Kritis (*Influencer Engagement*)
Tujuh akun TikTok kontra-regulasi dengan *engagement* terbesar yang menjadi pusat amplifikasi kritik publik:
1. `@nabillaaptriii` (47.998 engagement)
2. `@ooribeefsnn` (27.199 engagement)
3. `@dioooimida` (16.923 engagement)
4. `@dindakest` (14.149 engagement)
5. `@user71542340382576` (14.103 engagement)
6. `@rifky_m1bb` (12.125 engagement)
7. `@itadwi123` (12.052 engagement)

---

## 💡 Rekomendasi Kebijakan & Komunikasi Publik (Actionable Insights)

1. **Klarifikasi dan Edukasi Substansi Kebijakan:**
   Pemerintah perlu mempertegas sosialisasi bahwa regulasi menyasar batas diskon dari penyedia jasa kurir (mencegah *predatory pricing* logistik), bukan melarang sepenuhnya promosi dari *merchant* e-commerce, guna meluruskan mispersepsi yang memicu 55% sentimen negatif.
2. **Jaring Pengaman & Perlindungan Kurir Lapangan:**
   Kekhawatiran publik didominasi oleh empati terhadap pendapatan kurir. Diperlukan penetapan standar tarif dasar logistik yang layak dan transparansi skema komisi agar mitra kurir tidak menjadi korban penurunan volume kiriman.
3. **Penyelarasan Kebijakan untuk Wilayah 3T dan Luar Jawa:**
   Mengingat disparitas tarif logistik yang tinggi di luar Jawa, regulasi perlu menyediakan pengecualian atau subsidi ongkir terarah agar tidak memperdalam kesenjangan akses barang konsumen daerah.
4. **Kolaborasi dengan Pelaku E-Commerce & Logistik:**
   Mendorong integrasi layanan pengiriman konsolidasi atau logistik hemat biaya agar konsumen tetap mendapatkan alternatif pengiriman yang terjangkau secara legal dan berkelanjutan.

---

*Proyek ini dikembangkan untuk studi Analisis Media Sosial (AMS), text mining NLP, dan evaluasi kebijakan publik di platform media sosial.*
