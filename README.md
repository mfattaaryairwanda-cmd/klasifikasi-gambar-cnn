# Klasifikasi Gambar Pemandangan Menggunakan CNN dan MobileNetV2

## Deskripsi Proyek

Proyek ini membahas klasifikasi gambar pemandangan ke dalam enam kategori: **buildings, forest, glacier, mountain, sea,** dan **street**. Model dikembangkan menggunakan Python dan TensorFlow/Keras untuk mempelajari alur klasifikasi gambar, mulai dari pemuatan data dan prapemrosesan hingga pelatihan dan evaluasi model.

Repositori ini memiliki dua notebook:
- `Model.ipynb` — notebook model CNN.
- `Model - MobileNetV2.ipynb` — notebook eksperimen CNN dan MobileNetV2.

## Tujuan

- Memahami proses klasifikasi gambar menggunakan CNN.
- Melakukan prapemrosesan dan augmentasi gambar.
- Melatih model untuk mengenali enam kategori pemandangan.
- Mengevaluasi hasil model menggunakan akurasi, loss, confusion matrix, dan classification report.
- Mempelajari penggunaan MobileNetV2 untuk eksperimen transfer learning.

## Dataset

Dataset disimpan dalam dua folder utama:
- `seg_train/` — data pelatihan.
- `seg_test/` — data pengujian.

Jumlah data yang tercatat pada notebook:

| Bagian | Jumlah gambar |
|---|---:|
| Data latih | 14.014 |
| Data uji | 2.985 |
| **Total** | **16.999** |

Kelas gambar terdiri dari `buildings`, `forest`, `glacier`, `mountain`, `sea`, dan `street`.

Pastikan setiap folder berisi subfolder berdasarkan kelas agar dapat dibaca oleh fungsi pemuatan dataset dari direktori.

## Struktur Folder

```text
CNN 1/
├── images/
│   ├── confusion_matrix...png
│   ├── confusion_matrix...png
│   ├── learning_curve...png
│   └── learning_curve...png
├── seg_test/
│   ├── buildings/
│   ├── forest/
│   ├── glacier/
│   ├── mountain/
│   ├── sea/
│   └── street/
├── seg_train/
│   ├── buildings/
│   ├── forest/
│   ├── glacier/
│   ├── mountain/
│   ├── sea/
│   └── street/
├── Model - MobileNetV2.ipynb
├── Model.ipynb
└── README.md
```

Nama file gambar di dalam folder `images/` ditulis secara ringkas agar struktur lebih mudah dibaca. Gunakan nama file sebenarnya yang ada di repositori. Folder `images/` berisi visualisasi hasil, sedangkan `seg_train/` dan `seg_test/` berisi dataset.

## Tahapan Pengerjaan

1. Memuat dataset dari folder pelatihan dan pengujian.
2. Memeriksa kelas gambar yang tersedia.
3. Mengubah ukuran gambar menjadi `150 × 150` piksel dan melakukan normalisasi sesuai kode notebook.
4. Melakukan augmentasi gambar, seperti pembalikan horizontal, rotasi, dan zoom.
5. Membangun serta melatih model CNN.
6. Memantau proses pelatihan menggunakan akurasi dan loss.
7. Mengevaluasi model menggunakan data uji.
8. Membuat visualisasi berupa learning curve dan confusion matrix, serta classification report.

## Hasil Evaluasi

### 1. CNN — `Model.ipynb`

| Metrik | Data latih | Data uji |
|---|---:|---:|
| Akurasi | 83,99% | 82,88% |
| Loss | 0,4524 | 0,4952 |

Model CNN memperoleh akurasi data uji sebesar **82,88%**.

Classification report pada data uji:

| Kelas | Precision | Recall | F1-score | Jumlah data |
|---|---:|---:|---:|---:|
| Buildings | 0,78 | 0,82 | 0,80 | 422 |
| Forest | 0,94 | 0,97 | 0,96 | 474 |
| Glacier | 0,82 | 0,76 | 0,78 | 553 |
| Mountain | 0,78 | 0,77 | 0,77 | 525 |
| Sea | 0,80 | 0,83 | 0,81 | 510 |
| Street | 0,86 | 0,85 | 0,85 | 501 |
| **Akurasi keseluruhan** |  |  | **0,83** | **2.985** |

Dari hasil tersebut, kelas `forest` memiliki F1-score tertinggi, yaitu 0,96, sedangkan kelas `mountain` memiliki F1-score terendah, yaitu 0,77.

### 2. Notebook eksperimen — `Model - MobileNetV2.ipynb`

| Metrik | Data latih | Data uji |
|---|---:|---:|
| Akurasi | 85,07% | 83,25% |
| Loss | 0,4198 | 0,4925 |

Notebook kedua mencatat akurasi data uji sebesar **83,25%**. Namun, berdasarkan implementasi yang diperiksa, objek `base_model` MobileNetV2 belum dimasukkan ke dalam model yang dilatih. Dengan demikian, hasil tersebut belum dapat dianggap sebagai hasil MobileNetV2 yang sebenarnya. Perbaiki susunan model terlebih dahulu sebelum menarik kesimpulan tentang transfer learning.

## Visualisasi

Folder `images/` digunakan untuk menyimpan hasil visualisasi, antara lain:
- Confusion matrix.
- Learning curve akurasi dan loss.

Visualisasi membantu melihat kelas yang sering tertukar serta perubahan performa model selama pelatihan.

## Teknologi

- Python
- TensorFlow/Keras
- NumPy
- Matplotlib
- Seaborn
- scikit-learn
- Jupyter Notebook

## Cara Menjalankan

1. Buka folder proyek di VS Code atau Jupyter Notebook.
2. Pastikan dataset berada di folder `seg_train/` dan `seg_test/` sesuai jalur yang dipakai pada notebook.
3. Pasang pustaka yang diperlukan:

   ```bash
   pip install tensorflow numpy matplotlib seaborn scikit-learn jupyter
   ```

4. Buka `Model.ipynb` atau `Model - MobileNetV2.ipynb`.
5. Jalankan sel secara berurutan dari awal hingga akhir.

Hasil pelatihan dapat berbeda bergantung pada lingkungan, konfigurasi, dan proses pengacakan. Jalankan ulang notebook untuk mereproduksi hasil.

## Pengembangan Selanjutnya

- Memperbaiki notebook MobileNetV2 agar model pralatih benar-benar digunakan dalam arsitektur yang dilatih.
- Memastikan prapemrosesan input sesuai dengan kebutuhan MobileNetV2.
- Menggunakan data validasi untuk memantau pelatihan dan menyisihkan data uji untuk evaluasi akhir.
- Meninjau kelas dengan F1-score lebih rendah, terutama `mountain` dan `glacier`.
- Menyimpan model hasil pelatihan agar dapat digunakan kembali untuk prediksi gambar baru.

## Kesimpulan

Model CNN pada `Model.ipynb` memperoleh akurasi data uji sebesar **82,88%** dalam klasifikasi enam kategori gambar pemandangan. Notebook kedua mencatat akurasi **83,25%**, tetapi implementasi MobileNetV2 masih perlu diperbaiki agar hasil eksperimennya benar-benar merepresentasikan penggunaan model tersebut.
