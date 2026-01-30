# Excel to Line Converter

Aplikasi web sederhana untuk mengubah data dari Excel (satu kolom atau data yang belum bersih) menjadi satu baris dengan pembatas kustom. Cocok untuk menyiapkan daftar ID, kode, atau nilai lain agar mudah ditempel ke aplikasi lain.

## Fitur Utama

- **Konversi otomatis saat paste**: tempel data dari Excel dan hasil langsung diproses serta tersalin ke clipboard.
- **Mode data belum bersih**: membersihkan karakter seperti `(Released)`, tanda `;`, spasi berlebih, dan kolom kosong.
- **Pembatas fleksibel**: pilih pembatas bawaan (`,`, `;`, `|`, spasi, baris baru) atau isi pembatas kustom.
- **Hapus duplikat**: opsi untuk menghapus data duplikat sebelum digabungkan.
- **Statistik realtime**: melihat jumlah baris diproses, baris unik, panjang hasil, dan pembatas aktif.
- **Tombol cepat**: proses manual, salin ulang hasil, sembunyikan hasil, dan reset semua.

## Demo Singkat (Alur Pakai)

1. Buka `index.html` di browser.
2. Salin data dari Excel (satu kolom) atau data mentah Anda.
3. Tempelkan ke area teks pada tab yang sesuai:
   - **Konversi Data** untuk data yang sudah rapi.
   - **Data Belum Bersih** untuk data dengan format semacam `;IR00974264 (Released)`.
4. Hasil akan langsung muncul dan otomatis tersalin.
5. Tempel hasil ke aplikasi tujuan Anda.

## Struktur Proyek

```
.
├── index.html   # Aplikasi utama (UI + logika JS)
└── test.html    # File uji (opsional, jika ada)
```

## Cara Menjalankan

Karena ini aplikasi berbasis HTML murni (tanpa build), cukup buka langsung di browser.

### Opsi 1: Buka langsung

Klik dua kali `index.html` atau drag & drop ke browser.

### Opsi 2: Jalankan dengan server lokal (disarankan)

Jika Anda ingin menghindari keterbatasan clipboard di beberapa browser, jalankan dengan server lokal:

```bash
python -m http.server 8000
```

Lalu buka: `http://localhost:8000/index.html`

## Cara Menggunakan

### 1) Konversi Data (tab **Konversi Data**)

- Tempelkan data dari Excel (satu kolom).
- Sistem akan:
  - Memisahkan baris berdasarkan newline.
  - Menghapus baris kosong.
  - Menghapus duplikat (opsional).
  - Menggabungkan semuanya dengan pembatas yang dipilih.

**Contoh input:**
```
IO00895128
IO00885689
IO00875123
```

**Output (pembatas `;`)**:
```
IO00895128;IO00885689;IO00875123
```

### 2) Data Belum Bersih (tab **Data Belum Bersih**)

- Tempel data mentah seperti berikut:
  - Mengandung tanda `;`
  - Mengandung teks `(Released)`
  - Memiliki spasi/kosong

Sistem akan membersihkan data terlebih dahulu sebelum digabungkan.

**Contoh input:**
```
;IR00974264 (Released)
;IR00974265 (Released)
```

**Output (pembatas `,`)**:
```
IR00974264,IR00974265
```

## Opsi Pembatas

Anda bisa memilih pembatas dari dropdown atau isi sendiri:

- `;` (Titik koma)
- `,` (Koma)
- `|` (Pipe)
- `Spasi`
- `Baris Baru`
- `Tanpa pembatas`
- **Kustom**: isi teks sesuai kebutuhan (contoh: `--`, `::`, ` / `)

> Catatan: jika pembatas kustom diisi, nilai dropdown akan diabaikan.

## Opsi Hapus Duplikat

Jika checkbox **Hapus data duplikat dari hasil** aktif:

- Data akan diubah menjadi daftar unik.
- Statistik akan menampilkan berapa duplikat yang dihapus.

## Tombol Aksi

- **Proses Manual**: memproses data jika Anda tidak menggunakan auto-paste.
- **Salin Ulang**: menyalin ulang hasil terakhir ke clipboard.
- **Sembunyikan Hasil**: menyembunyikan panel hasil.
- **Reset Semua**: mengosongkan input dan mengembalikan pengaturan.

## FAQ

**1. Kenapa hasil tidak otomatis tersalin?**  
Beberapa browser memerlukan halaman berjalan di HTTPS atau server lokal agar clipboard dapat diakses. Jalankan dengan `python -m http.server` untuk solusi cepat.

**2. Data saya tidak terpecah dengan benar**  
Pastikan data ditempel dari Excel dalam satu kolom. Jika data memiliki tab/kolom, gunakan mode **Data Belum Bersih** agar diproses ulang.

**3. Bisa untuk banyak kolom?**  
Aplikasi ini fokus pada satu kolom. Jika data Anda multi-kolom, tempel pada tab **Data Belum Bersih** agar tab diperlakukan sebagai pemisah.

## Kontribusi

Pull request dan saran perbaikan selalu diterima. Silakan buat issue atau PR jika ada ide tambahan.

## Lisensi

Belum ditentukan. Silakan tambahkan file LICENSE jika diperlukan.
