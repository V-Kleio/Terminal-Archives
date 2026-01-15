# LOG ENTRY #SCRIPT-07

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Exit Codes

Setiap perintah atau *script* di terminal akan menghasilkan **exit code** setelah dijalankan.
Exit code adalah angka yang menunjukkan apakah perintah berhasil atau gagal.

---

## Exit Code 0 dan 1

- **0** berarti perintah berhasil dijalankan tanpa error.
- **1** (atau angka selain 0) berarti terjadi error atau perintah gagal.

!!! tip "Windows Users"
    Konsep Exit Code sama saja di Windows, namun cara mengeceknya berbeda (`%ERRORLEVEL%` di Batch, `$LastExitCode` di PowerShell). Lihat [Exit Code Windows](99_additional.md#windows-scripting-batch-powershell).

Kamu bisa melihat exit code terakhir dengan perintah:

```bash
echo $?
```

Contoh:

```bash
ls ada_file.txt
echo $?   # Biasanya 0 jika file ada

ls file_tidak_ada.txt
echo $?   # Biasanya 1 jika file tidak ada
```

---

## Exit Code in Script

Kamu bisa menentukan exit code sendiri di dalam *script* dengan perintah `exit`:

```bash
if [ -z "$1" ]; then
    echo "Argumen tidak boleh kosong"
    exit 1
fi

echo "Argumen: $1"
exit 0
```

---

## Chaining Commands: `&&` & `||`

Kamu bisa menggabungkan beberapa perintah dalam satu baris, dan menjalankan perintah berikutnya hanya jika perintah sebelumnya berhasil atau gagal.

- `&&` : Perintah setelah `&&` hanya dijalankan jika perintah sebelumnya **berhasil** (exit code 0).
- `||` : Perintah setelah `||` hanya dijalankan jika perintah sebelumnya **gagal** (exit code bukan 0).

Contoh:

```bash
mkdir data && echo "Folder berhasil dibuat"
```
Jika `mkdir data` berhasil, maka pesan akan ditampilkan.

```bash
ls file_tidak_ada.txt || echo "File tidak ditemukan"
```
Jika file tidak ada, maka pesan akan ditampilkan.

Kamu juga bisa menggabungkan keduanya:

```bash
cp file1.txt backup/ && echo "Berhasil" || echo "Gagal"
```

Sesuatu yang aneh mungkin saja terjadi jika perintah kedua (`echo "Berhasil"`) gagal (hampir tidak pernah terjadi), maka perintah setelah `||` juga akan dijalankan.
Situasi ini menyebabkan *weird behaviour*, perintah `cp` berhasil namun terminal melakukan `echo` "Gagal".

---

## Exit Code in Function

Fungsi di Bash juga mengembalikan exit code dari perintah terakhir yang dijalankan di dalam fungsi.
Kamu bisa menggunakan `return` untuk mengatur exit code fungsi:

```bash
cek_file() {
    if [ -f "$1" ]; then
        return 0
    else
        return 1
    fi
}

cek_file data.txt && echo "File ada" || echo "File tidak ada"
```

---

## Summary

| Konsep      | Fungsi                                      |
|-------------|---------------------------------------------|
| $?          | Melihat exit code perintah terakhir         |
| exit N      | Mengatur exit code di *script*              |
| &&          | Jalankan perintah berikutnya jika sukses    |
| \|\|        | Jalankan perintah berikutnya jika gagal     |

---

## Next Step

Selamat, kamu sudah memahami dasar dari scripting.
Kamu sekarang sudah bisa membuat *script* untuk membuat perintah terminal yang lebih kompleks atau secara otomatis menjalankan perintah terminal.

Sekarang, saatnya kita belajar tentang Git, sebuah program untuk mengelola perubahan file.

[Lanjut ke Git](../module3/01_intro.md){ .md-button .md-button--primary }
[Appendix](99_additional.md){ .md-button .md-button--primary }
