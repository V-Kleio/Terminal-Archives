# LOG ENTRY #GIT-03

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Dasar Git

Di bagian ini, kita akan membahas siklus hidup file dalam Git, bagaimana cara mencatat perubahan, dan cara melihat kembali apa yang sudah terjadi.

---

## The Three States of Git

Git membagi status file kamu ke dalam tiga area utama. Memahami ini adalah kunci agar tidak bingung saat file "hilang" atau belum tersimpan.

1.  **Working Directory**: Tempat kamu bekerja (ngoding, edit, hapus file). Perubahan di sini belum disimpan Git secara permanen.
2.  **Staging Area (Index)**: Kamu memilih file mana saja yang **akan** di-commit (snapshot) oleh Git.
3.  **Repository (.git)**: Tempat snapshot (commit) disimpan selamanya.

**Workflow Normal:**
```
[Edit File] -> git add -> [Staging Area] -> git commit -> [Repository]
```

---

## 1. Inisialisasi: `git init`

Langkah pertama membuat repositori baru agar bisa dilacak oleh Git:

```bash
git init
```
Ini akan membuat hidden folder `.git` yang bertugas sebagai *database* semua perubahanmu.

!!! note
    Kamu mungkin membaca istilah *repository* sebelumnya pada modul ini, apa itu? Pada konteks ini, repository adalah nama lain untuk folder (direktori) yang sedang dilacak oleh git. Ketika kamu menggunakan `git init`, kamu mengubah direktori kamu saat ini menjadi git repository.

## 2. Status File: `git status`

Perintah paling penting untuk mengetahui state dari file. Gunakan ini setiap saat.

```bash
git status
```
Outputnya akan memberitahumu file mana yang *Untracked* (belum dikenal Git), *Modified* (diubah tapi belum di-add), atau *Staged* (siap commit).

## 3. Staging Perubahan: `git add`

Memindahkan perubahan dari Working Directory ke Staging Area.

```bash
git add file1.txt       # Menambahkan satu file
git add .               # Menambahkan SEMUA perubahan di folder ini
```

!!! tip "Ignored Files"
    Kadang ada file yang tidak ingin kamu add, seperti file sampah atau rahasia. Kamu bisa mengaturnya menggunakan file khusus bernama `.gitignore`. Lihat caranya di [Gitignore](99_additional.md#mengabaikan-file-dengan-gitignore).

## 4. Menyimpan Snapshot: `git commit`

Merekam apa yang ada di Staging Area menjadi satu *history* permanen.

```bash
git commit -m "Menambahkan fitur login"
```
*Pesan commit (`-m`) wajib diisi agar kamu (dan tim) tahu apa yang berubah di snapshot ini.*

## 5. Melihat Masa Lalu: `git log`

Melihat daftar riwayat snapshot yang pernah kamu buat.

```bash
git log
```
Kamu akan melihat hash (ID unik), author, tanggal, dan pesan commit.

- `git log --oneline`: Versi ringkas, satu baris per commit.
- `q`: Tombol untuk keluar dari tampilan log.

---

## Melihat Perbedaan: `git diff`

Kadang kamu lupa, "Tadi saya ubah baris yang mana ya?".

- **`git diff`**: Membandingkan Working Directory vs Staging Area (apa yang belum di-add).
- **`git diff --staged`**: Membandingkan Staging Area vs Repository (apa yang akan di-commit).

---

## Ringkasan Perintah

| Perintah | Fungsi |
| :--- | :--- |
| `git init` | Mulai melacak folder ini dengan Git |
| `git status` | Cek status file (wajib sering-sering!) |
| `git add .` | Masukkan semua perubahan ke Staging Area |
| `git commit -m "msg"` | Simpan permanen ke Repository |
| `git log` | Lihat riwayat perubahan |

---

## Next Step

Sekarang kamu sudah menguasai siklus dasar Git: ubah, add, commit.
Selanjutnya, kita akan belajar salah satu fitur penting dari Git yang memungkinkan kita bereksperimen tanpa takut merusak kode utama.

[Lanjut ke Branching & Merging](04_branching.md){ .md-button .md-button--primary }
