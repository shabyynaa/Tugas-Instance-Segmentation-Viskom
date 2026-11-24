# Tugas Evaluasi CPMK 3: Segmentasi Instance pada Lingkungan Indoor Nyata

| Nama | NRP | Mata Kuliah |
| :--- | :--- | :--- |
| Shabrina Sarayati | 5054241009 | Visi Komputer |

## Deklarasi Penggunaan AI

Pada pengerjaan tugas ini, **Gemini** digunakan untuk membantu menjelaskan alur pengerjaan dari awal (urutan langkah yang perlu dilakukan) serta membantu menyusun beberapa bagian kode untuk pelatihan, evaluasi, dan visualisasi hasil eksperimen di Google Colab.

**Kasus kode dari AI yang kurang tepat dan cara memperbaikinya:**
Saat mengevaluasi Mask R-CNN pada custom test set, kode awal dari AI langsung memproses foto kamera HP ukuran penuh (3024x4032 piksel) di GPU dengan `batch_size=2`. Hal ini menyebabkan error `CUDA OutOfMemoryError` karena memori GPU Colab habis saat menyesuaikan ukuran mask ke resolusi asli. Kode tersebut diperbaiki dengan memperkecil batas ukuran gambar yang masuk ke GPU, mengubah `batch_size` menjadi 1, dan memindahkan proses penyesuaian ukuran mask ke CPU sehingga evaluasi berjalan lancar.
