# LOG ENTRY #REMOTE-01

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Apa itu Remote Repository?

Sampai saat ini, repository Git kamu hanya ada di laptopmu sendiri (Local Repository).
Jika laptopmu rusak, kodenya akan hilang. Jika temanmu ingin ikut ngoding di repository yang sama, mereka tidak akan bisa akses.

**Remote Repository** adalah versi repository-mu yang di-host di server (internet atau jaringan lokal).
Dengan remote repository, kamu bisa menyimpan backup kode dan berkolaborasi dengan orang lain.

---

## Layanan Hosting Git Populer

Git adalah alatnya (tool), sedangkan hosting adalah tempat penyimpanannya. Ada banyak layanan hosting Git:

- **GitHub**: Paling populer, punyanya Microsoft.
- **GitLab**: Populer untuk DevOps/CI-CD, bisa di-install di server sendiri.
- **Bitbucket**: Banyak digunakan di lingkungan korporat (bisa integrasi dengan Jira).
- **Azure DevOps**: Dari Microsoft juga.

!!! note
    Panduan di modul ini menggunakan contoh **GitHub**, tapi 95% perintah dan konsepnya (push, pull, clone, remote) berlaku sama persis untuk GitLab, Bitbucket, dll. Akan ada perbedaan sedikit seperti istilah *Pull Request* di GitHub disebut dengan *Merge Request* di GitLab.

---

## Cara Kerja Remote Repository

Biasanya, kamu akan:

1. Membuat repository di layanan seperti GitHub.
2. Menghubungkan repository lokal ke remote repository.
3. Mengirim (push) perubahan dari lokal ke remote.
4. Mengambil (pull/fetch) perubahan dari remote ke lokal.

---

## Next Step

Dengan menggunakan layanan hosting Git, kode kamu bisa ada di cloud sebagai backup.
Repositori Git kamu juga bisa dilihat dan diakses oleh orang lain bahkan orang lain juga bisa memberi kontribusi.
Selanjutnya, kita akan melihat cara untuk menyambungkan Git lokal dengan layanan hosting Git.

[Lanjut ke Autentikasi SSH](02_auth.md){ .md-button .md-button--primary }
