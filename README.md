# SIPALUTER – Sistem Penentuan Lulusan Terbaik

<p align="center">
  <img src="picture/SMAN1MANDIRANCAN.png" alt="Logo SMAN 1 Mandirancan" width="120">
</p>

SIPALUTER adalah aplikasi web untuk membantu SMA Negeri 1 Mandirancan memilih siswa yang layak mendapat predikat **Lulusan Terbaik**. Perhitungannya memakai metode **SMART (Simple Multi Attribute Rating Technique)**. Jadi penilaian tidak lagi dihitung manual satu per satu, tapi berdasarkan kriteria dan bobot yang sudah ditentukan sekolah.

Aplikasi ini dibuat dengan CodeIgniter 3, MySQL, dan template AdminLTE.

---

## Cara Kerja Singkat

1. Operator menentukan kriteria penilaian beserta bobotnya.
2. Setiap kriteria punya sub kriteria (rentang nilai) dengan skor 0 sampai 100.
3. Wali kelas / wakasek memasukkan nilai siswa sesuai sub kriteria.
4. Sistem menghitung skor akhir: **nilai sub kriteria × bobot normalisasi**, lalu dijumlahkan untuk semua kriteria.
5. Siswa dengan skor **75 – 100** berstatus **diterima**, sedangkan skor **0 – 74** berstatus **ditolak**.
6. Hasilnya diurutkan dari skor tertinggi (ranking) dan bisa dicetak sebagai laporan.

### Kriteria Bawaan

| Kriteria                  | Bobot | Normalisasi |
| ------------------------- | :---: | :---------: |
| Nilai Rata-rata Raport    |   4   |     0.4     |
| Nilai Ujian Sekolah       |   3   |     0.3     |
| Nilai Ekstrakurikuler     |   1   |     0.1     |
| Nilai Prestasi            |   1   |     0.1     |
| Nilai Presensi Kehadiran  |   1   |     0.1     |

Kriteria dan bobotnya bisa diubah kapan saja oleh operator. Bobot normalisasi akan dihitung ulang otomatis.

---

## Hak Akses Pengguna

Ada empat jenis pengguna, dan menu yang muncul menyesuaikan perannya masing-masing.

| Peran              | Yang bisa dilakukan |
| ------------------ | ------------------- |
| **Operator**       | Kelola kriteria, sub kriteria, tahun akademik, kelas, data siswa, data user, melihat hasil penilaian dan laporan |
| **Wali Kelas**     | Kelola data siswa dan input penilaian |
| **Wakasek**        | Kelola data siswa dan input penilaian |
| **Kepala Sekolah** | Melihat data siswa, hasil penilaian, dan mencetak laporan |

---

## Fitur

### 1. Login
Setiap pengguna masuk dengan username dan password. Setelah login, sistem langsung mengarahkan ke dashboard sesuai hak aksesnya.

![Halaman Login](docs/screenshots/login.png)

### 2. Dashboard
Menampilkan ringkasan jumlah data siswa, kriteria, kelas, dan user. Ada juga grafik pie untuk melihat perbandingan siswa yang diterima dan ditolak.

![Dashboard](docs/screenshots/dashboard.png)

### 3. Data Kriteria
Tempat menambah, mengubah, dan menghapus kriteria penilaian. Saat bobot diisi, sistem otomatis menghitung bobot normalisasinya sehingga totalnya selalu 1.

![Data Kriteria](docs/screenshots/kriteria.png)

### 4. Data Sub Kriteria
Setiap kriteria dipecah lagi menjadi beberapa tingkat. Contohnya untuk nilai raport: ≥ 91 dapat skor 100, 86–90 dapat 75, dan seterusnya sampai ≤ 75 dapat 0.

![Data Sub Kriteria](docs/screenshots/sub-kriteria.png)

### 5. Tahun Akademik
Mengatur tahun ajaran. Hanya satu tahun yang bisa aktif, dan data penilaian yang tampil mengikuti tahun yang sedang aktif.

![Tahun Akademik](docs/screenshots/tahun-akademik.png)

### 6. Data Kelas
Mengelola daftar kelas yang nantinya dipakai untuk mengelompokkan siswa.

![Data Kelas](docs/screenshots/kelas.png)

### 7. Data Siswa
Menyimpan data siswa lengkap dengan kelasnya. Data bisa ditambah satu per satu, atau diimpor sekaligus lewat file Excel. Daftar siswa juga bisa diekspor ke Excel.

![Data Siswa](docs/screenshots/data-siswa.png)

### 8. Penilaian
Wali kelas atau wakasek memilih siswa lalu mengisi nilainya untuk tiap kriteria. Nama siswa bisa dicari dengan fitur autocomplete, jadi tidak perlu mengetik lengkap.

![Penilaian](docs/screenshots/penilaian.png)

### 9. Hasil Penilaian
Menampilkan skor akhir setiap siswa, status diterima/ditolak, serta ranking. Hasil bisa difilter per kelas dan diekspor ke Excel.

![Hasil Penilaian](docs/screenshots/hasil-penilaian.png)

### 10. Laporan
Laporan hasil penentuan lulusan terbaik bisa dicetak ke PDF, lengkap dengan kop sekolah. Laporan juga bisa difilter sebelum dicetak.

![Laporan](docs/screenshots/laporan.png)

### 11. Data User
Operator bisa menambah, mengubah, atau menghapus akun pengguna sekaligus menentukan perannya.

![Data User](docs/screenshots/data-user.png)

---

## Teknologi yang Dipakai

- PHP dengan framework CodeIgniter 3
- MySQL / MariaDB
- AdminLTE + Bootstrap
- DataTables untuk tabel
- Google Charts untuk grafik dashboard
- Dompdf untuk cetak PDF
- PHPExcel untuk impor dan ekspor Excel

---

## Lisensi

Proyek ini menggunakan lisensi MIT. Detailnya ada di file [LICENSE](LICENSE).
