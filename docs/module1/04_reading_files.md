# LOG ENTRY #CLI-04

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Membaca File

Setelah kamu bisa membuat dan mengelola file, langkah berikutnya adalah membaca isi file langsung dari terminal.
CLI menyediakan beberapa perintah yang sangat berguna untuk melihat isi file teks, baik secara keseluruhan maupun sebagian.

---

## Melihat Isi File: `cat`

Perintah `cat` digunakan untuk menampilkan seluruh isi file ke layar.

```bash
cat nama_file.txt
```

Jika file berukuran kecil, `cat` sangat praktis. Namun untuk file yang sangat panjang, isi file akan langsung memenuhi layar dan bisa sulit untuk dibaca.

---

## Interactive Reading: `less`

Untuk membaca file yang lebih panjang, gunakan perintah `less`.
Perintah ini membuka file dalam mode interaktif, sehingga kamu bisa *scroll* ke atas dan bawah.

```bash
less nama_file.txt
```

Navigasi di `less`:
- Gunakan tombol panah atas/bawah untuk *scroll*.
- Tekan `q` untuk keluar dari `less`.

!!! tip
    Kamu juga bisa mencari kata di dalam `less` dengan mengetik `/<kata>` lalu tekan Enter. `<kata>` adalah kata yang ingin kalian cari.

---

## Melihat Beberapa Baris Awal: `head`

Jika kamu hanya ingin melihat beberapa baris pertama dari file, gunakan perintah `head`.

```bash
head nama_file.txt
```

Secara default, `head` akan menampilkan 10 baris pertama.
Kamu bisa mengatur jumlah baris dengan flag `-n`:

```bash
head -n 20 nama_file.txt
```

---

## Melihat Beberapa Baris Akhir: `tail`

Untuk melihat beberapa baris terakhir dari file, gunakan perintah `tail`.

```bash
tail nama_file.txt
```

Secara default, `tail` juga menampilkan 10 baris terakhir.
Kamu bisa mengatur jumlah baris dengan flag `-n`:

```bash
tail -n 15 nama_file.txt
```

`tail` sangat berguna untuk memantau file log yang terus bertambah.

---

## Membaca Secara Real-Time: `tail -f`

Jika kamu ingin melihat update terbaru pada file secara langsung (misal, file log), gunakan:

```bash
tail -f nama_file.txt
```

Perintah ini akan menampilkan baris-baris baru yang ditambahkan ke file secara real-time.
Tekan ++ctrl+c++ untuk keluar dari mode ini.

---

## Summary

| Perintah         | Fungsi                                      |
|------------------|---------------------------------------------|
| `cat`            | Menampilkan seluruh isi file                |
| `less`           | Membaca file secara interaktif              |
| `head`           | Melihat beberapa baris awal file            |
| `tail`           | Melihat beberapa baris akhir file           |
| `tail -f`        | Memantau perubahan file secara real-time    |

---

## Next Step

Sekarang kamu sudah bisa langsung melihat isi file hanya dengan menggunakan terminal.
Selanjutnya kita akan belajar salah satu kelebihan terminal dibandingkan dengan GUI yaitu **wildcards**.

[Lanjut ke Power of Text](05_text_power.md){ .md-button .md-button--primary }
