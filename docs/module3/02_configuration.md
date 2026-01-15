# LOG ENTRY #GIT-02

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Konfigurasi Git

Sebelum mulai menggunakan Git, kamu perlu mendaftar di Git.
Git mencatat siapa yang membuat setiap perubahan, sehingga penting untuk mengatur nama dan email dengan benar.

---

## Konfigurasi Username dan Email

Setiap commit di Git selalu menyimpan informasi nama dan email pembuatnya.
Untuk mengatur identitas ini, gunakan perintah `git config`.

### Username

```bash
git config --global user.name "Namamu"
```

Gantilah `"Namamu"` dengan nama asli atau nama yang ingin kamu tampilkan di riwayat commit.

### Email

```bash
git config --global user.email "email@example.com"
```

Gantilah `"email@example.com"` dengan email yang kamu gunakan untuk GitHub atau layanan Git remote lainnya.

---

## Global vs Local Configuration

- `--global` akan mengatur konfigurasi untuk semua repository di komputer ini.
- Jika ingin mengatur nama/email hanya untuk satu repository, hilangkan `--global` dan jalankan perintah di dalam folder repository tersebut.

Contoh konfigurasi lokal:

```bash
git config user.name "Nama Proyek"
git config user.email "proyek@example.com"
```

---

## Mengecek Current Configuration

Untuk mengecek konfigurasi yang sudah diatur, gunakan:

```bash
git config --list
```

Atau untuk melihat nilai tertentu:

```bash
git config user.name
git config user.email
```

---

## Konfigurasi Lain

- `git config --global core.editor "vim"`
  Mengatur editor teks default untuk Git (bisa diganti dengan `nano`, `code`, dll).
- `git config --global color.ui auto`
  Mengaktifkan warna pada output Git agar lebih mudah dibaca.

---

## Next Step

Jika kamu sudah meng-install dan melakukan konfigurasi Git, selanjutnya kita akan belajar tentang dasar-dasar git.

[Lanjut ke Git Basic](03_git_basics.md){ .md-button .md-button--primary }
