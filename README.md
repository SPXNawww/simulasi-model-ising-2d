Buatlah halaman Github yang baru (bukan clone/fork) dengan anggota kelompok yang sama. Pada halaman tersebut kalian menjelaskan hasil simulasi Ising 2 Dimensi. Ikuti arahan berikut ini.

## Fisika Komputasi: Simulasi Model Ising 2D via Algoritma Metropolis

Selamat datang dalam tugas studi kasus komprehensif mengenai Model Ising 2 Dimensi (2D) dan Transisi Fasa. Dalam tugas ini, Anda akan menerapkan algoritma Monte Carlo Metropolis untuk mensimulasikan sistem kisi magnetik dua dimensi dan mengamati bagaimana perilaku kolektif partikel memicu terjadinya magnetisasi spontan serta transisi fasa makroskopis.

### Tujuan

Tugas Anda adalah membangun program simulasi, melakukan analisis matematis serta komputasional terhadap Model Ising 2D pada tiga rentang suhu yang berbeda di dalam Jupyter Notebook, kemudian memublikasikan hasil temuan Anda sebagai portofolio web publik menggunakan GitHub Pages.

## Instruksi Langkah Demi Langkah

### Langkah 1: Membangun Repositori GitHub dan Menyiapkan Lingkungan Kerja

1. Buka akun GitHub Anda dan buatlah sebuah repositori publik baru secara mandiri dari awal (misalnya dengan nama `simulasi-model-ising-2d`). Pastikan Anda **tidak** menyalin (*fork*) atau mengklon templat yang sudah ada.
2. Buatlah struktur direktori di dalam folder proyek Anda, yang minimal terdiri dari folder `notebooks/` untuk menyimpan berkas analisis dan folder `docs/` untuk keperluan publikasi web.

### Langkah 2: Melakukan Simulasi dan Analisis Kasus

Buatlah berkas Jupyter Notebook baru di dalam direktori `notebooks/`. Anda diminta untuk mengimplementasikan algoritma Metropolis secara mandiri yang mencakup pemilihan spin acak , perhitungan perubahan energi lokal ($\Delta E$) secara efisien , serta penerapan kriteria penerimaan Metropolis.

Analisis harus dibagi ke dalam tiga studi kasus berdasarkan kondisi termodinamika sistem:

- **Kasus 1: Fase Feromagnetik (T = 1.0)** – Simulasikan sistem di bawah suhu kritis (`$T < T_c$`). Amati bagaimana spin individu berorientasi searah secara spontan untuk membentuk domain magnetik yang seragam, sehingga nilai mutlak magnetisasi rata-rata mendekati satu (|M| $\approx 1$).
- **Kasus 2: Transisi Fasa & Kritikalitas (T = 2.27)** – Amati perilaku sistem pada titik suhu kritis teoritis ($T_c \approx 2.27$). Analisis fluktuasi kritis yang terjadi, pembentukan pola domain fraktal, dan runtuhnya keteraturan jarak jauh.
- **Kasus 3: Fase Paramagnetik (T = 4.0)** – Teliti sistem pada rentang suhu tinggi ($T > T_c$). Tunjukkan bagaimana energi termal mendominasi interaksi antar-spin sehingga arah spin menjadi acak dan nilai magnetisasi rata-rata mendekati nol.

Untuk setiap studi kasus di atas, Anda wajib:

- Menginisialisasi kisi  $N \times N$ (dengan N = 20) menggunakan konfigurasi acak (*Hot Start*) untuk merepresentasikan entropi maksimum sistem.
- Menjalankan minimal 200.000 langkah Monte Carlo untuk memastikan sistem telah mencapai kesetimbangan termal sebelum pengumpulan data makrostate dilakukan.
- Menghitung nilai magnetisasi rata-rata secara berkala (misalnya setiap 100 langkah).
- Menampilkan visualisasi keadaan akhir kisi spin menggunakan peta warna biner (`cmap='binary'`) berdampingan dengan kurva riwayat magnetisasi rata-rata sepanjang fungsi waktu simulasi.
- Menyusun interpretasi fisis ilmiah yang mendalam mengenai mekanika statistik yang mendasari fenomena tersebut menggunakan sel Markdown.

### Langkah 3: Kompilasi Berkas Menjadi HTML

Setelah seluruh analisis selesai dikembangkan dan semua sel kode telah dieksekusi dengan benar hingga memunculkan grafik, konversikan berkas Jupyter Notebook tersebut menjadi dokumen HTML statis. Jalankan perintah berikut melalui terminal Anda:

Bash

```
jupyter nbconvert --to html notebooks/Kasus_1_Suhu_Rendah.ipynb --output-dir docs/
jupyter nbconvert --to html notebooks/Kasus_2_Suhu_Kritis.ipynb --output-dir docs/
jupyter nbconvert --to html notebooks/Kasus_3_Suhu_Tinggi.ipynb --output-dir docs/
```

*Catatan: Buatlah sebuah berkas `docs/index.html` sederhana secara manual yang berfungsi sebagai halaman utama (homepage) untuk menautkan ketiga berkas HTML hasil konversi tersebut.*

### Langkah 4: Penyebaran (*Deployment*) via GitHub Pages (tidak diperlukan jika langkah sebelumnya sudah dikerjakan secara online)

1. Lakukan *commit* dan dorong (*push*) seluruh berkas proyek Anda ke repositori GitHub:Bash
    
    ```
    git add .
    git commit -m "Menyelesaikan simulasi Model Ising 2D dan kompilasi HTML"
    git push origin main
    ```
    
2. Buka halaman repositori Anda di GitHub melalui peramban, lalu masuk ke menu **Settings** > **Pages**.
3. Pada bagian **Build and deployment**, ubah parameter Source menjadi **Deploy from a branch**.
4. Pada opsi pemilihan Branch, pilih opsi **main**, lalu ubah direktori folder dari `/(root)` menjadi `/docs`.
5. Klik **Save**. Dalam waktu beberapa menit, situs portofolio komputasi fisika Anda akan aktif dan dapat diakses secara publik.

## Kriteria Evaluasi

Penilaian terhadap hasil modifikasi dan pengerjaan tugas ini didasarkan pada aspek-aspek berikut:

1. **Akurasi Matematis dan Fisis:** Ketepatan formulasi matematis dalam menghitung selisih energi lokal $\Delta E = 2s_{i,j} \sum s_{\text{tetangga}}$ dengan menerapkan kondisi batas periodik (*periodic boundary conditions*) menggunakan operasi modulo , serta kebenaran implementasi probabilitas penerimaan Metropolis $\mathcal{R} = e^{-\Delta E / T}$.
2. **Efisiensi Komputasi:** Kebersihan struktur kode Python, penulisan dokumentasi/komentar yang informatif , serta optimalisasi algoritma dengan memanfaatkan perhitungan energi lokal alih-alih menghitung ulang energi total seluruh kisi pada setiap iterasi.
3. **Komunikasi Ilmiah:** Kejelasan visualisasi data yang disajikan (kelengkapan label sumbu, judul grafik, dan skala yang tepat)  serta kedalaman analisis teoretis fisis yang dituliskan pada penjelasan teks.

## Referensi dan Sumber Data

- Landau, D. P., dkk. *A Guide to Monte Carlo Simulations in Statistical Physics* (Bab 17.2: Aturan Implementasi).
- Rifani, Agus. *Modul Pembelajaran: Simulasi Model Magnet dan Transisi Fasa*.

## Penggunaan AI

Contohnya kalian menuliskan: 

Pada pengerjaan *case-based* ini, kami menggunakan:

1. **Gemini 3.1 Pro** untuk mendesain struktur instruksi tugas serta melakukan optimasi sintaksis algoritma Metropolis pada potongan kode simulasi;
2. **Claude Sonnet 4.6** untuk memvalidasi penalaran fisis penurunan persamaan energi lokal dan penataan komponen dokumen markdown.

## Penggunaan Aplikasi Lain

Contohnya seperti ini

1. **Jupyter Software** untuk menyediakan lingkungan eksekusi kode secara interaktif, penulisan analisis berbasis teks formal, dan penampilan visualisasi kurva magnetisasi secara *inline*.
2. **Miniconda** untuk manajemen isolasi lingkungan virtual (*virtual environment*) Python guna memastikan kestabilan versi pustaka `numpy` dan `matplotlib` yang digunakan.
Buatlah halaman Github yang baru (bukan clone/fork) dengan anggota kelompok yang sama. Pada halaman tersebut kalian menjelaskan hasil simulasi Ising 2 Dimensi. Ikuti arahan berikut ini.

## Fisika Komputasi: Simulasi Model Ising 2D via Algoritma Metropolis

Selamat datang dalam tugas studi kasus komprehensif mengenai Model Ising 2 Dimensi (2D) dan Transisi Fasa. Dalam tugas ini, Anda akan menerapkan algoritma Monte Carlo Metropolis untuk mensimulasikan sistem kisi magnetik dua dimensi dan mengamati bagaimana perilaku kolektif partikel memicu terjadinya magnetisasi spontan serta transisi fasa makroskopis.

### Tujuan

Tugas Anda adalah membangun program simulasi, melakukan analisis matematis serta komputasional terhadap Model Ising 2D pada tiga rentang suhu yang berbeda di dalam Jupyter Notebook, kemudian memublikasikan hasil temuan Anda sebagai portofolio web publik menggunakan GitHub Pages.

## Instruksi Langkah Demi Langkah

### Langkah 1: Membangun Repositori GitHub dan Menyiapkan Lingkungan Kerja

1. Buka akun GitHub Anda dan buatlah sebuah repositori publik baru secara mandiri dari awal (misalnya dengan nama `simulasi-model-ising-2d`). Pastikan Anda **tidak** menyalin (*fork*) atau mengklon templat yang sudah ada.
2. Buatlah struktur direktori di dalam folder proyek Anda, yang minimal terdiri dari folder `notebooks/` untuk menyimpan berkas analisis dan folder `docs/` untuk keperluan publikasi web.

### Langkah 2: Melakukan Simulasi dan Analisis Kasus

Buatlah berkas Jupyter Notebook baru di dalam direktori `notebooks/`. Anda diminta untuk mengimplementasikan algoritma Metropolis secara mandiri yang mencakup pemilihan spin acak , perhitungan perubahan energi lokal ($\Delta E$) secara efisien , serta penerapan kriteria penerimaan Metropolis.

Analisis harus dibagi ke dalam tiga studi kasus berdasarkan kondisi termodinamika sistem:

- **Kasus 1: Fase Feromagnetik (T = 1.0)** – Simulasikan sistem di bawah suhu kritis (`$T < T_c$`). Amati bagaimana spin individu berorientasi searah secara spontan untuk membentuk domain magnetik yang seragam, sehingga nilai mutlak magnetisasi rata-rata mendekati satu (|M| $\approx 1$).
- **Kasus 2: Transisi Fasa & Kritikalitas (T = 2.27)** – Amati perilaku sistem pada titik suhu kritis teoritis ($T_c \approx 2.27$). Analisis fluktuasi kritis yang terjadi, pembentukan pola domain fraktal, dan runtuhnya keteraturan jarak jauh.
- **Kasus 3: Fase Paramagnetik (T = 4.0)** – Teliti sistem pada rentang suhu tinggi ($T > T_c$). Tunjukkan bagaimana energi termal mendominasi interaksi antar-spin sehingga arah spin menjadi acak dan nilai magnetisasi rata-rata mendekati nol.

Untuk setiap studi kasus di atas, Anda wajib:

- Menginisialisasi kisi  $N \times N$ (dengan N = 20) menggunakan konfigurasi acak (*Hot Start*) untuk merepresentasikan entropi maksimum sistem.
- Menjalankan minimal 200.000 langkah Monte Carlo untuk memastikan sistem telah mencapai kesetimbangan termal sebelum pengumpulan data makrostate dilakukan.
- Menghitung nilai magnetisasi rata-rata secara berkala (misalnya setiap 100 langkah).
- Menampilkan visualisasi keadaan akhir kisi spin menggunakan peta warna biner (`cmap='binary'`) berdampingan dengan kurva riwayat magnetisasi rata-rata sepanjang fungsi waktu simulasi.
- Menyusun interpretasi fisis ilmiah yang mendalam mengenai mekanika statistik yang mendasari fenomena tersebut menggunakan sel Markdown.

### Langkah 3: Kompilasi Berkas Menjadi HTML

Setelah seluruh analisis selesai dikembangkan dan semua sel kode telah dieksekusi dengan benar hingga memunculkan grafik, konversikan berkas Jupyter Notebook tersebut menjadi dokumen HTML statis. Jalankan perintah berikut melalui terminal Anda:

Bash

```
jupyter nbconvert --to html notebooks/Kasus_1_Suhu_Rendah.ipynb --output-dir docs/
jupyter nbconvert --to html notebooks/Kasus_2_Suhu_Kritis.ipynb --output-dir docs/
jupyter nbconvert --to html notebooks/Kasus_3_Suhu_Tinggi.ipynb --output-dir docs/
```

*Catatan: Buatlah sebuah berkas `docs/index.html` sederhana secara manual yang berfungsi sebagai halaman utama (homepage) untuk menautkan ketiga berkas HTML hasil konversi tersebut.*

### Langkah 4: Penyebaran (*Deployment*) via GitHub Pages (tidak diperlukan jika langkah sebelumnya sudah dikerjakan secara online)

1. Lakukan *commit* dan dorong (*push*) seluruh berkas proyek Anda ke repositori GitHub:Bash
    
    ```
    git add .
    git commit -m "Menyelesaikan simulasi Model Ising 2D dan kompilasi HTML"
    git push origin main
    ```
    
2. Buka halaman repositori Anda di GitHub melalui peramban, lalu masuk ke menu **Settings** > **Pages**.
3. Pada bagian **Build and deployment**, ubah parameter Source menjadi **Deploy from a branch**.
4. Pada opsi pemilihan Branch, pilih opsi **main**, lalu ubah direktori folder dari `/(root)` menjadi `/docs`.
5. Klik **Save**. Dalam waktu beberapa menit, situs portofolio komputasi fisika Anda akan aktif dan dapat diakses secara publik.

## Kriteria Evaluasi

Penilaian terhadap hasil modifikasi dan pengerjaan tugas ini didasarkan pada aspek-aspek berikut:

1. **Akurasi Matematis dan Fisis:** Ketepatan formulasi matematis dalam menghitung selisih energi lokal $\Delta E = 2s_{i,j} \sum s_{\text{tetangga}}$ dengan menerapkan kondisi batas periodik (*periodic boundary conditions*) menggunakan operasi modulo , serta kebenaran implementasi probabilitas penerimaan Metropolis $\mathcal{R} = e^{-\Delta E / T}$.
2. **Efisiensi Komputasi:** Kebersihan struktur kode Python, penulisan dokumentasi/komentar yang informatif , serta optimalisasi algoritma dengan memanfaatkan perhitungan energi lokal alih-alih menghitung ulang energi total seluruh kisi pada setiap iterasi.
3. **Komunikasi Ilmiah:** Kejelasan visualisasi data yang disajikan (kelengkapan label sumbu, judul grafik, dan skala yang tepat)  serta kedalaman analisis teoretis fisis yang dituliskan pada penjelasan teks.

## Referensi dan Sumber Data

- Landau, D. P., dkk. *A Guide to Monte Carlo Simulations in Statistical Physics* (Bab 17.2: Aturan Implementasi).
- Rifani, Agus. *Modul Pembelajaran: Simulasi Model Magnet dan Transisi Fasa*.

## Penggunaan AI

Contohnya kalian menuliskan: 

Pada pengerjaan *case-based* ini, kami menggunakan:

1. **Gemini 3.1 Pro** untuk mendesain struktur instruksi tugas serta melakukan optimasi sintaksis algoritma Metropolis pada potongan kode simulasi;
2. **Claude Sonnet 4.6** untuk memvalidasi penalaran fisis penurunan persamaan energi lokal dan penataan komponen dokumen markdown.

## Penggunaan Aplikasi Lain

Contohnya seperti ini

1. **Jupyter Software** untuk menyediakan lingkungan eksekusi kode secara interaktif, penulisan analisis berbasis teks formal, dan penampilan visualisasi kurva magnetisasi secara *inline*.
2. **Miniconda** untuk manajemen isolasi lingkungan virtual (*virtual environment*) Python guna memastikan kestabilan versi pustaka `numpy` dan `matplotlib` yang digunakan.
