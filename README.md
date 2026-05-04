# T4-mobile

Nama : Apriesna Zulhan
NIM  : F1D02310100

Aplikasi Student Contact App Merupakan aplikasi berbasis android yang dirancang untuk mengelola data mahasiswa, pengguna dapat menambahkan, mengedit, dan menghapus data mahasiswa dengan mudah.

Halaman Login
<img width="1080" height="2400" alt="image" src="https://github.com/user-attachments/assets/dd3b5025-a80f-4693-a83e-4fbb7782217e" />

Daftar Mahasiswa 
<img width="1080" height="2400" alt="image" src="https://github.com/user-attachments/assets/6d1e1412-f679-4b82-8df4-ca8c1893fa6b" />

Detail Mahasiswa
<img width="1080" height="2400" alt="image" src="https://github.com/user-attachments/assets/e9bf17e0-f1c2-446f-bc0c-bf43fbfdff30" />

Student Directory
<img width="1080" height="2400" alt="image" src="https://github.com/user-attachments/assets/9044a652-a3bd-48b5-85f0-a2b340dc4a6a" />

Edit Data Mahasiswa 
<img width="1080" height="2400" alt="image" src="https://github.com/user-attachments/assets/ddb4ed07-9291-4abf-9eba-ef25685cf0a8" />

Hapus Data Mahasiswa
<img width="1080" height="2400" alt="image" src="https://github.com/user-attachments/assets/b63c81ec-e296-4436-ad7d-6330916b8dc7" />

Profie Admin/Zulhan
<img width="1080" height="2400" alt="image" src="https://github.com/user-attachments/assets/c007d107-f346-4e25-a1d1-e157d37f204c" />


## 💾 Metode Penyimpanan

| Metode | Digunakan Untuk |
|---|---|
| **Room Database** | Data mahasiswa (CRUD: nama, NIM, prodi, email, semester) |
| **SharedPreferences** | Sesi login & preferensi pengguna (dark mode, font size, notifikasi) |
| **Internal File Storage** | Catatan per mahasiswa, disimpan sebagai `.txt` dengan nama file berdasarkan NIM |

**Alasan pemilihan:**
- Room dipilih karena data mahasiswa bersifat terstruktur dan membutuhkan operasi pencarian/filter
- SharedPreferences cocok untuk data key-value ringan seperti status login dan pengaturan tampilan
- Internal File Storage digunakan untuk teks bebas (catatan) yang tidak memerlukan struktur tabel

---

## ⚠️ Kendala & Solusi

**1. Migrasi Database**
Saat skema Room berubah (versi 1 → 2), digunakan `fallbackToDestructiveMigration()` agar tidak crash. Konsekuensinya data terhapus saat versi naik — cukup untuk tahap development.

**2. Duplikasi FileHelper**
Terdapat dua file `FileHelper.kt` di package berbeda. Diselesaikan dengan mengacu hanya pada versi di `utils/` yang lebih lengkap.

**3. Coroutine Tanpa ViewModel**
Operasi Room berjalan di `suspend fun` tanpa ViewModel, sehingga lifecycle management dilakukan manual menggunakan `lifecycleScope` di Activity/Fragment.




