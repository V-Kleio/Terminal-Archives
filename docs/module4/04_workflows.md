# LOG ENTRY #REMOTE-04

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Kolaborasi Tim

Di tahap ini, kita akan membahas metode standar bagaimana tim berkolaborasi menggunakan Git.

Istilah yang digunakan di tiap platform mungkin berbeda (GitHub menggunakan **Pull Request**, GitLab menggunakan **Merge Request**), tapi konsepnya sama.

!!! note
    Programmer yang baik adalah programmer yang membuat commit message yang jelas dan dokumentasi kode yang lengkap. Lihat [Appendix](99_additional.md/#dokumen-standar-repository) untuk tips mengenai hal ini.

---

## Feature Branch Workflow

Jangan pernah coding langsung di `main` (atau `master`)!
Gunakan branch untuk setiap fitur atau perbaikan.

1.  **Buat branch baru**:
    ```bash
    git checkout -b fitur-a
    ```
2.  **Ngoding lalu commit**:
    ```bash
    git add .
    git commit -m "Add login page layout"
    ```
3.  **Push ke remote**:
    ```bash
    git push -u origin fitur-a
    ```

---

## Pull Request (PR) / Merge Request (MR)

Setelah kodemu ada di remote repository, jangan langsung merge ke main. Buat Pull Request.

1.  Buka repository di browser.
2.  Kamu akan melihat notifikasi "fitur-a had recent pushes". Klik tombol **Compare & Pull Request**.
3.  Isi judul dan deskripsi (jelaskan apa yang kamu ubah).
4.  Klik **Create Pull Request**.

Sekarang, kodemu sedang di-review. Ketua tim atau temanmu bisa melihat kode tersebut sebelum masuk ke `main`.

### PR dari Fork (Open Source Contribution)

Jika kamu berkontribusi ke repository orang lain melalui **Fork** (seperti proyek Open Source), langkahnya sedikit berbeda karena melibatkan dua repository terpisah.

1.  Buka halaman repository asli (yang kamu fork).
2.  Masuk ke tab **Pull requests** lalu klik **New pull request**.
3.  Klik tulisan **compare across forks**.
4.  Atur arah merge:
    -   **base repository**: Repository asli (Tujuan).
    -   **head repository**: Repository fork milikmu (Sumber).
5.  Pilih branch fiturmu, lalu klik **Create Pull Request**.

---

## 3. Code Review

Di tahap PR/MR, tim akan melakukan **Code Review**.
Mereka bisa memberikan komentar di baris kode tertentu, "Ini bisa dioptimalkan", "Variabel ini typo", dsb.

Jika ada revisi:

1.  Edit kode di komputer lokalmu.
2.  Commit dan Push lagi ke branch yang sama.
    ```bash
    git commit -am "Fix typo"
    git push
    ```
3.  PR/MR di website akan otomatis terupdate!

---

## 4. Merging

Jika semua sudah Approved, tombol **Merge** akan aktif (atau bisa diklik oleh maintainer).
Setelah di-merge:

-   Kode dari `fitur-a` pindah ke `main` di remote.
-   Branch `fitur-a` bisa dihapus.

Di lokalmu, jangan lupa update:

```bash
git checkout main
git pull
git branch -d fitur-a
```

---

## Next Step

Bagaimana jika proyeknya sangat besar dan butuh rilis versi (v1.0, v2.0)? Atau butuh branch khusus untuk development dan production? Mari kita bahas GitFlow.

[Lanjut ke GitFlow](05_gitflow.md){ .md-button .md-button--primary }
