# LOG ENTRY #CLI-03

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Manipulasi File

Setelah memahami cara navigasi di terminal, kini saatnya belajar mengelola file dan folder secara langsung.
Di CLI, kamu bisa membuat, menyalin, memindahkan, dan menghapus file atau folder hanya dengan satu baris perintah.

---

## Membuat File Baru: `touch`

Untuk membuat file kosong baru, gunakan perintah:

```bash
touch nama_file.txt
```

Jika file dengan nama tersebut sudah ada, perintah ini akan memperbarui waktu modifikasinya tanpa mengubah isinya.

Perhatikan bahwa perintah tersebut membuat file dengan akhiran `.txt`.
Akhiran ini disebut sebagai **file extension**.
File extension merupakan penanda jenis suatu file agar komputer atau program dapat mengenal format file dengan mudah dan dapat mengintepretasikan file tersebut dengan tepat.
Beberapa contoh file extension:

- `.txt`: File plain text, format file berisi teks paling sederhana.
- `.docx`: Format file yang digunakan untuk menyimpan dokumen MS Word.
- `.png`, `.jpg`: Format file untuk gambar.
- `.mp3`, `.wav`: Format file untuk audio.
- `.mp4`: Format file untuk video.
- `.c`, `.java`, `.rs`: Format file untuk beberapa kode bahasa pemrograman.

Informasi lebih lanjut bisa lihat di [sini](https://www.geeksforgeeks.org/techtips/list-of-file-formats/).

---

## Membuat Folder Baru: `mkdir`

Untuk membuat folder (direktori) baru, gunakan:

```bash
mkdir nama_folder
```

Kamu juga bisa membuat beberapa folder sekaligus:

```bash
mkdir folder1 folder2 folder3
```

Untuk membuat folder beserta subfolder sekaligus, gunakan flag `-p`:

```bash
mkdir -p parent/child/grandchild
```

---

## Menyalin File & Folder: `cp`

Untuk menyalin file, gunakan:

```bash
cp sumber.txt tujuan.txt
```

Ini akan membuat salinan `sumber.txt` dengan nama `tujuan.txt`.

Untuk menyalin file ke folder lain:

```bash
cp file.txt folder_tujuan/
```

Untuk menyalin folder beserta isinya, gunakan flag `-r` (recursive):

```bash
cp -r folder_sumber/ folder_tujuan/
```

---

## Memindahkan/Mengganti Nama File & Folder: `mv`

Perintah `mv` digunakan untuk memindahkan file atau folder, atau mengganti namanya.

Memindahkan file ke folder lain:

```bash
mv file.txt folder_tujuan/
```

Mengganti nama file:

```bash
mv lama.txt baru.txt
```

Kamu juga bisa memindahkan beberapa file sekaligus:

```bash
mv file1.txt file2.txt folder_tujuan/
```

---

## Menghapus File & Folder: `rm`

Untuk menghapus file, gunakan:

```bash
rm nama_file.txt
```

Untuk menghapus beberapa file sekaligus:

```bash
rm file1.txt file2.txt
```

Untuk menghapus folder beserta seluruh isinya, gunakan flag `-r`:

```bash
rm -r nama_folder
```

!!! danger
    **Hati-hati dengan `rm -rf`!**
    Perintah `rm -rf` akan menghapus folder dan seluruh isinya secara paksa tanpa konfirmasi.
    Jika salah mengetik path, kamu bisa kehilangan banyak data.
    Selalu cek kembali path yang kamu tulis sebelum menekan Enter.

---

## Menghapus dengan Aman

- Gunakan flag `-i` pada `rm` untuk meminta konfirmasi sebelum menghapus:
    ```bash
    rm -i file.txt
    ```
- Untuk folder:
    ```bash
    rm -ri nama_folder
    ```
- Selalu cek lokasi dengan `pwd` sebelum menjalankan perintah hapus.

---

## Summary

| Perintah         | Fungsi                                 |
|------------------|----------------------------------------|
| `touch`          | Membuat file kosong baru               |
| `mkdir`          | Membuat folder baru                    |
| `cp`             | Menyalin file atau folder              |
| `mv`             | Memindahkan atau mengganti nama        |
| `rm`             | Menghapus file atau folder             |

---

## Next Step

Sekarang kamu sudah memahami cara mengelola file dan folder di terminal.
Selanjutnya kita akan belajar cara untuk melihat isi file melalui terminal.

[Lanjut ke Reading Files](04_reading_files.md){ .md-button .md-button--primary }
