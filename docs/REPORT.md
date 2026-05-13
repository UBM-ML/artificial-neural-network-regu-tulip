# Laporan Kelompok — ANN Bake-Off

> Isi semua bagian di bawah. Hapus _italic placeholder_ setelah diisi.

## Identitas Kelompok

- **Nama Kelompok:** _isi di sini_
- **Anggota:**
  1. Nico Andreas — 322300126 — 01_Single_Layer
  2. Sonny Jong — 32230088 — 02_mlp_sigmoid
  3. Renaldy Rantalulo — 32230132 — 03_mlp_tanh
  4. Jonathan — 32230109 — 04_mlp_relu

---

## 1. Ringkasan Hasil Eksperimen

_Tabel hasil akhir dari notebook `05_comparison.ipynb`. Boleh copy-paste tabel markdown atau screenshot._

| Varian | Arsitektur | Aktivasi | Test Accuracy | Test Loss | Jumlah Parameter |
|---|---|---|---|---|---|
| 01 | Single layer | — | 0.7667 | 0.5789 | 15 |
| 02 | 1 hidden (16) | Sigmoid | 0.9333 | 0.3025 | 131 |
| 03 | 1 hidden (16) | Tanh | 0.9333 | 0.1463 | 131 |
| 04 | 2 hidden (32→16) | ReLU | 0.9333 | 0.1025 | 739 |

---

## 2. Analisis & Diskusi

Pilih **minimal 3 pertanyaan** dari daftar pertanyaan diskusi di `README.md` dan jawab di sini.

### 2.1 Apakah single-layer mampu mencapai akurasi yang sebanding dengan multi-layer? Mengapa?
Tidak. Berdasarkan tabel ringkasan (summary), model 01_single_layer hanya mencapai val_accuracy 0.75, sedangkan ketiga varian MLP (sigmoid, tanh, relu) mencapai 0.958. Hal ini dikarenakan single-layer perceptron hanya mampu memisahkan data secara linear (linear decision boundary). Dataset ini kemungkinan memiliki kompleksitas non-linear yang hanya bisa dipelajari oleh model yang memiliki hidden layers (MLP).

### 2.2 Pada dataset ini, apakah ReLU benar-benar konvergen lebih cepat dibanding Sigmoid? Buktikan dengan grafik loss.
a, ReLU konvergen lebih cepat. Jika kita melihat grafik Perbandingan Validation Loss (_ZzlJQ7VWXIb), kurva 04_mlp_relu (hijau) turun sangat tajam di awal epoch dan langsung mencapai nilai loss terendah di bawah 0.1. Sementara itu, 02_mlp_sigmoid (oranye) turun lebih landai dan membutuhkan lebih banyak epoch untuk mendekati nilai loss yang stabil. Secara teori, ini terjadi karena ReLU menghindari masalah vanishing gradient yang sering dialami Sigmoid.

### 2.3 Apa yang terjadi pada validation accuracy ketika model terlalu dalam (overfitting)? Cocokkan dengan klaim di slide 1.9.
Berdasarkan klaim di slide 1.9 mengenai kapasitas model, ketika model terlalu kompleks (terlalu dalam atau dilatih terlalu lama), ia akan mulai menghafal noise pada training data. Pada grafik val_accuracy (anovhkNiWXIa), jika overfitting terjadi, kita akan melihat kurva akurasi validasi mulai menurun atau stagnan meskipun akurasi training terus meningkat. Hal ini menyebabkan gap yang besar antara performa training dan validasi, yang menandakan penurunan kemampuan generalisasi model.

---

## 3. Refleksi Proses Kerja Kelompok

_300–500 kata. Ceritakan:_
- _Bagaimana kelompok membagi tugas?_
- _Kesulitan apa yang muncul (teknis maupun non-teknis)?_
- _Bagaimana cara mengatasinya?_
- _Pelajaran apa yang bisa dibawa ke proyek ML berikutnya?_

Pembagian Tugas
Dalam mengerjakan proyek perbandingan varian ANN ini, kelompok kami membagi tugas berdasarkan empat varian arsitektur yang harus diuji. Setiap anggota bertanggung jawab penuh atas satu notebook eksperimen: satu anggota mengerjakan Single Layer Perceptron, sementara tiga lainnya masing-masing mengimplementasikan Multi-Layer Perceptron (MLP) dengan fungsi aktivasi yang berbeda (Sigmoid, Tanh, dan ReLU). Setelah eksperimen individual selesai, koordinasi dilakukan untuk mengumpulkan file hasil (.csv) ke dalam repositori GitHub pusat. Satu anggota bertindak sebagai integrator yang menyusun notebook perbandingan akhir untuk melakukan visualisasi gabungan dan analisis lintas model.

Kesulitan yang Muncul
Kendala Teknis: Salah satu kesulitan utama adalah memastikan format output CSV dari tiap anggota seragam. Pada awalnya, ada perbedaan penamaan kolom (misalnya ada yang menggunakan val_acc sementara yang lain val_accuracy), yang menyebabkan error saat penggabungan data (merging). Selain itu, sinkronisasi folder kerja di Google Colab dengan repositori GitHub memerlukan pemahaman teknis terkait perintah Git yang sempat membingungkan beberapa anggota.

Kendala Non-Teknis: Masalah komunikasi dan manajemen waktu menjadi tantangan tersendiri. Karena setiap anggota memiliki jadwal yang berbeda, sinkronisasi hasil sering kali tertunda, sehingga integrator harus menunggu hingga saat-saat terakhir sebelum bisa memulai analisis gabungan.

Cara Mengatasi Masalah
Untuk mengatasi kendala teknis, kami menyepakati sebuah standar template notebook di awal kerja sehingga struktur data yang dihasilkan konsisten. Kami juga berbagi skrip otomasi sederhana untuk melakukan clone dan push hasil ke GitHub agar proses integrasi lebih mulus. Untuk kendala non-teknis, kami menggunakan platform pesan instan secara intensif untuk melakukan update progres secara berkala dan menentukan tenggat waktu internal (dua hari sebelum pengumpulan resmi) agar ada waktu cukup untuk melakukan perbaikan jika terjadi error pada tahap integrasi.

Pelajaran untuk Proyek Berikutnya
Pelajaran berharga yang kami petik adalah pentingnya standardisasi awal dan kontrol versi. Kami menyadari bahwa dalam proyek machine learning yang melibatkan banyak orang, kesepakatan mengenai arsitektur data dan workflow Git jauh lebih penting daripada sekadar menulis kode itu sendiri. Di masa depan, kami berencana menggunakan alat manajemen proyek yang lebih terstruktur dan melakukan code review antar anggota untuk memastikan kualitas kode dan konsistensi logika pemodelan tetap terjaga sejak awal.

---

## 4. Kontribusi Tiap Anggota

| Anggota | Kontribusi Konkret | % Effort |
|---|---|---|
| Sonny Jong | mengerjakan notebook varian 2 | 25 |
| Jonathan | mengerjakan notebook varian 4 | 25 |
| Nico Andreas | mengerjakan notebook varian 1 | 25 |
| Renaldy Runtulalo | mengerjakan notebook varian 3 dan menggabungkan ke notebook 5 | 25 |

_Total harus 100%._

---

## 5. Referensi

_Jika kalian merujuk sumber di luar slide kuliah, tulis di sini (format bebas tapi konsisten)._
