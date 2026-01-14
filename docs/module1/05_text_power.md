# LOG ENTRY #CLI-05

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## The Power of Text

Salah satu kekuatan utama CLI adalah kemampuannya dalam mengelola dan mencari data berbasis teks dengan sangat efisien.
Dengan beberapa perintah sederhana, kamu bisa menemukan file, mencari isi file, dan memanipulasi banyak file sekaligus menggunakan pola tertentu.

---

## Wildcards

Wildcards adalah karakter khusus yang digunakan untuk mewakili satu atau beberapa karakter dalam nama file atau folder.
Dengan wildcards, kamu bisa memilih banyak file sekaligus tanpa harus mengetik satu per satu.

- `*` : Mewakili nol atau lebih karakter apa saja.
    - Contoh: `ls *.txt` akan menampilkan semua file yang berakhiran `.txt`.
- `?` : Mewakili tepat satu karakter apa saja.
    - Contoh: `ls file?.txt` akan menampilkan `file1.txt`, `fileA.txt`, dll.

Contoh lain penggunaan wildcard:

```bash
cp *.jpg backup/
```
Menyalin semua file dengan ekstensi `.jpg` ke folder `backup`.

```bash
rm data_202?.csv
```
Menghapus semua file dengan nama seperti `data_2021.csv`, `data_2022.csv`, dst.

---

## Mencari di Dalam File: `grep`

Perintah `grep` digunakan untuk mencari teks tertentu di dalam satu atau banyak file.
Ini sangat berguna untuk menemukan baris yang mengandung kata kunci tertentu.

```bash
grep kata_kunci nama_file.txt
```

Contoh:

```bash
grep error log.txt
```
Menampilkan semua baris yang mengandung kata "error" di file `log.txt`.

### `grep` Flags

- `-i` : Tidak membedakan huruf besar/kecil (case-insensitive).
- `-n` : Menampilkan nomor baris.
- `-r` : Mencari secara rekursif di semua file dalam folder.

Contoh:

```bash
grep -in todo *.md
```
Mencari kata "todo" (tanpa peduli kapitalisasi) di semua file `.md` dan menampilkan nomor baris.

---

## Mencari File/Folder: `find`

Perintah `find` digunakan untuk mencari file atau folder berdasarkan nama, tipe, atau kriteria lain.

```bash
find path -name "pola"
```

Contoh:

```bash
find . -name "*.txt"
```
Mencari semua file `.txt` di direktori saat ini dan subfoldernya.

```bash
find /home/user/Documents -type d -name "backup*"
```
Mencari semua folder yang namanya diawali "backup" di dalam `/home/user/Documents`.

### `find` Flags

- `-type f` : Cari hanya file.
- `-type d` : Cari hanya folder.
- `-iname` : Cari tanpa membedakan huruf besar/kecil.

---

## Summary

| Perintah                | Fungsi                                         |
|-------------------------|------------------------------------------------|
| `*`, `?` (wildcards)    | Memilih banyak file dengan pola tertentu       |
| `grep`                  | Mencari teks di dalam file                     |
| `find`                  | Mencari file atau folder berdasarkan nama      |

---

## Next Step

Sekarang kamu sudah memahami apa itu wildcards.
Kamu bisa gunakan wildcard pada banyak hal selain `grep` dan `find`.
Gunakanlah wildcard untuk membuat pola teks agar tidak perlu mengetik semua kemungkinannya secara manual.
Selanjutnya kita akan belajar aliran data dari output terminal hingga ke dalam file.

[Lanjut ke I/O Redirection](06_io_redirection.md){ .md-button .md-button--primary }
