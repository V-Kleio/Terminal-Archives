# LOG ENTRY #REMOTE-APPENDIX

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Trunk Based Development

Di materi GitFlow, kita belajar tentang manajemen branch. Kebalikannya adalah **Trunk Based Development**.
Workflow ini sangat populer di perusahaan teknologi modern yang butuh kecepatan tinggi (Speed of Delivery).

-   Semua developer melakukan push langsung ke branch utama (`main` atau `trunk`) sesering mungkin (bisa setiap hari).
-   Wajib memiliki **Automated Testing**. Jika tes gagal, commit ditolak.
-   Kelebihan: Menghindari "Merge Hell" (konflik besar di akhir cycle rilis) dan mempercepat feedback.

---

## Intro to CI/CD

Bagaimana cara memastikan kode yang di-push ke Trunk/Main tidak merusak aplikasi? Jawabannya adalah **CI/CD**.

-   **CI (Continuous Integration)**: Otomatisasi testing. Setiap kali ada push atau Pull Request, server menjalankan script test (Unit Test, Linter).
-   **CD (Continuous Delivery/Deployment)**: Otomatisasi rilis. Jika CI lulus, kode otomatis dideploy ke server staging atau production.

Layanan seperti **GitHub Actions** atau **GitLab CI** menyediakan fitur ini secara gratis untuk public repository.

---

## Dokumen Standar Repository

Selain kode program, repository profesional wajib memiliki dokumen berikut:

### 1. README.md
Dokumentasi utama repository. Berisi penjelasan utama repositori:

-   Penjelasan singkat proyek.
-   Cara instalasi dan penggunaan.
-   Badge status (CI passing, version number).

### 2. LICENSE
Dokumen hukum yang mengatur hak guna kode.

-   **MIT**: Bebas dipakai/diubah siapa saja, cukup sertakan kredit.
-   **GPL**: Jika orang lain memodifikasi atau fork kodemu, kode mereka harus memiliki lisensi GPL juga (Copyleft).
-   **Proprietary**: Tidak boleh dipakai tanpa izin (Biasanya jika tidak ada file LICENSE, ini asumsinya).

### 3. CONTRIBUTING.md
File dokumentasi panduan untuk kontributor luar.

-   Standar penulisan kode (Code Style).
-   Langkah-langkah membuat Pull Request.
-   Cara setup environment lokal.

### 4. CHANGELOG.md
Daftar perubahan di setiap versi rilis. Informasi lebih lanjut di [sini](https://keepachangelog.com/en/1.1.0/)

-   Apa saja fitur baru?
-   Apa bug yang diperbaiki?
-   Apakah ada perubahan yang bikin error (Breaking Changes)?

---

## Semantic Commit Messages

Pernah baca history Git isinya cuma "fix", "fix again", "final fix"?
Gunakan standar **Conventional Commits** agar riwayat perubahanmu mudah dibaca manusia dan mesin (bisa generate Changelog otomatis!).

Format dasar:
`type(scope): description`

### Tipe Commit Umum
-   **feat**: Fitur baru (e.g., `feat: add dark mode toggle`).
-   **fix**: Perbaikan bug (e.g., `fix: crashing on login page`).
-   **docs**: Perubahan dokumentasi atau komentar (e.g., `docs: update copyright year`).
-   **style**: Perubahan format (spasi, titik koma) tanpa ubah logika (e.g., `style: format code with prettier`).
-   **refactor**: Perubahan kode yang bukan fix atau fitur, perubahan struktur (e.g., `refactor: simplify auth logic`).
-   **test**: Menambah atau memperbaiki test module (e.g., `test: add unit test for math module`).
-   **chore**: Tugas lain-lain (e.g., `chore: update dependencies`).
-   **nit**: perubahan kecil (nitpick), tidak signifikan, biasanya dari code review (non-standar) (e.g., `nit: reorder imports for consistency`). Dalam beberapa konvensi, bisa tidak digunakan. Biasanya digantikan oleh `docs`, `style`, atau `chore`.

### Contoh Penerapan
```text
feat(auth): add google oauth login
fix(payment): resolve timeout issue on checkout
docs(readme): add installation guide
```

!!! tip "Bacaan Lanjutan"
    -   [Conventional Commits](https://www.conventionalcommits.org/)
    -   [Karma Commit Style](http://karma-runner.github.io/6.4/dev/git-commit-msg.html)
    -   [How to Write a Git Commit Message](https://cbea.ms/git-commit)
    -   [Semantic Commit Messages](https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716)

---

## Chrome Extension & Tools

Ada banyak tools yang bisa membantu GitHub/GitLab experience kamu:

-   **Octotree / Refined GitHub**: Extension browser untuk navigasi file yang lebih cepat.
-   **GitLens (VS Code)**: Bisa melihat siapa yang edit baris kode tersebut (Blame) langsung di editor.

---

## Project Management Tools

Remote repository modern seperti GitHub dan GitLab tidak hanya tempat menyimpan kode. Mereka juga menyediakan tools manajemen proyek.

### 1. Issues
Tempat melaporkan bug, mendiskusikan fitur baru, atau tanya jawab.

-   Developer bisa assign issue ke orang tertentu.
-   Bisa pakai label (e.g., `bug`, `enhancement`, `wontfix`).
-   Issue bisa ditutup otomatis lewat commit message: `Fixes #12`.

### 2. Projects (Kanban Board)
Kanban Board untuk mengatur tugas (To Do, In Progress, Done). Mirip Trello tapi terintegrasi langsung dengan Issues dan Pull Request.

### 3. Wiki
Tempat menulis dokumentasi panjang yang terpisah dari kode. Cocok untuk panduan teknis yang kompleks.


[Kembali ke Git Remote](01_intro_remote.md){ .md-button .md-button--primary }
