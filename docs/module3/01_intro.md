# LOG ENTRY #GIT-01

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Konsep Git

Ketika kamu bekerja dengan file, terutama dalam pengembangan perangkat lunak, perubahan dan revisi adalah hal yang tidak terhindarkan.
Bagaimana jika kamu ingin kembali ke versi sebelumnya? Bagaimana jika kamu ingin tahu siapa yang mengubah apa, dan kapan?
Di sinilah **Version Control System (VCS)** seperti Git menjadi sangat penting.

---

## Kenapa Menggunakan Version Control System?

Tanpa Version Control System, biasanya orang menyimpan banyak salinan file dengan nama berbeda:

```
laporan_final.docx
laporan_final_revisi2.docx
laporan_final_fix_beneran.docx
```

Dengan Version Control System, kamu bisa:

- Melacak setiap perubahan yang terjadi pada file.
- Kembali ke versi sebelumnya kapan saja.
- Melihat siapa yang melakukan perubahan dan kapan.
- Bekerja sama dalam tim tanpa takut file tertimpa.

---

## Snapshots vs Saving

Perbedaan utama antara menyimpan file biasa dan menggunakan Git adalah konsep **snapshot**.

- **Saving**: Hanya menyimpan keadaan file saat ini, menimpa versi sebelumnya.
- **Snapshot**: Git menyimpan keadaan seluruh file setiap kali kamu melakukan commit (membuat snapshot).
  Setiap snapshot bisa diakses kembali kapan saja, tanpa kehilangan versi sebelumnya.

---

## Workflow Dasar

1. **Inisialisasi repository**: Membuat folder proyek menjadi repository Git.
2. **Menambahkan perubahan**: Memilih file yang ingin disimpan perubahannya (staging).
3. **Commit**: Menyimpan snapshot perubahan ke dalam history.
4. **Melihat riwayat**: Mengecek daftar commit yang pernah dibuat.
5. **Kembali ke versi sebelumnya**: Checkout atau reset ke commit tertentu.

---

## Instalasi Git

Sebelum mulai, kamu harus menginstall Git di komputer lokalmu.

### Windows (Wajib Baca!)
Pengguna Windows **SANGAT DISARANKAN** untuk menginstall **Git Bash**.
Modul-modul sebelumnya (Terminal & Scripting) menggunakan sintaks Bash (Linux). Dengan Git Bash, kamu mendapatkan terminal yang mendukung perintah-perintah Linux tersebut di Windows.

1.  Download **Git for Windows** di [git-scm.com](https://git-scm.com/download/win).
2.  Jalankan installer.
3.  Saat instalasi, pastikan opsi **Git Bash Here** terpilih.
4.  Setelah selesai, buka aplikasi **Git Bash** untuk menggunakan terminal bash.
    Ini akan mengatasi isu kompatibilitas perintah terminal di Windows.

### Linux (Debian/Ubuntu)
Buka terminal dan jalankan:
```bash
sudo apt update
sudo apt install git
```

### macOS
Jika kamu sudah menginstall Xcode atau Homebrew:
```bash
brew install git
```

Cek versi untuk memastikan instalasi berhasil:
```bash
git --version
```

---

## Next Step

Git sangatlah berguna karena kita bisa membuat banyak versi dari proyek kita dengan snapshot.
Kita juga bisa berpindah versi perubahan dengan mudah.
Hal inilah yang mungkin terkesan seperti *time-travel* karena kita bisa saja kembali ke keadaan snapshot folder sebelumnya.
Git juga menyimpan seluruh file dalam repositori git (tidak hanya satu file)

Selanjutnya ayo kita coba gunakan Git!

[Lanjut ke Konfigurasi Git](02_configuration.md){ .md-button .md-button--primary }
