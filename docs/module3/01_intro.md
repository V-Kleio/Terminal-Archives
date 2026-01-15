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

## Next Step

[Lanjut ke Konfigurasi Git](02_configuration.md){ .md-button .md-button--primary }
