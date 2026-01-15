# LOG ENTRY #GIT-04

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Branching

Salah satu fitur terkuat di Git adalah **branching**.
Dengan branch, kamu bisa bereksperimen, mengembangkan fitur baru, atau memperbaiki bug tanpa mengganggu kode utama.
Branching membuat kolaborasi dan pengembangan proyek jadi lebih aman dan terstruktur.

---

## Kenapa Perlu Branch?

Tanpa branch, semua perubahan langsung terjadi di branch utama (biasanya `main` atau `master`).
Jika ada kesalahan, kode utama bisa rusak.
Dengan branch, kamu bisa:

- Mengembangkan fitur baru tanpa mengganggu kode utama.
- Memperbaiki bug secara terpisah.
- Menguji ide atau eksperimen.
- Bekerja paralel dengan tim.

!!! tip "Work in Progress?"
    Jika kamu harus pindah branch tapi pekerjaanmu belum selesai (belum siap commit), jangan khawatir. Kamu bisa menggunakan fitur `git stash` untuk menyimpan pekerjaanmu sementara. Cek caranya di [Git Stash](99_additional.md#menyimpan-sementara-dengan-git-stash).

---

## Membuat dan Melihat Branch: `git branch`

Untuk melihat daftar branch yang ada di repository:

```bash
git branch
```

Branch aktif akan ditandai dengan tanda `*`.

Untuk membuat branch baru:

```bash
git branch nama_branch
```

Branch baru ini adalah salinan dari commit saat ini.

---

## Berpindah Branch: `git checkout` dan `git switch`

Untuk berpindah ke branch lain, gunakan:

```bash
git checkout nama_branch
```

Atau dengan perintah yang lebih baru dan lebih mudah:

```bash
git switch nama_branch
```

Jika ingin membuat dan langsung berpindah ke branch baru:

```bash
git checkout -b fitur-baru
# atau
git switch -c fitur-baru
```

!!! note
    Kenapa ada dua jenis perintah? Perintah `checkout` merupakan perintah lama di Git yang tidak hanya dipakai untuk branching. Karena fungsinya banyak, perintah ini menjadi membingungkan dan terkadang jadi salah pakai. Perintah `switch` baru ada sekitar tahun 2019 dan **hanya khusus** untuk mengelola branch. Perintah ini ada untuk menghindari kebingungan dan kesalahan yang terjadi akibat perintah `checkout`.

---

## Menggabungkan Branch: `git merge`

Setelah selesai bekerja di branch, kamu bisa menggabungkan perubahan ke branch utama (misal `main`):

1. Pindah dulu ke branch utama:

    ```bash
    git checkout main
    # atau
    git switch main
    ```

2. Lakukan merge:

    ```bash
    git merge nama_branch
    ```

---

## Merge Conflict

Terkadang, Git tidak bisa menggabungkan branch secara otomatis. Ini terjadi jika baris yang sama di file yang sama diubah di kedua branch. Ini disebut **Merge Conflict**.

Jangan panik! Git akan memberitahumu file mana yang konflik. Buka file tersebut, dan kamu akan melihat penanda seperti ini:

```
<<<<<<< HEAD
Ini kode di branch main
=======
Ini kode di branch fitur
>>>>>>> fitur
```

**Cara mengatasi:**

1.  Hapus penanda (`<<<<`, `====`, `>>>>`).
2.  Pilih kode mana yang benar (atau gabungkan keduanya).
3.  Simpan file.
4.  Lakukan `git add` dan `git commit` lagi.

---

## Menghapus Branch

Setelah branch selesai dan sudah digabung, kamu bisa menghapusnya:

```bash
git branch -d nama_branch
```

---

## Ringkasan

| Perintah                    | Fungsi                                      |
|-----------------------------|---------------------------------------------|
| git branch                  | Melihat/membuat branch                      |
| git switch -c nama          | Membuat & pindah ke branch baru             |
| git merge nama              | Menggabungkan branch ke posisi sekarang     |
| git branch -d               | Menghapus branch                            |


---

## Next Step

Selamat, kamu sudah tahu cara memisahkan fitur dan menggabungkannya kembali! Namun, bagaimana jika kita melakukan kesalahan fatal seperti menghapus file atau salah commit?

[Lanjut ke Disaster Recovery](05_recovery.md){ .md-button .md-button--primary }
