# LOG ENTRY #SCRIPT-04

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Flow Control

Agar *script* bisa mengambil keputusan, kamu perlu memahami konsep **flow control**.
Dengan flow control, *script* bisa menjalankan perintah yang berbeda tergantung kondisi tertentu.

---

## Struktur Dasar: `if`, `else`, `elif`

Struktur `if` digunakan untuk menjalankan perintah jika suatu kondisi terpenuhi.

!!! tip "Windows Users"
    Logika `IF` di Windows (Batch/PowerShell) memiliki sintaks yang berbeda, terutama pada operator perbandingannya. Lihat [Flow Control Windows](99_additional.md#windows-scripting-batch-powershell).

```bash
if [ kondisi ]
then
    # perintah jika kondisi benar
fi
```

Kamu bisa menambahkan `else` untuk menangani kondisi sebaliknya:

```bash
if [ kondisi ]
then
    # perintah jika kondisi benar
else
    # perintah jika kondisi salah
fi
```

Untuk lebih dari dua kondisi, gunakan `elif` (else if):

```bash
if [ kondisi1 ]
then
    # perintah jika kondisi1 benar
elif [ kondisi2 ]
then
    # perintah jika kondisi2 benar
else
    # perintah jika semua kondisi salah
fi
```

---

## Test Operators

Di dalam tanda kurung siku `[ ... ]`, kamu bisa menggunakan berbagai operator untuk melakukan pengecekan.

### Number Operator

- `-eq` : sama dengan (equal)
- `-ne` : tidak sama dengan (not equal)
- `-lt` : kurang dari (less than)
- `-le` : kurang dari atau sama dengan (less or equal)
- `-gt` : lebih dari (greater than)
- `-ge` : lebih dari atau sama dengan (greater or equal)

Contoh:

```bash
a=5
b=10
if [ $a -lt $b ]
then
    echo "$a lebih kecil dari $b"
fi
```

### String Operator

- `=`   : string sama
- `!=`  : string tidak sama
- `-z`  : string kosong
- `-n`  : string tidak kosong

Contoh:

```bash
nama=""
if [ -z "$nama" ]
then
    echo "Nama masih kosong"
fi
```

### File Operator

- `-f file` : file ada dan merupakan file biasa
- `-d dir`  : direktori ada
- `-e file` : file atau direktori ada

Contoh:

```bash
if [ -f "data.txt" ]
then
    echo "File data.txt ditemukan"
else
    echo "File data.txt tidak ada"
fi
```

---

## Contoh

```bash
#!/bin/bash

echo "Masukkan angka:"
read angka

if [ $angka -eq 67 ]
then
    echo "Angka rahasia ditebak!"
elif [ $angka -gt 67 ]
then
    echo "Terlalu besar."
else
    echo "Terlalu kecil."
fi
```

---

## Summary

| Operator   | Fungsi                        |
|------------|------------------------------|
| -eq        | Sama dengan (angka)          |
| -ne        | Tidak sama dengan (angka)    |
| -lt        | Kurang dari (angka)          |
| -le        | Kurang dari/sama dengan      |
| -gt        | Lebih dari (angka)           |
| -ge        | Lebih dari/sama dengan       |
| =, !=      | String sama/tidak sama       |
| -z, -n     | String kosong/tidak kosong   |
| -f, -d, -e | File/dir ada                 |

---

## Next Step

Sekarang kamu sudah tahu cara menggunakan `if statement` di dalam *script*.
Selanjutnya kita akan mempelajari temannya yaitu `loops`.

[Lanjut ke Loops](05_loops.md){ .md-button .md-button--primary }
