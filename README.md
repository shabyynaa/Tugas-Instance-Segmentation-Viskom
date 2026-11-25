# Tugas Evaluasi CPMK 3: Segmentasi Instance pada Lingkungan Indoor Nyata

| Nama | NRP | Mata Kuliah |
| :--- | :--- | :--- |
| Shabrina Sarayati | 5054241009 | Visi Komputer |

## Struktur Folder Berdasarkan Bukti / Luaran yang Dikumpulkan

| No | Komponen Penilaian | Folder / Berkas di Repositori | Isi Bukti / Luaran |
| :---: | :--- | :--- | :--- |
| **1** | Test set buatan sendiri (wajib) | [`01_Test_Set_Sendiri_dan_Domain_Shift/`](./01_Test_Set_Sendiri_dan_Domain_Shift/) | 44 foto ruangan nyata (`Dataset/`), anotasi COCO & YOLO, screenshot proses anotasi Roboflow, metadata EXIF (`exif_metadata_custom_testset.csv`), serta tabel, grafik, dan analisis *domain shift*. |
| **2** | Parameter unik berdasarkan NRP (Digit 9) | [`02_Parameter_Unik_NRP_3Kelas_Tersulit/`](./02_Parameter_Unik_NRP_3Kelas_Tersulit/) | Tabel CSV dan grafik perbandingan eksperimen **Semua Kelas vs Hanya 3 Kelas Tersulit** (`cabinet-merged`, `pillow`, `wall-tile`) pada ketiga model. |
| **3** | Hipotesis sebelum eksperimen | [`03_Hipotesis_Sebelum_Eksperimen/`](./03_Hipotesis_Sebelum_Eksperimen/) | Entri hipotesis bertanggal sebelum training pertama (18 Nov 2026) beserta evaluasi hasil ketika hipotesis keliru (juga termuat di Bagian 1 `Logbook.pdf`). |
| **4** | Analisis kegagalan berbasis bukti | [`04_Analisis_Kegagalan_Berbasis_Bukti/`](./04_Analisis_Kegagalan_Berbasis_Bukti/) | 5 studi kasus bergambar pada *custom test set*, audit 44 foto, serta tabel dan grafik bukti 2 eksperimen kecil pembuktian. |
| **5** | Bukti proses | [`05_Bukti_Proses_Log_dan_Logbook/`](./05_Bukti_Proses_Log_dan_Logbook/) | `Logbook.pdf`, catatan waktu pelatihan GPU (`gpu_time_total_summary.csv`), kurva training, dan seluruh file log asli (`results.csv` & TensorBoard). |
| **6** | Penggunaan AI | [`06_Deklarasi_Penggunaan_AI/`](./06_Deklarasi_Penggunaan_AI/) | Lampiran deklarasi penggunaan AI beserta kasus kode AI yang kurang tepat dan cara memperbaikinya. |
| **7** | Demo dan tanya jawab | [`07_Demo_Inferensi_Foto_Baru/`](./07_Demo_Inferensi_Foto_Baru/) | Notebook dan hasil inferensi langsung ketiga model pada foto baru yang belum dianotasi (`foto_demo_baru.jpg`). |
| **-** | Notebook Utama Pelatihan & Eksperimen | [`5054241009_Training Notebook.ipynb`](./5054241009_Training%20Notebook.ipynb)<br>[`5054241009_Notebook_Eksperimen.ipynb`](./5054241009_Notebook_Eksperimen.ipynb) | Kode lengkap pelatihan Tahap 1 (Semua Kelas) dan eksperimen Tahap 2 (*Domain Shift*, 3 Kelas Tersulit, dan *Failure Analysis*). |

## Deklarasi Penggunaan AI

Pada pengerjaan tugas ini, **Gemini** digunakan untuk membantu menjelaskan alur pengerjaan dari awal (urutan langkah yang perlu dilakukan) serta membantu menyusun beberapa bagian kode untuk pelatihan, evaluasi, dan visualisasi hasil eksperimen di Google Colab.

**Kasus kode dari AI yang kurang tepat dan cara memperbaikinya:**
Saat mengevaluasi Mask R-CNN pada custom test set, kode awal dari AI langsung memproses foto kamera HP ukuran penuh (3024x4032 piksel) di GPU dengan `batch_size=2`. Hal ini menyebabkan error `CUDA OutOfMemoryError` karena memori GPU Colab habis saat menyesuaikan ukuran mask ke resolusi asli. Kode tersebut diperbaiki dengan memperkecil batas ukuran gambar yang masuk ke GPU, mengubah `batch_size` menjadi 1, dan memindahkan proses penyesuaian ukuran mask ke CPU sehingga evaluasi berjalan lancar.
