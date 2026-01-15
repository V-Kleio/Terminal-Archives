# LOG ENTRY #REMOTE-01

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Apa itu Remote Repository?

Sampai sejauh ini, repository Git kamu hanya hidup di laptopmu sendiri (Local Repository).
Jika laptopmu rusak, kodenya hilang. Jika temanmu ingin membantu koding, mereka tidak bisa akses.

**Remote Repository** adalah versi repository-mu yang di-host di server (internet atau jaringan lokal).
Dengan remote repository, kamu bisa menyimpan backup kode dan berkolaborasi dengan orang lain.

---

## Layanan Hosting Git Populer

Git adalah alatnya (tool), sedangkan hosting adalah tempat penyimpanannya. Ada banyak layanan hosting Git:

- **GitHub**: Paling populer, dimiliki Microsoft. Istilah khas: *Pull Request*.
- **GitLab**: Populer untuk DevOps/CI-CD, bisa di-install di server sendiri. Istilah khas: *Merge Request*.
- **Bitbucket**: Populer di lingkungan korporat (integrasi Jira).
- **Azure DevOps**: Solusi enterprise dari Microsoft.

!!! note "Konsep Universal"
    Panduan di modul ini menggunakan contoh **GitHub**, tapi 95% perintah dan konsepnya (push, pull, clone, remote) berlaku sama persis untuk GitLab, Bitbucket, dll.

---

## Cara Kerja Remote Repository

Biasanya, kamu akan:

1. Membuat repository di layanan seperti GitHub.
2. Menghubungkan repository lokal ke remote repository.
3. Mengirim (push) perubahan dari lokal ke remote.
4. Mengambil (pull/fetch) perubahan dari remote ke lokal.

---

## Next Step

[Lanjut ke Autentikasi SSH](02_auth.md){ .md-button .md-button--primary }
