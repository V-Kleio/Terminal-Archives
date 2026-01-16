# LOG ENTRY #GIT-05

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Disaster Recovery: Mengatasi Kesalahan di Git

Terkadang kamu melakukan perubahan yang salah, menghapus file penting, atau commit yang tidak diinginkan.
Untungnya, Git menyediakan berbagai cara untuk memulihkan keadaan dan membatalkan perubahan.

---

## Mengembalikan File: `git restore`

Jika kamu ingin membatalkan perubahan pada file di working directory (sebelum di-commit), gunakan:

```bash
git restore nama_file.txt
```

Perintah ini akan mengembalikan file ke kondisi terakhir di commit terbaru.

Untuk membatalkan perubahan yang sudah di-staging (setelah `git add`):

```bash
git restore --staged nama_file.txt
```

---

## Memperbaiki Kesalahan Kecil: `git commit --amend`

Pernahkah kamu baru saja melakukan commit, lalu sadar ada typo di pesannya? Atau ada file yang lupa di-`add`?
Daripada melakukan reset, kamu bisa memperbaiki commit terakhir tersebut.

1. **Ganti pesan commit**:
    ```bash
    git commit --amend -m "Pesan baru yang benar"
    ```

2. **Menambah file yang ketinggalan**:
    ```bash
    git add file_ketinggalan.txt
    git commit --amend --no-edit
    ```

!!! note
    `--no-edit` artinya menggunakan pesan commit yang lama.

---

## Membatalkan Commit: `git reset`

`git reset` digunakan untuk memindahkan pointer branch ke commit sebelumnya.
Ada beberapa mode reset yang perlu kamu ketahui:

### Soft Reset

```bash
git reset --soft HEAD~1
```

- Mengembalikan commit terakhir, tapi perubahan tetap ada di staging area.
- Cocok jika kamu ingin mengedit ulang commit terakhir.

### Mixed Reset (Default)

```bash
git reset HEAD~1
```

- Membatalkan commit terakhir, perubahan tetap ada di working directory, tapi keluar dari staging area.

### Hard Reset

```bash
git reset --hard HEAD~1
```

- Membatalkan commit terakhir dan menghapus semua perubahan di working directory.

!!! danger
    Hati-hati, perubahan yang belum di-commit akan hilang permanen.

---

## Membatalkan Commit Tanpa Mengubah History: `git revert`

Jika commit sudah terlanjur di-push ke remote atau kamu ingin membatalkan commit tanpa menghapus history, gunakan:

```bash
git revert <hash_commit>
```

- Git akan membuat commit baru yang mengembalikkan perubahan dari commit yang dipilih.
- Aman digunakan di repository bersama (collaborative).

---

## Alias

Jika perintah-perintah di atas terasa terlalu panjang untuk diketik berulang-ulang, kamu bisa membuat shortcut atau **Alias**.
Lihat caranya di [Appendix: Alias Git](99_additional.md#alias-untuk-efisiensi).

---

## Ringkasan

| Perintah                        | Fungsi                                      |
|---------------------------------|---------------------------------------------|
| git restore nama_file           | Mengembalikan file ke commit terakhir       |
| git restore --staged nama_file  | Menghapus file dari staging area            |
| git reset --soft HEAD~1         | Membatalkan commit, perubahan tetap di stage|
| git reset HEAD~1                | Membatalkan commit, perubahan ke working dir|
| git reset --hard HEAD~1         | Membatalkan commit dan perubahan di file    |
| git revert <hash>               | Membuat commit pembalik dari commit tertentu|

---

## Next Step

Sekarang kamu sudah jago dalam mengelola repository lokalmu, mulai dari inisialisasi, branching, hingga memperbaiki kesalahan.
Langkah selanjutnya adalah membawa kodemu ke cloud agar bisa berkolaborasi dengan orang lain.

[Lanjut ke Git Remote](../module4/01_intro_remote.md){ .md-button .md-button--primary }
[Appendix](99_additional.md){ .md-button .md-button--primary }
