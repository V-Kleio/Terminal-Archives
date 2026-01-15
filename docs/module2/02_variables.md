# LOG ENTRY #SCRIPT-02

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Variabel dalam Bash Scripting

Variabel adalah salah satu konsep paling dasar dalam scripting.
Dengan variabel, kamu bisa menyimpan data sementara, seperti teks, angka, atau hasil dari perintah lain, lalu menggunakannya kembali di dalam script.

---

## Definisi Variabel

Di Bash, kamu bisa membuat variabel tanpa tipe data khusus.
Penulisan variabel tidak menggunakan spasi di sekitar tanda sama dengan (`=`).

!!! tip "Windows Users"
    Sintaks variabel di Windows sangat berbeda. Batch menggunakan `%var%` dan PowerShell menggunakan `$var` (mirip Bash). Lihat [panduan variabel Windows](99_additional.md#windows-scripting-batch-powershell).

```bash
nama="Kleio"
umur=300
```

- `nama` adalah variabel string berisi "Kleio".
- `umur` adalah variabel integer berisi 300 (tetap dianggap string oleh Bash).

Untuk mengakses nilai variabel, gunakan tanda `$` di depan nama variabel:

```bash
echo $nama
echo $umur
```

---

## String Variable

Variabel string bisa berisi teks apa saja.

```bash
pesan="Selamat datang di Terminal Archives!"
echo $pesan
```

Jika string mengandung spasi, gunakan tanda kutip (`"` atau `'`).

### Single vs Double Quotes

Hati-hati, tanda kutip satu (`'`) dan kutip dua (`"`) memiliki perbedaan penting di Bash:

- **Double Quotes (`"`)**: Variabel di dalamnya akan **di-expand**.
- **Single Quotes (`'`)**: Semua karakter di dalamnya dianggap **teks biasa** (literal).

Contoh:

```bash
nama="Kleio"
echo "Halo, $nama"  # Output: Halo, Kleio
echo 'Halo, $nama'  # Output: Halo, $nama
```

---

## Number Variable

Bash memperlakukan semua variabel sebagai string secara default.
Untuk operasi aritmatika, gunakan sintaks khusus:

```bash
a=10
b=5
jumlah=$((a + b))
echo $jumlah
```

Kamu juga bisa menggunakan perintah `let` atau `expr`:

```bash
let hasil=a*b
echo $hasil

# atau
hasil=$(expr $a / $b)
echo $hasil
```

## Command Substitution

Salah satu fitur paling berguna dalam scripting adalah **Command Substitution**.
Ini memungkinkan kamu menyimpan *output* (hasil) dari suatu perintah ke dalam variabel.
Caranya adalah dengan memasukkan perintah ke dalam `$(...)`.

Contoh:

```bash
user_aktif=$(whoami)
tanggal=$(date)
echo "User $user_aktif menjalankan script pada $tanggal"
```

Script di atas akan menjalankan perintah `whoami` dan `date`, lalu menyimpan hasilnya ke variabel `user_aktif` dan `tanggal`.

---

## Environment Variables

*Environment Variables* adalah variabel global yang tersedia untuk semua proses di sistem.
Contoh variabel lingkungan yang umum:

- `HOME` : Direktori home user
- `PATH` : Daftar direktori tempat sistem mencari program
- `USER` : Nama user aktif

Untuk melihat semua *environment variables*:

```bash
printenv
```

Atau untuk melihat nilai variabel tertentu:

```bash
echo $HOME
```

---

## Membuat Environment Variables

Agar variabel yang kamu buat bisa diakses oleh proses lain, gunakan perintah `export`:

```bash
export PROJECT="Terminal Archives"
```

Sekarang variabel `PROJECT` bisa diakses oleh script atau program lain yang dijalankan dari shell tersebut.

---

## Menghapus Environment Variables

Untuk menghapus variabel dari environment shell, gunakan perintah `unset`:

```bash
unset nama
```

---

## Summary

| Konsep         | Fungsi                                      |
|----------------|---------------------------------------------|
| nama="isi"     | Membuat variabel                            |
| $nama          | Mengakses nilai variabel                    |
| export VAR=isi | Membuat variabel lingkungan                 |
| unset VAR      | Menghapus variabel                          |

---

## Next Step

Sekarang kamu sudah bisa membuat variabel di dalam script.
Selanjutnya kita akan belajar tentang user input agar script kita lebih interaktif.

[Lanjut ke User Input](03_user_input.md){ .md-button .md-button--primary }
