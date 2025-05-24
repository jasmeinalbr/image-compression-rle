# 📄 LAPORAN KOMPRENSI GAMBAR MENGGUNAKAN ALGORITMA RLE (Run-Length Encoding)

## 🔍 1. Latar Belakang

Kompresi gambar adalah proses untuk mengurangi ukuran file gambar agar lebih efisien dalam penyimpanan dan pengiriman. Salah satu teknik kompresi lossless (tanpa kehilangan data) yang sederhana adalah Run-Length Encoding (RLE).

RLE bekerja dengan cara mencatat berapa kali sebuah nilai piksel muncul secara berurutan. Teknik ini sangat cocok untuk gambar yang banyak memiliki area warna yang sama, seperti gambar grayscale atau hitam-putih.

## 🧠 2. Algoritma Kompresi: Run-Length Encoding (RLE)

**Apa itu RLE?**

Run-Length Encoding (RLE) adalah algoritma kompresi lossless yang menyimpan data dengan cara mendeteksi pengulangan berturut-turut dari elemen yang sama.

Contoh sederhana:

Data asli (grayscale): 150, 150, 150, 150, 149, 149, 200

Setelah dikompresi dengan RLE: (150, 4), (149, 2), (200, 1)

Artinya:

Piksel bernilai 150 muncul 4 kali,

Nilai 149 muncul 2 kali,

Nilai 200 muncul 1 kali.

Setiap pasangan disimpan sebagai nilai dan jumlah kemunculannya.

### Kelebihan RLE:
1. Mudah diimplementasikan.
2. Sangat efisien untuk gambar dengan banyak piksel yang sama (contoh: background putih polos, dokumen hasil scan hitam-putih).

### Kekurangan RLE:
1. Tidak cocok untuk gambar yang punya banyak variasi warna atau gradasi halus, karena perubahan kecil antar piksel membuat hasil kompresi jadi lebih besar.

## 🧪 3. Proses Eksperimen

**📁 Dataset:**

- Jumlah gambar: 10 file
- Format gambar: .jpg (JPEG)
- Resolusi bervariasi: dari 640×426 piksel hingga 4118×2740 piksel
- Gambar-gambar disimpan di folder: images/

### 🔧 Langkah-langkah Kompresi:

1. Membaca gambar dari folder menggunakan Python.
2. Mengubah gambar menjadi grayscale (abu-abu, 1 channel), agar proses lebih sederhana dan efisien.
3. Mengubah piksel gambar menjadi array 1 dimensi (flatten) agar bisa diproses dengan algoritma RLE.
4. Mengompresi array piksel dengan RLE, yaitu mencatat nilai piksel dan berapa kali nilai tersebut muncul secara berurutan.
5. Menyimpan hasil kompresi ke file baru dengan ekstensi .rle.
6. Menghitung ukuran file asli dan file hasil kompresi, lalu dibandingkan.

## 📊 4. Hasil Kompresi

| Nama File                | Ukuran Asli (Byte) | Ukuran RLE (Byte) |
| ------------------------ | -----------------: | ----------------: |
| sample\_640x426\_1.jpg   |           24,594 B |          62,096 B |
| sample\_640x426\_2.jpg   |           22,734 B |          63,498 B |
| sample\_1280x853\_1.jpg  |           74,195 B |         218,396 B |
| sample\_1280x853\_2.jpg  |           75,354 B |         218,215 B |
| sample\_1280x853\_3.jpg  |           73,943 B |         218,172 B |
| sample\_1920x1280\_1.jpg |          121,025 B |         491,582 B |
| sample\_1920x1280\_2.jpg |          118,264 B |         487,897 B |
| sample\_1920x1280\_3.jpg |          117,562 B |         487,910 B |
| sample\_3000x2000.jpg    |          239,859 B |         952,742 B |
| sample\_4118x2740.jpg    |          598,268 B |       2,257,832 B |

## 📌 5. Analisis Hasil

Dari tabel di atas, terlihat bahwa ukuran file hasil kompresi RLE justru lebih besar daripada ukuran file asli JPEG. Hal ini disebabkan oleh:
1. JPEG adalah format kompresi lossy, yang sudah sangat efisien untuk menyimpan gambar foto berwarna.
2. Sedangkan RLE hanya efisien jika banyak piksel yang identik dan berurutan (misalnya background putih polos).
3. Dalam foto nyata, meskipun warnanya mirip, pikselnya jarang 100% sama dan berurutan. Akibatnya, RLE harus menyimpan banyak pasangan (nilai, jumlah) untuk setiap variasi piksel kecil, yang membuat file membengkak.

## 📚 6. Kesimpulan
- RLE cocok digunakan untuk gambar yang memiliki banyak pengulangan warna, seperti citra hitam-putih hasil scan atau hasil threshold.
- Untuk gambar nyata (foto) berformat JPEG, RLE tidak efektif karena ukuran file hasil kompresi menjadi jauh lebih besar.
- Percobaan ini menunjukkan bahwa jenis algoritma kompresi harus disesuaikan dengan jenis dan isi gambar yang akan dikompresi.

## ✅ 7. Saran
- Gunakan RLE hanya untuk data biner atau gambar dengan sedikit warna (contoh: hasil OCR, peta biner, citra medikal hitam-putih).
- Untuk kompresi gambar umum/foto, sebaiknya tetap gunakan format seperti JPEG, PNG, atau WebP yang dirancang khusus untuk efisiensi penyimpanan gambar.