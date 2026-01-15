# LOG ENTRY #REMOTE-04

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## The Workflow: Kolaborasi Tim

Tidak ada insinyur yang bekerja sendirian selamanya. Di tahap ini, kita akan membahas "Workflow"—metode standar bagaimana tim berkolaborasi menggunakan Git.

Istilah yang digunakan di tiap platform mungkin berbeda (GitHub menggunakan **Pull Request**, GitLab menggunakan **Merge Request**), tapi konsepnya sama.

---

## 1. Feature Branch Workflow

Jangan pernah coding langsung di `main` (atau `master`)! Itu adalah aturan emas.
Gunakan branch untuk setiap fitur atau perbaikan.

1.  **Buat branch baru**:
    ```bash
    git checkout -b fitur-login
    ```
2.  **Kerjakan coding, commit**:
    ```bash
    git add .
    git commit -m "Add login page layout"
    ```
3.  **Push ke remote**:
    ```bash
    git push -u origin fitur-login
    ```

---

## 2. Pull Request (PR) / Merge Request (MR)

Setelah kodemu ada di remote repository, jangan langsung merge ke main. Ajukan permintaan penggabungan.

-   **GitHub**: Disebut **Pull Request (PR)**.
-   **GitLab**: Disebut **Merge Request (MR)**.

Cara kerjanya:
1.  Buka repository di browser.
2.  Kamu akan melihat notifikasi "fitur-login had recent pushes". Klik tombol **Compare & Pull Request**.
3.  Isi judul dan deskripsi (jelaskan apa yang kamu ubah).
4.  Klik **Create Pull Request**.

Sekarang, kodemu sedang dalam mode "Diskusi". Pemimpin tim atau temanmu bisa melihat kode tersebut sebelum masuk ke `main`.

---

## 3. Code Review

Di tahap PR/MR, tim akan melakukan **Code Review**.
Mereka bisa memberikan komentar di baris kode tertentu. "Ini bisa dioptimalkan", "Variabel ini typo", dsb.

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

Jika semua sudah oke (Approved), tombol **Merge** akan menyala (atau bisa diklik oleh maintainer).
Setelah di-merge:
-   Kode dari `fitur-login` pindah ke `main` di remote.
-   Branch `fitur-login` bisa dihapus.

Di lokalmu, jangan lupa update:
```bash
git checkout main
git pull
git branch -d fitur-login
```

---

## Next Step

Bagaimana jika proyeknya sangat besar dan butuh rilis versi (v1.0, v2.0)? Atau butuh branch khusus untuk development dan production? Mari kita bahas GitFlow.

[Lanjut ke GitFlow](05_gitflow.md){ .md-button .md-button--primary }
