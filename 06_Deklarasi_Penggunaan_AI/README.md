# 6. Lampiran Deklarasi Penggunaan AI

**Alat AI yang digunakan:** Gemini

**Lingkup penggunaan:**
Pada pengerjaan tugas ini, **Gemini** digunakan untuk membantu menjelaskan alur pengerjaan dari awal (urutan langkah yang perlu dilakukan) serta membantu menyusun beberapa bagian kode untuk pelatihan, evaluasi, dan visualisasi hasil eksperimen di Google Colab. Pengambilan foto ruangan nyata, proses anotasi polygon di Roboflow, eksekusi pelatihan model, serta pemeriksaan hasil dilakukan sendiri.

### Contoh Prompt Utama yang Digunakan
1. Meminta penjelasan urutan pengerjaan tugas dari persiapan dataset hingga tahap eksperimen dan analisis kegagalan.
2. Meminta bantuan penyusunan kode Google Colab untuk melatih dan mengevaluasi YOLOv8s-seg, Mask R-CNN, dan Mask2Former beserta penyimpanan file log dan pencatatan waktu GPU.
3. Meminta bantuan penyusunan kode pemfilteran dataset 3 kelas tersulit, evaluasi *custom test set*, dan visualisasi perbandingan hasil prediksi.

### Kasus Kode dari AI yang Kurang Tepat dan Cara Memperbaikinya
Saat mengevaluasi Mask R-CNN pada *custom test set*, kode awal dari AI langsung memproses foto kamera HP ukuran penuh (3024x4032 piksel) di GPU dengan `batch_size=2`. Hal ini menyebabkan error `CUDA OutOfMemoryError` (`Tried to allocate 4.54 GiB` pada fungsi `paste_masks_in_image`) karena memori GPU Colab habis saat menyesuaikan ukuran banyak mask sekaligus ke resolusi 12 MP. Kode tersebut diperbaiki dengan membatasi sisi terpanjang gambar yang masuk ke GPU (`1333` piksel), mengubah `batch_size` menjadi `1`, dan memindahkan proses penyesuaian ukuran mask ke CPU hanya untuk prediksi yang lolos *threshold*, sehingga seluruh evaluasi dan pelatihan 3 kelas tersulit berjalan lancar.
