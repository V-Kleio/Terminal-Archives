# LOG ENTRY #SCRIPT-APPENDIX

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Memahami Interpreter & Shebang

### Apa itu Interpreter?
Komputer tidak paham bahasa manusia (seperti perintah `echo "Halo"`). Diperlukan penerjemah yang membaca kode kita lalu menyuruh prosesor bekerja. Definisi ini mungkin mirip seperti definisi shell sebelumnya, karena shell memang adalah interpreter (command-line interpreter).

- Di **Bash script**, interpreternya adalah program `/bin/bash`.
- Di **Python script**, interpreternya adalah `/usr/bin/python3`.
- Di **Windows**, interpreternya bisa berupa `cmd.exe` atau `powershell.exe`.

### Shebang (`#!`) di Unix vs Windows
- **Unix/Linux/Mac**: Sistem operasi melihat baris pertama file. Jika melihat tanda `#!` (shebang), sistem tahu program apa yang harus dipakai untuk menjalankan file tersebut. Itulah sebabnya script Bash bisa berjalan tanpa ekstensi `.sh`, asalkan ada shebang `#!/bin/bash`.
- **Windows**: Windows **TIDAK** peduli dengan shebang. Windows hanya melihat **Ekstensi File**.
    - Jika akhiran file `.bat` atau `.cmd`, Windows otomatis membukanya dengan Command Prompt.
    - Jika akhiran file `.ps1`, Windows otomatis membukanya dengan PowerShell.
    - Jika akhiran file `.py`, Windows mencarikan `python.exe` (jika sudah terinstall).

---

## Windows Scripting (Batch & PowerShell)

Materi di modul 2 ini berfokus pada Bash (Unix/Linux/Mac). Jika kamu pengguna Windows, kamu memiliki dua pilihan utama untuk scripting: **Batch** (klasik) dan **PowerShell** (modern).

### 1. Batch Script (`.bat`)
Format "jadul" peninggalan MS-DOS. Masih banyak dipakai untuk tugas sederhana karena ringan dan ada di semua komputer Windows.

- **Ekstensi**: `.bat` atau `.cmd`.
- **Komentar**: Menggunakan `REM` atau `::`.

#### A. Variables & User Input
Menggunakan `set` untuk mendefinisikan dan `%var%` untuk memanggil.

```cmd
:: Variable
set nama=Kleio
echo Halo, %nama%

:: User Input
set /p umur="Berapa umurmu? "
echo Umurmu %umur% tahun.
```

#### B. Flow Control
Menggunakan `IF`. Hati-hati dengan spasi dan tanda kurung.

```cmd
IF %umur% GEQ 17 (
    echo Kamu sudah dewasa.
) ELSE (
    echo Kamu belum cukup umur.
)
```
*Operator: `EQU` (=), `NEQ` (!=), `LSS` (<), `LEQ` (<=), `GTR` (>), `GEQ` (>=).*

#### C. Loops
Looping di Batch cukup kompleks, menggunakan perintah `FOR`.

```cmd
:: Loop angka 1-5
FOR /L %%i IN (1,1,5) DO (
    echo Angka ke-%%i
)

:: Loop file dalam folder
FOR %%f IN (*.txt) DO (
    echo Menemukan file: %%f
)
```

#### D. Functions
Batch tidak memiliki fungsi asli, tapi menggunakan Label (`:Label`) dan `CALL`.

```cmd
CALL :Sapa Kleio
EXIT /B %ERRORLEVEL%

:Sapa
echo Halo dari fungsi, %1!
EXIT /B 0
```

#### E. Exit Codes
Menggunakan variabel spesial `%ERRORLEVEL%`.

```cmd
ls file_ngawur.txt
IF %ERRORLEVEL% NEQ 0 (
    echo Terjadi error!
)
```

#### F. Contoh Full Script (`script.bat`)

```cmd
@echo off
:: Judul Script
echo === BAT SCRIPT DEMO ===

:: Input
set /p nama="Masukkan namamu: "

:: Flow Control
IF "%nama%"=="" (
    echo Nama tidak boleh kosong!
    EXIT /B 1
)

:: Function Call
CALL :CekUmur
echo Script selesai dengan kode %ERRORLEVEL%
EXIT /B 0

:: Definisi Fungsi
:CekUmur
set /p umur="Masukkan umur: "
IF %umur% LSS 17 (
    echo Halo Dek %nama%.
) ELSE (
    echo Halo Kak %nama%.
)
EXIT /B 0
```

### 2. PowerShell Script (`.ps1`)
Bahasa scripting modern yang jauh lebih *powerful*, berbasis objek (.NET).

- **Ekstensi**: `.ps1`.
- **Komentar**: Menggunakan `#`.

#### A. Variables & User Input
Variabel diawali `$`. Input menggunakan `Read-Host`.

```powershell
# Variable
$nama = "Kleio"
Write-Output "Halo, $nama"

# User Input
$umur = Read-Host "Berapa umurmu?"
```

#### B. Flow Control
Sintaks mirip bahasa C/Java, tapi operator pembanding mirip Bash.

```powershell
if ($umur -ge 17) {
    Write-Output "Kamu sudah dewasa."
} else {
    Write-Output "Kamu belum cukup umur."
}
```
*Operator: `-eq`, `-ne`, `-lt`, `-le`, `-gt`, `-ge`.*

#### C. Loops
PowerShell memiliki banyak jenis loop: `for`, `foreach`, `while`.

```powershell
# Range Operator (Paling simpel)
1..5 | ForEach-Object { Write-Output "Angka $_" }

# For Loop Klasik
for ($i=1; $i -le 5; $i++) {
    Write-Output "Index $i"
}
```

#### D. Functions
Sangat mirip dengan Bash.

```powershell
function Sapa {
    param($namaOrang)
    Write-Output "Halo dari fungsi, $namaOrang!"
}

Sapa -namaOrang "Kleio"
```

#### E. Exit Codes
Menggunakan variabel `$LastExitCode` untuk program eksternal, atau `$?` (True/False).

```powershell
ls file_ngawur.txt
if ($LastExitCode -ne 0) {
    Write-Output "Terjadi error!"
}
```

#### F. Contoh Full Script (`script.ps1`)

```powershell
Write-Output "=== PS SCRIPT DEMO ==="

# Function
function Cek-Umur {
    param($u)
    if ($u -lt 17) { return "Halo Dek" }
    else { return "Halo Kak" }
}

# Input
$nama = Read-Host "Masukkan namamu"

# Flow Control
if ([string]::IsNullOrEmpty($nama)) {
    Write-Error "Nama kosong!"
    exit 1
}

$umurInput = Read-Host "Masukkan umur"
$sapaan = Cek-Umur -u $umurInput

# Output
Write-Output "$sapaan $nama"
exit 0
```

### Tabel Perbandingan Cepat

| Fitur | Bash (Modul ini) | PowerShell (Rekomendasi Windows) | CMD / Batch (Legacy) |
|---|---|---|---|
| **Ekstensi** | `.sh` (opsional) | `.ps1` (wajib) | `.bat` (wajib) |
| **Shebang** | `#!/bin/bash` | Tidak Butuh | Tidak Butuh |
| **Variabel** | `nama="Kleio"` | `$nama = "Kleio"` | `set nama=Kleio` |
| **Cetak Var** | `echo $nama` | `Write-Output $nama` | `echo %nama%` |
| **Input** | `read nama` | `$nama = Read-Host` | `set /p nama=` |
| **Kondisi** | `if [ $a -eq 1 ]` | `if ($a -eq 1)` | `if %a%==1` |

---

## Process Management

Terkadang *script* yang kamu jalankan memakan waktu lama, atau kamu ingin menghentikan *script* yang "macet".

### Melihat Proses (`ps`, `top`)
- `ps` : Menampilkan snapshot proses saat ini.
- `top` (atau `htop`) : Menampilkan aktivitas proses secara real-time.

### Menjalankan di Background (`&`)
Agar terminal tidak "terkunci" saat menjalankan script lama, tambahkan `&` di akhir perintah:
```bash
./long_script.sh &
```

### Menghentikan Proses (`kill`)
Jika ada script yang error dan tidak bisa berhenti:
1. Cari PID (Process ID) dengan `ps` atau `top`.
2. Hentikan paksa dengan:
   ```bash
   kill 1234  # Ganti 1234 dengan PID
   ```

---

## Scheduling dengan Cron

Ingin script kamu jalan otomatis setiap jam 8 pagi? Linux punya fitur bernama **cron**.

1. Buka editor cron:
   ```bash
   crontab -e
   ```
2. Tambahkan baris jadwal. Formatnya: `menit jam tanggal bulan hari perintah`.
   Contoh (jalan setiap hari jam 08:00):
   ```
   0 8 * * * /home/user/myscript.sh
   ```

---

## Debugging

Jika scriptmu error dan kamu bingung kenapa, jalankan dengan mode debug `-x`. Bash akan menampilkan setiap baris sebelum dieksekusi.

```bash
bash -x script_error.sh
```

Atau tambahkan `set -x` di dalam script untuk mendebug bagian tertentu saja.

---

[Kembali ke Scripting](../module2/01_shebang.md){ .md-button .md-button--primary }
[Lanjut ke Git](../module3/01_intro.md){ .md-button .md-button--primary }
