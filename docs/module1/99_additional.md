# LOG ENTRY #CLI-APPENDIX

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Command Equivalence

Perintah-perintah yang ditulis dalam module ini merupakan perintah untuk terminal di sistem Unix (Linux/Mac). Perintah di Windows memiliki perbedaan. Berikut merupakan perbandingan perintah di Unix, Command Prompt (Windows), dan PowerShell (Windows).

### Identitas & Output (`whoami`, `echo`)

=== "Unix (Linux/Mac)"
    ```bash
    whoami
    echo "Halo"
    ```
=== "Command Prompt (Windows)"
    ```cmd
    whoami
    echo Halo
    ```
=== "PowerShell (Windows)"
    ```powershell
    whoami
    Write-Output "Halo"
    ```

### Lokasi & Navigasi (`pwd`, `ls`, `cd`)

=== "Unix (Linux/Mac)"
    ```bash
    pwd
    ls
    cd nama_folder
    ```
=== "Command Prompt (Windows)"
    ```cmd
    cd
    dir
    cd nama_folder
    ```
=== "PowerShell (Windows)"
    ```powershell
    Get-Location
    Get-ChildItem
    Set-Location nama_folder
    ```

### Manipulasi File & Folder (`touch`, `mkdir`, `cp`, `mv`, `rm`)

=== "Unix (Linux/Mac)"
    ```bash
    touch nama_file.txt
    mkdir nama_folder
    cp sumber.txt tujuan.txt
    mv lama.txt baru.txt
    rm nama_file.txt
    ```
=== "Command Prompt (Windows)"
    ```cmd
    type nul > nama_file.txt
    mkdir nama_folder
    copy sumber.txt tujuan.txt
    move lama.txt baru.txt
    del nama_file.txt
    ```
=== "PowerShell (Windows)"
    ```powershell
    New-Item nama_file.txt
    New-Item -ItemType Directory nama_folder
    Copy-Item sumber.txt tujuan.txt
    Move-Item lama.txt baru.txt
    Remove-Item nama_file.txt
    ```

### Membaca File (`cat`, `less`, `head`, `tail`)

=== "Unix (Linux/Mac)"
    ```bash
    cat nama_file.txt
    less nama_file.txt
    head -n 10 nama_file.txt
    tail -n 10 nama_file.txt
    ```
=== "Command Prompt (Windows)"
    ```cmd
    type nama_file.txt
    more nama_file.txt
    :: Tidak ada equivalent langsung untuk head/tail di CMD
    ```
=== "PowerShell (Windows)"
    ```powershell
    Get-Content nama_file.txt
    Get-Content nama_file.txt | Out-Host -Paging
    Get-Content nama_file.txt -TotalCount 10
    Get-Content nama_file.txt -Tail 10
    ```

### Pencarian (`grep`, `find`)

=== "Unix (Linux/Mac)"
    ```bash
    grep "teks" nama_file.txt
    find . -name "*.txt"
    ```
=== "Command Prompt (Windows)"
    ```cmd
    findstr "teks" nama_file.txt
    dir /s /b *.txt
    ```
=== "PowerShell (Windows)"
    ```powershell
    Select-String "teks" nama_file.txt
    Get-ChildItem -Recurse -Filter "*.txt"
    ```

### I/O Redirection & Pipes

=== "Unix (Linux/Mac)"
    ```bash
    command > output.txt
    command >> output.txt
    command < input.txt
    command1 | command2
    command 2> error.log
    ```
=== "Command Prompt (Windows)"
    ```cmd
    command > output.txt
    command >> output.txt
    command < input.txt
    command1 | command2
    command 2> error.log
    ```
=== "PowerShell (Windows)"
    ```powershell
    command > output.txt
    command >> output.txt
    # PowerShell tidak mendukung redirection '<' secara langsung
    Get-Content input.txt | command
    command1 | command2
    command 2> error.log
    ```

---

## ++ctrl++ Button Behaviour

Di terminal, kombinasi tombol ++ctrl++ memiliki fungsi yang berbeda.

Berikut adalah beberapa kombinasi ++ctrl++ yang sering digunakan:

- **++ctrl+c++ (Interrupt)**: Menghentikan paksa perintah yang sedang berjalan. Berguna jika kamu menjalankan program yang tidak kunjung selesai atau ingin membatalkan perintah yang salah ketik.
- **++ctrl+l++ (Clear)**: Membersihkan layar terminal, fungsinya sama dengan mengetik perintah `clear`.
- **++ctrl+a++ (Start)**: Memindahkan kursor ke bagian paling awal dari baris perintah yang sedang kamu ketik.
- **++ctrl+e++ (End)**: Memindahkan kursor ke bagian paling akhir dari baris perintah.
- **++ctrl+u++ (Erase to Start)**: Menghapus semua teks dari posisi kursor saat ini ke arah kiri hingga awal baris.
- **++ctrl+k++ (Erase to End)**: Menghapus semua teks dari posisi kursor saat ini ke arah kanan hingga akhir baris.
- **++ctrl+w++ (Erase Word)**: Menghapus satu kata tepat di sebelah kiri kursor.
- **++ctrl+r++ (Reverse Search)**: Mencari perintah yang pernah kamu ketik sebelumnya di history. Cukup ketik potongan katanya, dan shell akan mencarikan perintah lengkapnya.
- **++ctrl+d++ (Exit/EOF)**: Mengirim sinyal *End-Of-File*. Jika kamu sedang di shell biasa, ini akan menutup terminal (sama seperti `exit`).

!!! info
    Kombinasi tombol ini mungkin sedikit berbeda jika kamu menggunakan terminal tertentu di Windows (seperti CMD bawaan), namun hampir semuanya bekerja dengan baik di Linux, Mac, dan PowerShell.

---

## Tips & Shortcut

Ada beberapa fitur bawaan shell yang bisa membuatmu mengetik jauh lebih cepat.

### 1. Tab Completion
- Ketik beberapa huruf awal dari nama file, folder, atau perintah, lalu tekan **++tab++**. Shell akan otomatis melengkapi namanya.
- Jika ada lebih dari satu pilihan, tekan **++tab++** dua kali untuk melihat semua daftar kemungkinan yang diawali huruf tersebut.

### 2. Navigasi History (Panah Atas/Bawah)
- Gunakan tombol **++up++** untuk memanggil kembali perintah-perintah sebelumnya.
- Gunakan tombol **++down++** untuk kembali ke perintah yang lebih baru jika kamu sudah mencarinya terlalu jauh ke atas.

### 3. Perintah `history`
- Ketik perintah `history`. Terminal akan menampilkan daftar panjang berisi history perintahmu beserta nomor urutnya.
- Kamu bisa menjalankan kembali perintah dari history dengan mengetik `!<nomor>`, misalnya `!67` untuk menjalankan perintah nomor 67.

### 4. Menjalankan Perintah Terakhir (`!!`)
Jika kamu lupa mengetik `sudo` di awal perintah panjang, kamu tidak perlu mengetik ulang semuanya. Cukup ketik:
```bash
sudo !!
```
Simbol `!!` akan otomatis digantikan oleh perintah terakhir yang kamu jalankan.

### 5. Multi-Commands (Chaining)
Kamu bisa menjalankan beberapa perintah sekaligus dalam satu baris:

- Pemisah `;`: Menjalankan perintah secara berurutan tanpa peduli perintah sebelumnya berhasil atau gagal.
  Contoh: `mkdir folder ; cd folder`
- Pemisah `&&`: Menjalankan perintah kedua **hanya jika** perintah pertama berhasil.
  Contoh: `make && ./program`
- Pemisah `||`: Menjalankan perintah kedua **hanya jika** perintah pertama gagal.
  Contoh: `cd folder_tidak_ada || echo gagal`

!!! info
    Beberapa fitur ini mungkin berbeda pada Windows(Command Prompt/PowerShell).

---

[Kembali ke Terminal](01_intro.md){ .md-button .md-button--primary }
[Lanjut ke Scripting](../module2/01_shebang.md){ .md-button .md-button--primary }
