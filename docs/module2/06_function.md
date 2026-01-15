# LOG ENTRY #SCRIPT-06

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Functions

Dalam scripting, sering kali kamu ingin menjalankan sekelompok perintah yang sama di beberapa tempat berbeda.
Daripada menulis ulang perintah yang sama berulang kali, kamu bisa membuat **function** (fungsi).
Fungsi adalah blok kode yang bisa dipanggil berkali-kali.

---

## Membuat Functions

Sintaks dasar fungsi di Bash:

!!! tip "Windows Users"
    PowerShell mendukung fungsi mirip Bash, namun Batch menggunakan teknik "Label" dan "Call". Lihat [Functions di Windows](99_additional.md#windows-scripting-batch-powershell).

```bash
nama_fungsi() {
    # perintah-perintah di sini
}
```

Atau bisa juga:

```bash
function nama_fungsi {
    # perintah-perintah di sini
}
```

Untuk memanggil fungsi, cukup tulis nama fungsinya:

```bash
nama_fungsi
```

Contoh fungsi.

```bash
say() {
    echo "Halo, selamat datang di Terminal Archives!"
}

say
```

---

## Function dengan Arguments

Fungsi bisa menerima argumen seperti *script* biasa.
Argumen diakses dengan `$1`, `$2`, dan seterusnya.

```bash
tambah() {
    hasil=$(( $1 + $2 ))
    echo "Hasil: $hasil"
}

tambah 5 7
```

---

## Function Returning Value

Fungsi di Bash biasanya mengembalikan nilai lewat `echo`, lalu hasilnya bisa ditangkap dengan **command subtitution**:

```bash
kali() {
    echo $(( $1 * $2 ))
}

hasil=$(kali 3 4)
echo "3 x 4 = $hasil"
```

---

## Summary

| Konsep                | Fungsi                                      |
|-----------------------|---------------------------------------------|
| nama_fungsi() { ... } | Mendefinisikan fungsi                       |
| nama_fungsi           | Memanggil fungsi                            |
| $1, $2, ...           | Argumen fungsi                              |
| echo                  | Mengembalikan nilai dari fungsi             |

---

## Next Step

Sekarang kamu sudah mengetahui cara membuat function di dalam *script*.
Selanjutnya kita akan mempelajari exit code.

[Lanjut ke Exit Code](07_exit_code.md){ .md-button .md-button--primary }
