# Modul Praktikum Pertemuan 5: Working with Foundation Model (Part 1)

**Mata Kuliah:** Pemanfaatan AI Generative untuk Pengembangan Aplikasi  
**Kode Mata Kuliah / SKS:** KK140114_22 / 4 SKS  
**Topik:** Pengenalan Foundation Model (Menjalankan Foundation Model di Google Colab)

---

## 1. Nama Praktikum
Pengenalan Foundation Model: Menjalankan Foundation Model di Google Colab

## 2. Target Kompetensi
1. Mahasiswa mampu membuat akun, mengelola *Access Token*, dan mengambil ID *Foundation Model* dari platform Hugging Face.
2. Mahasiswa mampu mengonfigurasi lingkungan komputasi Google Colab berbasis GPU (T4) serta menjalankan *Foundation Model* **Qwen** untuk menghasilkan respons teks (*inference*).
3. Mahasiswa mampu menjalankan *Foundation Model* lain yaitu **Gamma (Google Gemma)** secara mandiri di Google Colab dengan mengadaptasi alur kerja pemanggilan model dari praktikum.

## 3. Alat/Tools yang Digunakan
1. **Google Colaboratory** (https://colab.research.google.com) dengan akselerator *Hardware* **T4 GPU**.
2. **Akun Hugging Face** (https://huggingface.co) sebagai repositori penyedia *Foundation Model*.
3. **Framework/Library Python:** `torch`, `transformers`, `accelerate`, dan `huggingface_hub`.
4. **Foundation Model:**
   - **Praktikum Kelas:** `Qwen/Qwen2.5-1.5B-Instruct` (https://huggingface.co/Qwen/Qwen2.5-1.5B-Instruct)
   - **Tugas Mandiri:** `google/gemma-2-2b-it` (https://huggingface.co/google/gemma-2-2b-it) atau repositori alternatif `unsloth/gemma-2-2b-it` (https://huggingface.co/unsloth/gemma-2-2b-it)

---

## 4. Daftar File pada Repository Ini
1. `Praktikum5_Menjalankan_Foundation_Model_Qwen.ipynb` : Notebook panduan praktikum di kelas menggunakan model **Qwen**.
2. `Tugas_Pertemuan_5_Menjalankan_Foundation_Model_Gamma.ipynb` : Template notebook kosong yang wajib diunduh dan dilengkapi oleh mahasiswa untuk tugas mandiri menggunakan model **Gamma (Gemma)**.

---

## 5. Langkah-Langkah Praktikum

### Tahap A: Persiapan Akun & Pembuatan Access Token di Hugging Face
Untuk memanggil *Foundation Model* dari Hugging Face ke dalam Google Colab, kita menggunakan **ID Model** dan **Access Token** melalui kode Python.

1. Buka situs https://huggingface.co.
2. Klik **Sign Up** di pojok kanan atas untuk mendaftar akun baru (jangan lupa lakukan verifikasi email), atau klik **Login** jika sudah memiliki akun.
3. Setelah berhasil masuk, buka halaman pembuatan token di: https://huggingface.co/settings/tokens.
4. Klik tombol **+ Create new token**.
5. Pilih tipe *Permissions* **Read** (di bagian atas).
6. Pada kolom **Token name**, ketik nama token bebas, misalnya: `praktikum-colab`.
7. Gulir ke bawah dan klik **Create token**.
8. Ketika jendela **Save your Access Token** muncul (berisi kode berawalan `hf_...`), klik tombol **Copy** dan simpan kode tersebut di *Notepad* pribadi Anda karena kode ini hanya ditampilkan satu kali, kemudian klik **Done**.

### Tahap B: Cara Mencari dan Menyalin ID Model di Hugging Face
1. Klik menu **Models** di bagian atas halaman Hugging Face (https://huggingface.co/models).
2. Ketik nama model pada kolom pencarian, misalnya: `Qwen2.5-1.5B-Instruct`, lalu klik hasil **`Qwen/Qwen2.5-1.5B-Instruct`**.
3. Di bagian kiri atas halaman model, klik ikon **Copy** di sebelah nama `Qwen/Qwen2.5-1.5B-Instruct`. Teks dengan format `Pembuat/Nama-Model` inilah yang disebut **ID Model**.
4. **Khusus untuk Tugas Mandiri Model Gamma (`google/gemma-2-2b-it`):**
   - Kunjungi halaman https://huggingface.co/google/gemma-2-2b-it.
   - Klik tombol **Acknowledge license** pada halaman tersebut dan setujui ketentuan penggunaannya agar akun Hugging Face Anda diizinkan mengakses model tersebut.
   - Apabila akun Anda terkendala persetujuan lisensi, Anda dapat menggunakan ID model alternatif yang terbuka langsung tanpa lisensi tambahan, yaitu: **`unsloth/gemma-2-2b-it`** (https://huggingface.co/unsloth/gemma-2-2b-it).

### Tahap C: Konfigurasi GPU & Eksekusi Praktikum di Google Colab
1. Unduh file `Praktikum5_Menjalankan_Foundation_Model_Qwen.ipynb` dari repositori ini, lalu buka di https://colab.research.google.com (**File -> Upload notebook**).
2. Ubah konfigurasi *runtime* ke GPU:
   - Klik menu **Runtime** di bagian atas -> pilih **Change runtime type**.
   - Pastikan **Runtime type** adalah `Python 3`.
   - Pada bagian **Hardware accelerator**, pilih **T4 GPU**.
   - Klik **Save**.
3. Jalankan sel **Tahap 1** untuk memastikan status `Is GPU Available? : True` dan menginstal library `transformers`, `accelerate`, serta `huggingface_hub`.
4. Jalankan sel **Tahap 2 (`login()`)**, lalu tempelkan (*paste*) kode token `hf_...` milik Anda pada kotak input yang muncul.
5. Jalankan sel **Langkah 1** untuk mengunduh *Tokenizer* dan bobot model `Qwen/Qwen2.5-1.5B-Instruct` ke dalam GPU.
6. Jalankan sel **Langkah 2** dan **Langkah 3** untuk menguji respons model Qwen pada 3 variasi *prompt* studi kasus **Softyum** (Keputusan Membeli Dompet, Kondisi Alergi Makanan di Warteg, dan Keputusan Memperbaiki Sepatu).

---

## 6. Tugas Praktikum (Asesmen Mandiri)
Setelah menyelesaikan praktikum model Qwen, mahasiswa wajib mengerjakan tugas mandiri yaitu **menjalankan Foundation Model lain yaitu Gamma (Google Gemma)** dengan langkah berikut:

1. Unduh file template `Tugas_Pertemuan_5_Menjalankan_Foundation_Model_Gamma.ipynb` dari repositori ini dan buka di Google Colab.
2. Aktifkan **T4 GPU** pada menu *Change runtime type*.
3. Lengkapi seluruh sel kode yang masih kosong pada template tersebut dengan mengikuti struktur kode yang telah dipelajari pada notebook praktikum Qwen:
   - Memeriksa GPU dan menginstal library pendukung.
   - Melakukan autentikasi `login()` Hugging Face.
   - Memuat (*load*) *Tokenizer* dan *Model* Gamma (`google/gemma-2-2b-it` atau `unsloth/gemma-2-2b-it`) ke dalam GPU.
   - Membuat function inference `jalankan_gamma()` untuk menghasilkan respons teks dari model. *(Catatan: Pastikan hanya menggunakan `"role": "user"` pada variabel `messages`).*
   - Menjalankan ke-3 *prompt* kasus **Softyum** yang sama seperti pada praktikum Qwen.
4. Lengkapi tabel pengamatan hasil jawaban antara model Qwen dan model Gamma beserta kesimpulan singkat pada bagian akhir notebook.

---

## 7. Format Laporan dan Pengumpulan
Mahasiswa wajib mengumpulkan **2 (dua) file** secara langsung ke LMS Layar sebelum batas waktu berakhir:

1. **File Notebook Tugas (`.ipynb`):**
   - Pastikan seluruh sel kode pada file tugas telah dijalankan (*Run*) sehingga seluruh *output* teks tampil lengkap di bawah setiap sel kode.
   - Unduh dari Google Colab melalui menu **File -> Download -> Download .ipynb**.
   - Format nama file: `Tugas5_[NPM]_[NamaLengkap].ipynb`
2. **File Laporan Praktikum (`.pdf`):**
   - Berisi identitas mahasiswa (Nama dan NPM), *screenshot* bukti hasil eksekusi praktikum (Qwen) dan tugas (Gamma), tabel pengamatan jawaban kedua model pada kasus Softyum, serta kesimpulan.
   - Format nama file: `LaporanP5_[NPM]_[NamaLengkap].pdf`

---

## 8. Rubrik Penilaian (Total: 100 Poin)

| No | Komponen Penilaian | Bobot Maksimal | Poin Penuh (Selesai & Tepat) | Setengah Poin (Kurang Lengkap / Error Sebagian) | 0 Poin (Tidak Dikerjakan / Gagal) |
| :-: | :--- | :---: | :--- | :--- | :--- |
| 1 | **Persiapan GPU, Instalasi Library & Login HF** | **20 Poin** | **20 Poin:** GPU T4 aktif (`True`), seluruh library terinstal tanpa konflik, dan proses autentikasi `login()` berhasil dijalankan. | **10 Poin:** Library terinstal namun *runtime* belum diubah ke GPU T4 (`False`). | **0 Poin:** Sel kode dibiarkan kosong. |
| 2 | **Load Tokenizer & Model Gamma (Gemma)** | **35 Poin** | **35 Poin:** Berhasil memuat *tokenizer* dan bobot model Gamma (`google/gemma-2-2b-it` atau `unsloth/gemma-2-2b-it`) ke GPU tanpa *error*. | **17 Poin:** Kode pemanggilan model sudah ditulis tetapi masih menghasilkan *error* saat dijalankan. | **0 Poin:** Sel kode dibiarkan kosong. |
| 3 | **Function Inference & Eksekusi 3 Prompt Softyum** | **30 Poin** | **30 Poin:** Function `jalankan_gamma()` berjalan lancar dan berhasil menampilkan jawaban model untuk ke-3 *prompt* kasus Softyum. | **15 Poin:** Function berhasil dibuat tetapi hanya menguji 1–2 *prompt*, atau *output* belum di-*run* saat file diunduh. | **0 Poin:** Function tidak dibuat dan *prompt* tidak dijalankan. |
| 4 | **Tabel Pengamatan, Laporan PDF & Format File** | **15 Poin** | **15 Poin:** Tabel ringkasan jawaban dan kesimpulan terisi lengkap, serta mengumpulkan kedua file (`.ipynb` dan `.pdf`) sesuai format penamaan. | **7 Poin:** Tabel pengamatan kurang lengkap atau hanya mengumpulkan salah satu dari dua file yang diwajibkan. | **0 Poin:** Tidak melampirkan kesimpulan dan format pengumpulan tidak sesuai. |
