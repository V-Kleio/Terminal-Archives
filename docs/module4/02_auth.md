# LOG ENTRY #REMOTE-02

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Authentication: Menghubungkan Git dengan Remote Repository

Agar bisa mengirim (push) atau mengambil (pull) perubahan ke dan dari remote repository seperti GitHub, kamu perlu melakukan **autentikasi**.
Autentikasi memastikan hanya pengguna yang sah yang bisa mengakses repository, terutama untuk operasi yang mengubah data.

---

## Dua Cara Utama Autentikasi: SSH Keys dan Personal Access Token (PAT)

Ada dua metode utama yang umum digunakan untuk autentikasi dengan layanan seperti GitHub:

### 1. SSH Keys

**SSH Key** adalah sepasang kunci kriptografi: satu kunci privat (disimpan di komputer lokal) dan satu kunci publik (didaftarkan di GitHub).

- **Keunggulan:**
    - Aman dan mudah digunakan setelah setup.
    - Tidak perlu memasukkan password setiap kali push/pull.
- **Cara kerja:**
    1. Buat SSH key di komputer lokal:
        ```bash
        ssh-keygen -t ed25519 -C "email@example.com"
        ```
    2. Tambahkan kunci publik (`~/.ssh/id_ed25519.pub`) ke akun GitHub (menu Settings > SSH and GPG keys).
    3. Gunakan URL SSH saat menambah remote:
        ```
        git@github.com:username/nama-repo.git
        ```
    4. Setelah setup, kamu bisa push/pull tanpa perlu password.

### 2. Personal Access Token (PAT)

**Personal Access Token** adalah kode unik yang digunakan sebagai pengganti password saat mengakses GitHub melalui HTTPS.

- **Keunggulan:**
    - Mudah digunakan di berbagai layanan dan CI/CD.
    - Bisa diatur hak aksesnya secara spesifik.
- **Cara kerja:**
    1. Buat token di GitHub (Settings > Developer settings > Personal access tokens).
    2. Saat push/pull dengan HTTPS, masukkan token sebagai password:
        ```
        https://github.com/username/nama-repo.git
        ```
    3. Token bisa disimpan di credential manager agar tidak perlu diketik setiap saat.

---

## Mana yang Sebaiknya Digunakan?

- **SSH Key** cocok untuk penggunaan sehari-hari di komputer pribadi.
- **PAT** lebih fleksibel untuk integrasi dengan aplikasi lain, CI/CD, atau jika SSH tidak tersedia.

---

## Tips Keamanan

- Jangan pernah membagikan kunci privat atau token ke orang lain.
- Hapus token yang sudah tidak digunakan.
- Gunakan passphrase saat membuat SSH key untuk keamanan ekstra.

---

## Ringkasan

| Metode      | Kelebihan                        | Kekurangan                  |
|-------------|----------------------------------|-----------------------------|
| SSH Key     | Aman, tidak perlu password lagi  | Perlu setup awal            |
| PAT         | Fleksibel, mudah diintegrasi     | Token harus dijaga baik-baik |

---

## Next Step

Autentikasi adalah langkah penting untuk menjaga keamanan repository dan kolaborasi.
Dengan memahami perbedaan SSH Key dan PAT, kamu bisa memilih metode yang paling sesuai untuk kebutuhanmu.

[Lanjut ke Syncing](03_sync.md){ .md-button .md-button--primary }
