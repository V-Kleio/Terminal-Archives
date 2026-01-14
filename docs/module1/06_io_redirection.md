# LOG ENTRY #CLI-06

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## I/O Redirection & Pipes

Salah satu kekuatan utama CLI adalah kemampuannya untuk mengalirkan data dari satu perintah ke perintah lain, atau dari dan ke file.
Konsep ini disebut **I/O Redirection** dan **Pipes**. Dengan fitur ini, kamu bisa menggabungkan perintah, menyimpan output ke file, atau mengambil input dari file dengan sangat fleksibel.

---

## Standard Input, Output, & Error

Setiap perintah di terminal bekerja dengan tiga tipe utama:

- **Standard Input (stdin)**: Tempat perintah menerima data (biasanya dari keyboard).
- **Standard Output (stdout)**: Tempat perintah mengirim hasil (biasanya ke layar).
- **Standard Error (stderr)**: Tempat perintah mengirim pesan error (juga ke layar).

Dengan redirection, kamu bisa mengubah ke mana data ini pergi.

---

## Output Redirection dengan `>` & `>>`

- `>` digunakan untuk **menulis** output ke file (file lama akan ditimpa).
- `>>` digunakan untuk **menambahkan** output ke akhir file (append).

Contoh:

```bash
echo "Halo dunia" > output.txt
```
Menulis "Halo dunia" ke file `output.txt`. Jika file sudah ada, isinya akan diganti.

```bash
ls -l >> daftar.txt
```
Menambahkan hasil `ls -l` ke akhir file `daftar.txt`. Jika file belum ada, akan dibuat.

---

## Input Redirection dengan `<`

Kamu juga bisa mengambil input dari file, bukan dari keyboard.

Contoh:

```bash
sort < daftar.txt
```
Menyortir isi file `daftar.txt` dan menampilkan hasilnya ke layar.

---

## Pipelining dengan Pipe (`|`)

Pipe (`|`) digunakan untuk mengalirkan output dari satu perintah menjadi input untuk perintah berikutnya.
Dengan pipe, kamu bisa membuat *chain of commands* yang sangat powerful.

Contoh:

```bash
cat log.txt | grep error | sort
```
- `cat log.txt` menampilkan isi file.
- Outputnya diteruskan ke `grep error` untuk mencari baris yang mengandung "error".
- Hasilnya diteruskan lagi ke `sort` untuk mengurutkan baris.

Kamu bisa menggabungkan beberapa pipe sekaligus sesuai kebutuhan.

---

## Mengalihkan Error Output

Secara default, pesan error akan tampil di layar.
Kamu bisa mengalihkan error ke file dengan:

```bash
ls folder_tidak_ada 2> error.log
```
Angka `2` menunjukkan **stderr**.
Perintah di atas akan menulis pesan error ke file `error.log`.

Untuk menggabungkan stdout dan stderr ke satu file:

```bash
command > output.log 2>&1
```

---

## Summary

| Operator   | Fungsi                                      |
|------------|---------------------------------------------|
| `>`        | Menulis output ke file (overwrite)          |
| `>>`       | Menambahkan output ke akhir file (append)   |
| `<`        | Mengambil input dari file                   |
| `|`        | Mengalirkan output ke perintah berikutnya   |
| `2>`       | Mengalihkan error ke file                   |
| `>&`       | Menggabungkan output dan error              |

---

## Next Step

Selamat, sekarang kamu sudah cukup menguasai cara menggunakan terminal dengan baik.
Gunakanlah terminal lebih sering agar terbiasa mengetik perintah terminal dan kamu bisa pamer ke temanmu.
Tidak semua perintah dituliskan di sini, tapi kamu bisa menggunakan perintah `help` untuk eksplorasi lebih banyak lagi.

Nah, kalau sudah terbiasa menggunakan terminal, kamu mungkin berpikir bagaimana caranya dengan mudah menjalankan banyak perintah sekaligus.
Atau, kamu mungkin ingin melakukan sesuatu di terminal berulang kali.
Saatnya, kamu belajar **scripting**, yaitu proses otomasi dengan membuat perintah terminal menjadi kode atau rangkaian instruksi yang bisa dieksekusi sekaligus oleh terminal.

!!! note
    Direkomendasikan kalian belajar dulu bahasa pemrograman atau pernah menulis kode sebelumnya.
    Module-module selanjutnya ditulis dengan asumsi kalian familier dengan beberapa konsep pemrograman.
    Module-module setelah ini juga paling relevan digunakan dalam workflow programming.
    Tapi, ini hanyalah rekomendasi. Kalau kalian tetap ingin lanjut membaca, silakan saja.

[Lanjut ke Next Module](../module2/01_intro.md){ .md-button .md-button--primary }
[Appendix](99_additional.md){ .md-button .md-button--primary }
