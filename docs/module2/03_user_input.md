# LOG ENTRY #SCRIPT-03

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## User Input

Script yang interaktif membutuhkan input dari pengguna.
Dengan mengambil input, script bisa menyesuaikan terhadap kebutuhan pengguna.

---

## Membaca Input: `read`

Perintah `read` digunakan untuk mengambil input dari keyboard dan menyimpannya ke dalam variabel.

!!! tip "Windows Users"
    Di Windows, Batch menggunakan `set /p` dan PowerShell menggunakan `Read-Host`. Lihat [contoh input di Windows](99_additional.md#windows-scripting-batch-powershell).

Contoh:

```bash
echo "Siapa namamu?"
read nama
echo "Halo, $nama!"
```

- `read nama` akan menunggu user mengetik sesuatu, lalu menyimpan hasilnya ke variabel `nama`.

Kamu juga bisa membaca beberapa input sekaligus:

```bash
echo "Masukkan nama depan dan belakang:"
read depan belakang
echo "Nama lengkapmu: $depan $belakang"
```

Untuk input seperti password, kamu bisa menggunakan flag `-s` agar input tidak tampil di layar:

```bash
read -s password
```

---

## Script Argument: `$1`, `$2`, ...

Selain input interaktif, script juga bisa menerima argumen saat dijalankan.
Argumen ini ditulis setelah nama script di terminal.

Contoh script `halo.sh`:

```bash
#!/bin/bash
echo "Halo, $1!"
```

Jalankan dengan:

```bash
./halo.sh Kleio
```

Output:

```
Halo, Kleio!
```

- `$1` adalah argumen pertama.
- `$2` adalah argumen kedua,
- dan seterusnya.

Kamu bisa menggunakan beberapa argumen sekaligus:

```bash
#!/bin/bash
echo "Nama depan: $1"
echo "Nama belakang: $2"
```

Gunakan variabel khusus untuk mengetahui jumlah argumen:

- `$#` : Jumlah argumen yang diberikan
- `$@` : Semua argumen sebagai list

Contoh:

```bash
echo "Jumlah argumen: $#"
echo "Semua argumen: $@"
```

---

## Summary

| Konsep      | Fungsi                                      |
|-------------|---------------------------------------------|
| read var    | Membaca input dari user                     |
| read -s var | Membaca input tanpa menampilkan ke layar    |
| $1, $2, ... | Mengakses argumen saat menjalankan script |
| $#          | Jumlah argumen                              |
| $@          | Semua argumen                               |

---

## Next Step

Sekarang kamu sudah tahu cara membaca input user.
Selanjutnya kita akan melihat salah satu konsep pemrograman, yaitu `if statement`, dalam scripting.

[Lanjut ke Flow Control](04_flow_control.md){ .md-button .md-button--primary }
