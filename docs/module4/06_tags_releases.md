# LOG ENTRY #REMOTE-06

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Tags & Releases: Menandai Sejarah

Branch itu bergerak (pointer-nya pindah setiap commit baru). Tapi **Tag** itu diam.
Tag digunakan untuk menandai titik spesifik dalam sejarah commit sebagai "Penting", biasanya untuk penomoran versi (Version Control).

---

## 1. Membuat Tag

Ada dua jenis tag: Lightweight dan Annotated. Gunakan **Annotated Tag** untuk rilis karena menyimpan info pembuat dan tanggal.

```bash
git tag -a v1.0 -m "Versi 1.0 - Rilis Pertama"
```
- `-a`: Annotated.
- `-m`: Pesan tag.

Untuk melihat daftar tag:
```bash
git tag
```

## 2. Push Tag ke Remote

`git push` biasa TIDAK mengirim tag. Kamu harus kirim manual.

```bash
git push origin v1.0
```
Atau kirim semua tag sekaligus:
```bash
git push origin --tags
```

---

## 3. Releases di GitHub/GitLab

Setelah tag di-push, remote repository (GitHub/GitLab) biasanya akan mengenalinya.
Kamu bisa mengubah Tag menjadi **Release** di menu GitHub.

Release di GitHub memungkinkan kamu melampirkan file binary (misal `.exe` atau `.zip` aplikasi) agar user bisa mendownload program jadinya, bukan hanya source code-nya.

---

## Semantic Versioning (SemVer)

Format penomoran versi yang standar: **MAJOR.MINOR.PATCH** (contoh: v2.1.4).

-   **MAJOR**: Perubahan besar yang tidak kompatibel dengan versi sebelumnya (Breaking changes).
-   **MINOR**: Fitur baru (backward compatible).
-   **PATCH**: Perbaikan bug (backward compatible).

---

## Next Step

Materi inti Remote Repository selesai! Lihat appendix untuk manajemen proyek (Issues & Wiki).

[Lihat Appendix](99_additional.md){ .md-button .md-button--primary }
