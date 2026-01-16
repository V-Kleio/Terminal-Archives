# LOG ENTRY #GIT-APPENDIX

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Menyimpan Sementara dengan `git stash`

Bayangkan kamu sedang asyik ngoding di branch `feature-a`, tiba-tiba ada bug urgent di `main` yang harus segera diperbaiki. Tapi, kodemu di `feature-a` belum selesai dan belum siap di-commit.
Jangan panik, gunakan `git stash`.

Fitur ini akan menyembunyikan perubahanmu sementara waktu agar working directory-mu bersih kembali.

- **Simpan perubahan sementara**:
    ```bash
    git stash
    ```
- **Ambil kembali perubahan**:
    ```bash
    git stash pop
    ```
- **Lihat daftar stash**:
    ```bash
    git stash list
    ```

---

## Mengabaikan File dengan `.gitignore`

Tidak semua file perlu dimasukkan ke Git. File seperti hasil build (`.exe`, `dist/`), folder dependensi (`node_modules/`), atau file konfigurasi rahasia (`.env`) sebaiknya diabaikan.

Caranya mudah, buat file bernama `.gitignore` di root repository, lalu tulis nama file/folder yang ingin diabaikan.

Contoh isi `.gitignore`:
```
# Abaikan folder node_modules
node_modules/

# Abaikan semua file .log
*.log

# Abaikan file rahasia
.env
```

!!! tip
    Selalu buat `.gitignore` di awal proyek agar repository tetap bersih dari file sampah.

---

## Alias untuk Efisiensi

Capek mengetik `git status` atau `git checkout` terus-menerus? Kamu bisa membuat singkatan (alias).

```bash
git config --global alias.s status
git config --global alias.co checkout
git config --global alias.br branch
```

Sekarang kamu cukup mengetik `git s`, `git co`, atau `git br`.

---

## Memahami `HEAD` dan "Detached HEAD"

Kamu mungkin sering melihat kata `HEAD` di terminal.
**HEAD** adalah pointer (penunjuk) yang menandakan "posisi kamu sekarang". Biasanya, HEAD menunjuk ke **Branch** (misal `main`).

Namun, jika kamu melakukan `checkout` langsung ke nomor commit (hash), misal `git checkout a1b2c3d`, kamu akan masuk ke mode **Detached HEAD**.

Artinya kamu sedang melihat keadaan commit masa lalu dan kamu bisa melakukan eksperimen di saat itu.

**PENTING**: Jika kamu membuat commit di sini, lalu pindah kembali ke `main`, commit tersebut akan **HILANG** (karena tidak terikat ke branch manapun). Jika ingin menyimpan perubahan di mode ini, buatlah branch baru: `git switch -c branch-eksperimen`.
Jika hanya ingin melihat-lihat, cukup kembali ke masa kini dengan: `git switch main`.

---

## Memilih Commit Spesifik dengan `cherry-pick`

Terkadang kamu tidak ingin menggabungkan (merge) seluruh branch, melainkan hanya ingin mengambil **satu commit tertentu** dari branch lain.

Misalnya, kamu punya branch `fitur-a` dan `fitur-b`. Ada perbaikan bug penting di `fitur-a` (commit hash: `a1b2c3d`) yang juga dibutuhkan di `fitur-b`, tapi kamu belum mau merge semuanya.

Caranya:

1. Pindah ke branch tujuan (`fitur-b`).
2. Jalankan perintah:
   ```bash
   git cherry-pick a1b2c3d
   ```
Git akan mengambil perubahan dari commit tersebut dan menempelkannya di branch kamu saat ini.

---

## Merapikan History dengan `rebase`

Selain `merge`, ada cara lain untuk menggabungkan perubahan, yaitu `rebase`.
Bedanya:

- **Merge**: Membuat history yang bertemu di satu titik (merge commit). Aman tapi bisa berantakan.
- **Rebase**: Memindahkan titik dasar branch kamu ke ujung branch lain.

History-mu akan terlihat lurus dan rapi seolah-olah semua dikerjakan berurutan tanpa branching.

```bash
# Pastikan kamu di branch fitur
git checkout fitur

# Rebase ke main
git rebase main
```

!!! danger "Peraturan Utama Rebase"
    **JANGAN PERNAH** melakukan rebase pada branch publik (branch yang dipakai bersama tim) yang sudah di-push ke remote. Rebase mengubah history, dan ini bisa membuat teman timmu menderita konflik yang parah. Gunakan rebase hanya untuk merapikan branch lokalmu sendiri sebelum di-merge.

[Kembali ke Git](01_intro.md){ .md-button .md-button--primary }
[Lanjut ke Git Remote](../module4/01_intro_remote.md){ .md-button .md-button--primary }
