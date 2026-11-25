# 7. Demo Inferensi Langsung pada Foto Baru (Tanpa Anotasi)

Folder ini berisi notebook dan hasil pengujian langsung ketiga model pada foto ruangan baru (`foto_demo_baru.jpg`) yang belum pernah dianotasi sebelumnya:
- **`Demo_Live_Inference_Foto_Baru.ipynb`**: Notebook inferensi langsung (dilengkapi pengaturan `CONF_THRESH` dan pengecekan AP per kelas).
- **`foto_demo_baru.jpg`**: Foto ruangan baru dengan kombinasi objek dekat (`laptop`, `bottle`, `person`, `table-merged`) dan kondisi *backlight* jendela di latar belakang.
- **`hasil_demo_foto_baru.png`**: Perbandingan hasil segmentasi ketiga model pada `CONF_THRESH = 0.30`.

![Hasil Inferensi Foto Baru](./hasil_demo_foto_baru.png)
