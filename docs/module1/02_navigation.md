# LOG ENTRY #CLI-02

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Navigasi dalam Komputer

Ketika menggunakan komputer, kita selalu berurusan dengan file dan folder.
Setiap file selalu berada di dalam folder, dan folder bisa berada di dalam folder lain.
Inilah yang membentuk struktur hierarkis yang disebut sebagai **file tree**.
Navigasi di dalam file tree ini adalah kemampuan yang sangat penting saat menggunakan CLI.

!!! note
    Di GUI, kita berpindah folder dengan klik. Namun di CLI, kita harus memahami struktur file tree dan menggunakan perintah untuk berpindah dan melihat isi folder.

---

## Struktur File Tree

Bayangkan file tree seperti pohon.
Ada satu akar utama (root), lalu bercabang ke banyak folder dan file.
Di sistem operasi berbasis Unix (Linux, Mac), root dilambangkan dengan `/`.
Di Windows, biasanya root adalah drive seperti `C:\`.

Contoh sederhana struktur file tree:

```
/
├── home/
│   └── user/
│       ├── Documents/
│       │   └── resume.pdf
│       └── Pictures/
│           └── photo.jpg
└── etc/
```

- `/` adalah root directory.
- `home` adalah folder di root.
- `user` adalah folder di dalam `home`.
- Dan seterusnya.

!!! note
    Folder juga dapat disebut sebagai *directory* (direktori). Kedua istilah ini dapat dipakai bergantian, tapi direktori lebih umum digunakan dalam konteks teknis.

---

## Kembali Mengenal Path

Path adalah alamat yang menunjukkan lokasi file atau folder di dalam file tree.
Ada dua jenis path: **absolute path** dan **relative path**.

- **Absolute path**: Selalu dimulai dari root (`/` di Linux/Mac, `C:\` di Windows).
    - Contoh: `/home/user/Documents/resume.pdf`
- **Relative path**: Dimulai dari posisi direktori saat ini.
    - Contoh: `Documents/resume.pdf` (jika kamu sedang berada di `/home/user`)

Simbol penting:

- `.` : direktori saat ini
- `..` : direktori parent
- `~` : home directory (khusus Unix/Linux/Mac)

---

## Posisi Saat Ini: `pwd`

Saat membuka terminal, kamu akan berada di suatu direktori.
Untuk mengetahui di mana kamu berada, gunakan perintah:

```bash
pwd
```

`pwd` adalah singkatan dari **print working directory**.
Perintah ini akan menampilkan path lengkap direktori aktif saat ini.

---

## Melihat Isi Folder: `ls`

Untuk melihat file dan folder di dalam direktori saat ini, gunakan:

```bash
ls
```

Perintah ini akan menampilkan daftar file dan folder.
Namun, secara default, file tersembunyi (hidden) tidak akan terlihat.

### `ls` Flags

- `ls -a` : Menampilkan semua file, termasuk yang tersembunyi (nama diawali dengan titik).
- `ls -l` : Menampilkan daftar dalam format panjang (detail).
- `ls -la` atau `ls -al` : Kombinasi, menampilkan semua file dengan detail.

Contoh:

```bash
ls -la
```

Outputnya akan menampilkan hak akses, pemilik, ukuran, dan tanggal modifikasi file.

---

## Apa itu Flag?

Saat menggunakan perintah di CLI, kamu mungkin pernah melihat tambahan seperti `-l`, `-a`, atau `--help` setelah nama perintah.
Tambahan ini disebut **flag** (atau kadang disebut "option" atau "switch"). Flag digunakan untuk mengubah cara kerja suatu perintah, menambah fitur, atau menampilkan informasi lebih detail.

### Cara Kerja Flag

- Flag biasanya diawali dengan satu atau dua tanda *dash*:
    - Satu dash (`-`) diikuti satu huruf, misal: `-l`
    - Dua dash (`--`) diikuti kata lengkap, misal: `--help`
- Flag bisa digabung, misal: `ls -la` sama dengan `ls -l -a`

Contoh penggunaan flag pada perintah `ls`:

```bash
ls -l
```
Menampilkan daftar file dalam format panjang (detail).

```bash
ls -a
```
Menampilkan semua file, termasuk file tersembunyi.

```bash
ls -la
```
Menggabungkan dua flag: menampilkan semua file dengan detail.

### Dua Bentuk Flag

Flag bisa ditulis dalam bentuk pendeknya (contoh, `ls -h`) atau bentuk lengkapnya (contoh, `ls --help`).
Lalu, mengapa kita tidak menggunakan bentuk pendeknya saja jika lebih mudah dan cepat untuk diketik?
Biasanya, bentuk lengkap suatu file digunakan dalam **scripting** agar script tersebut lebih mudah dibaca.
Oleh sebab itu, perintah CLI masih menyediakan opsi flag dalam bentuk lengkapnya.

### Flag Umum

- `-h` atau `--help` : Menampilkan bantuan atau dokumentasi singkat tentang perintah.
- `-v` atau `--version` : Menampilkan versi dari program/perintah.

!!! tip
    Tidak semua perintah memiliki flag yang sama. Untuk mengetahui flag yang tersedia, gunakan flag `--help` pada perintah yang ingin kamu pelajari, misal:
    ```bash
    ls --help
    ```

Dengan memahami konsep flag, kamu bisa mengeksplorasi lebih banyak fitur dari setiap perintah di terminal.

## Berpindah Direktori: `cd`

Untuk berpindah ke folder lain, gunakan perintah:

```bash
cd nama_folder
```

Beberapa contoh penggunaan:

- `cd Documents` : Masuk ke folder Documents (jika Documents ada di direktori saat ini).
- `cd ..` : Kembali ke direktori induk.
- `cd /home/user` : Pergi ke path absolut `/home/user`.
- `cd ~` : Pergi ke home directory.

!!! tip
    Kamu bisa menggunakan tombol ++tab++ untuk auto-complete nama folder atau file saat mengetik di terminal. ++tab++ juga dapat digunakan untuk auto-complete perintah terminal. Cobalah sering-sering menggunakan tombol ++tab++ agar lebih cepat dalam mengetik di terminal. Lihat [appendix](99_additional.md/#tips--shortcut) untuk tips lebih lanjut.

### Perintah `cd` yang Lain

- `cd -` : Kembali ke direktori sebelumnya dalam history.
- `cd` tanpa argumen : Kembali ke home directory.

---

## Next Step

Sekarang kamu sudah memahami bagaimana cara navigasi dan berpindah di file tree.
Ingatlah bahwa komputer hanyalah sebuah file tree besar yang menyimpan file dan folder kamu.
Komputer memerlukan file untuk dapat melakukan berbagai macam hal.
Selanjutnya kita akan berurusan langsung dengan file dan folder melalui terminal.

[Lanjut ke File Manipulation](03_file_manipulation.md){ .md-button .md-button--primary }
