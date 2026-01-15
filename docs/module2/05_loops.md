# LOG ENTRY #SCRIPT-05

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Loops

Dalam scripting, sering kali kamu ingin menjalankan perintah yang sama berulang kali, baik untuk setiap file di folder, setiap baris data, atau selama suatu kondisi masih terpenuhi.
Di Bash, ini bisa dilakukan dengan **loops**.

---

## For Loop

`for` loop digunakan untuk mengulang perintah untuk setiap item dalam sebuah daftar.

!!! tip "Windows Users"
    Looping di Windows (terutama Batch) cukup berbeda dan bisa sedikit *tricky*. PowerShell memiliki opsi looping yang lebih modern. Lihat [Looping di Windows](99_additional.md#windows-scripting-batch-powershell).

Contoh:

```bash
for nama in Alice Bob Charlie
do
    echo "Halo, $nama!"
done
```

Kamu juga bisa mengiterasi semua file di folder:

```bash
for file in *.txt
do
    echo "Isi file: $file"
    cat "$file"
done
```

- `*.txt` akan mencocokkan semua file dengan ekstensi `.txt` di direktori saat ini.
- Variabel `file` akan berisi nama file yang sedang diproses pada setiap iterasi.

---

## While Loop

`while` loop digunakan untuk mengulang perintah selama suatu kondisi bernilai benar (true).

Contoh:

```bash
angka=1
while [ $angka -le 5 ]
do
    echo "Angka: $angka"
    angka=$((angka + 1))
done
```

Loop di atas akan mencetak angka 1 sampai 5.

---

## Membaca File Baris per Baris

Kamu bisa menggunakan `while` loop untuk membaca isi file baris per baris:

```bash
while read baris
do
    echo "Baris: $baris"
done < nama_file.txt
```

- Perintah di atas akan membaca setiap baris dari `nama_file.txt` dan menampilkannya ke layar.

---

## Break & Continue

- `break` : Keluar dari loop lebih awal.
- `continue` : Lompat ke iterasi berikutnya tanpa menjalankan sisa perintah di dalam loop.

Contoh:

```bash
for angka in 1 2 3 4 5
do
    if [ $angka -eq 3 ]; then
        continue
    fi
    echo "Angka: $angka"
done
```
Perintah di atas akan melewati angka 3.

---

## Summary

| Struktur         | Fungsi                                      |
|------------------|---------------------------------------------|
| for ... in ...   | Mengulang untuk setiap item dalam daftar    |
| while [ kondisi ]| Mengulang selama kondisi terpenuhi          |
| break            | Keluar dari loop                            |
| continue         | Lompat ke iterasi berikutnya                |

---

## Next Step

Sekarang kamu sudah mengetahui cara menggunakan loop di dalam script.
Selanjutnya kita akan belajar tentang function.

[Lanjut ke Function](06_function.md){ .md-button .md-button--primary }
