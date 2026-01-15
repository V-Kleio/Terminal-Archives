# LOG ENTRY #SCRIPT-01

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Intro to Scripting

Setelah mengenal perintah-perintah dasar di terminal, kamu akan menemukan bahwa banyak tugas bisa diotomasi dengan menulis *script*.
*Script* adalah kumpulan perintah yang disimpan dalam sebuah file dan bisa dijalankan berulang kali.

---

## Apa itu Shebang?

Setiap *script* di Linux/Unix biasanya diawali dengan baris khusus yang disebut **shebang**.
Shebang adalah dua karakter `#!` diikuti path interpreter yang akan menjalankan *script*.

!!! tip "Windows Users"
    Konsep Shebang (`#!`) tidak digunakan di Windows (Batch/PowerShell). Sistem lebih melihat ekstensi file. Lihat [Interpreter & Shebang di Windows](99_additional.md#memahami-interpreter-shebang).

Contoh shebang untuk Bash:

```bash
#!/bin/bash
```

Baris ini memberi tahu sistem bahwa *script* harus dijalankan menggunakan Bash.

Kamu juga bisa menggunakan interpreter lain, misal Python:

```bash
#!/usr/bin/python3
```

Shebang harus diletakkan di baris pertama file *script*.

---

## Script Pertamamu

1.  Buat file baru bernama `hello.sh`. Kamu bisa menggunakan text editor grafis atau langsung dari terminal menggunakan `nano`:
    ```bash
    nano hello.sh
    ```
    (*Tekan ++ctrl+x++, lalu ++y++, lalu ++enter++ untuk menyimpan dan keluar dari `nano`*).

2.  Isi dengan kode berikut:
    ```bash
    #!/bin/bash
    echo "Hello, scripting!"
    ```

3.  Simpan file tersebut.

---

## Execution Permission: `chmod +x`

Agar *script* bisa dijalankan langsung, kamu perlu memberi izin eksekusi pada file tersebut.

```bash
chmod +x hello.sh
```

Perintah ini membuat file `hello.sh` bisa dieksekusi sebagai program.

---

## Menjalankan *script*

Setelah diberi izin eksekusi, jalankan *script* dengan:

```bash
./hello.sh
```

Tanda `./` menunjukkan bahwa file berada di direktori saat ini.

Kamu juga bisa menjalankan *script* tanpa mengubah izin eksekusi, dengan memanggil interpreter secara eksplisit:

```bash
bash hello.sh
```

---

## Tambahan

- Gunakan komentar dengan `#` untuk memberi penjelasan di dalam *script*.
- Simpan *script* dengan ekstensi `.sh` agar mudah dikenali.
- Selalu mulai *script* dengan shebang agar interpreter yang digunakan jelas.

---

## Summary

| Konsep            | Fungsi                                      |
|-------------------|---------------------------------------------|
| Shebang           | Menentukan interpreter untuk *script*       |
| chmod +x          | Memberi izin eksekusi pada file             |
| ./*script*.sh     | Menjalankan *script* di direktori saat ini  |

---

## Next Step

Sekarang kamu sudah tahu caranya membuat *script*.
Selanjutnya mari kita mulai menulis kode dan belajar tentang variabel.

[Lanjut ke Variables](02_variables.md){ .md-button .md-button--primary }
