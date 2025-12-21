# LOG ENTRY #CLI-01

<div class="stamp-box">Status: ARCHIVED</div>
<div class="stamp-box">Clearance: PUBLIC</div>



---

## What Are CLI, Terminal, & Shell?

Pernah dengar istilah CLI, terminal, atau shell?
Bagi banyak orang, istilah-istilah ini terdengar asing.
Padahal, istilah-istilah tersebut sangatlah penting di dunia komputer, terutama bagi programmer.

Kebanyakan dari kita terbiasa dengan **GUI** (Graphical User Interface) yakni suatu antarmuka yang memiliki banyak *icon*, tombol, dan gambar yang bisa diklik atau di-drag.
Misal, saat kamu ingin membuka file, kamu tinggal klik dua kali.
Tapi, sebenarnya ada cara lain yaitu **CLI** (Command Line Interface).

CLI adalah antarmuka berbasis teks, di mana kamu mengetik perintah langsung ke komputer.
Contohnya, kamu bisa menulis perintah untuk memindahkan file, mengganti nama ratusan file sekaligus, atau menjalankan program tertentu, semuanya melalui kode perintah.

Untuk mengakses CLI, kamu butuh aplikasi bernama **terminal**.

---

## Terminal & Shell: What's The Difference?

Dulu, terminal adalah perangkat fisik, sepasang layar dan keyboard yang terhubung ke komputer utama (*mainframe*).
Sekarang, terminal tetap ada sebagai aplikasi di komputer modern yang disebut **terminal emulator** (atau bisa juga tetap disebut terminal).

Namun, terminal hanyalah tempat kamu mengetik perintah.
Agar perintahmu dijalankan, dibutuhkan program bernama **shell**.

- **Terminal**: Tempat kamu mengetik perintah (interface).
- **Shell**: Program yang membaca dan menjalankan perintahmu.

Jadi, saat kamu membuka terminal dan mengeksekusi perintah, shell-lah yang melakukan perintah tersebut.

---

## Why Use CLI?

Mungkin kamu bertanya, "Bukankah GUI lebih mudah?"
Benar, GUI memang ramah pengguna. Tapi CLI juga punya keunggulan:

- **Fleksibilitas**. CLI memungkinkan operasi kompleks yang sulit (atau mustahil) dilakukan di GUI. Misal, mengganti nama 100 file sekaligus dengan pola tertentu.
- **Otomasi**. Kamu bisa menulis skrip untuk menjalankan serangkaian perintah secara otomatis.
- **Kecepatan**. Setelah terbiasa, banyak tugas bisa diselesaikan lebih cepat lewat CLI.
- **Remote Access**. Banyak server hanya bisa diakses lewat CLI, bukan GUI.
- **Tools Khusus**. Banyak alat pemrograman dan administrasi hanya tersedia di CLI.

Tidak semua orang butuh CLI, tapi dengan memahaminya, kamu akan lebih powerful dalam menggunakan komputermu.

---

## Your (Maybe) First CLI Experience

Saatnya mencoba langsung!
Mari buka terminal emulator di komputer masing-masing.

=== "Windows"
    1. Tekan ++win+r++ untuk membuka Run.
    2. Ketik `cmd` lalu tekan ++enter++.
    3. Terminal emulator (Command Prompt) akan terbuka.

=== "Mac"
    1. Buka **Spotlight** dengan ++cmd+space++.
    2. Ketik `Terminal` lalu tekan ++enter++.

=== "Linux"
    1. Tekan ++ctrl+alt+t++ (umumnya shortcut default).
    2. Atau cari "Terminal" di aplikasi.

---

## Run Your (Maybe) First Command

Sudah buka terminal?
Coba ketik perintah berikut, lalu tekan ++enter++:

```bash
whoami
```

Terminal akan menampilkan username-mu.
Selamat! Kamu baru saja menjalankan perintah shell pertamamu.

---

### What is Prompt?

Sebelum mengetik perintah, kamu pasti melihat baris seperti ini:

```bash
username@computer:~$
```

Itulah adalah **prompt**, tanda bahwa shell siap menerima perintah.

- `username` : Nama user aktif
- `@` : Pemisah user dan nama komputer
- `computer` : Nama komputermu
- `:` : Pemisah nama komputer dan path
- `~` : Direktori saat ini (home directory)
- `$` : Simbol prompt (siap menerima perintah)

!!! note
    Tampilannya bisa berbeda tergantung shell yang digunakan, tapi prinsipnya sama.

---

### Trying Other Command

Sekarang, coba perintah berikut:

```bash
echo Halo
```

Terminal akan menampilkan:
```
Halo
```

Perintah `echo` digunakan untuk menampilkan teks ke layar.

---

## What is Path?

Kamu mungkin melihat simbol `~` di prompt.
Itu adalah **path**, alamat lokasi kamu di dalam komputer.

- **Path**: Lokasi direktori/folder saat ini.
- Di GUI, kamu berpindah folder dengan klik.
  Di CLI, kamu berpindah dengan mengetik perintah dan path.

Saat pertama kali membuka terminal, kamu biasanya berada di **home directory** (dilambangkan dengan `~`).

---

### Absolute vs Relative Path

Ada dua jenis path:

- **Absolute Path**: Alamat lengkap dari root.
    - Windows: `C:\Users\username\some_directory`
    - Linux: `/home/username/some_directory` (atau `~` untuk home)
    - Mac: `/Users/username/some_directory`
- **Relative Path**: Alamat relatif terhadap direktori saat ini.
    - `.` : Direktori saat ini
    - `..` : Direktori induk (parent)
    - Contoh struktur:
        ```
        current_dir/
        ├── file1
        └── dir1/
            ├── file2
            └── dir2/
                └── file3
        ```
    - Jika kamu berada di `dir1`, maka:
        - `file2` ada di `./file2`
        - `file3` ada di `./dir2/file3`
        - `file1` ada di `../file1`

!!! tip
    Di Linux/Mac, path dipisahkan dengan `/`.
    Di Windows, gunakan `\` (kecuali di PowerShell, bisa pakai `/` juga).

---

## Next Step

Sekarang kamu sudah mengenal dasar CLI, terminal, shell, dan path.
Selanjutnya, kita akan belajar **navigasi** di terminal, bagaimana berpindah direktori, melihat isi folder, dan lain-lain.

[Lanjut ke: Navigation](02_navigation.md){ .md-button .md-button--primary }
