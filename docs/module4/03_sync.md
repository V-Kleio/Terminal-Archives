# LOG ENTRY #REMOTE-03

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Sync: Push, Pull, Clone, & Fork

Inti dari remote repository adalah sinkronisasi. Bagaimana mengirim kodemu ke server, dan bagaimana mengambil kode terbaru dari server.

---

## Menambahkan Remote: `git remote`

Jika kamu memulai proyek dari lokal (`git init`), kamu perlu memberi tahu Git ke mana kode ini harus dikirim.

```bash
git remote add origin git@github.com:username/repo.git
```

- `origin`: Nama alias default untuk remote utama (bisa diganti apa saja, tapi standar industri adalah `origin`).
- URL: Alamat repository di GitHub (gunakan versi SSH agar tidak diminta password terus).

Untuk mengecek remote yang terdaftar:
```bash
git remote -v
```

## Mengirim Kode: `git push`

Mengupload commit dari lokal ke remote server.

```bash
git push -u origin main
```

- `-u` (upstream): Menghubungkan branch lokal `main` dengan branch `main` di `origin`.
- Untuk push selanjutnya, cukup ketik `git push`.

## Mengambil Kode Repositori Baru: `git clone`

Jika kamu ingin mendownload repository yang sudah ada di GitHub (misal repository open source atau tugas teman).

```bash
git clone git@github.com:username/repo.git
```

Perintah ini otomatis melakukan `git init`, `git remote add origin`, dan mendownload semua file.

## Update Kode: `git pull` vs `git fetch`

Bagaimana jika temanmu melakukan push perubahan baru ke GitHub, dan kamu ingin mengambilnya?

### Fetch

Mendownload info perubahan dari remote, TAPI tidak langsung menggabungkannya ke kodemu.

```bash
git fetch origin
```

Ini aman untuk melihat apa yang baru tanpa mengubah kodemu.

### Pull

Mendownload DAN langsung menggabungkan (merge) ke kodemu.

```bash
git pull origin main
```

Sama dengan `git fetch` + `git merge`.

---

## Fork

**Fork** adalah menyalin repository milik orang lain ke akun GitHub pribadimu.
Berbeda dengan `clone` yang menyalin ke komputer lokal, `fork` menyalin dari server ke server (contoh: dari GitHub `pemilik-asli` ke GitHub `kamu`).

**Kenapa melakukan Fork?**

1.  Kamu ingin memperbaiki bug di repository orang lain, tapi kamu tidak punya izin untuk mengubahnya secara langsung (Write Access).
2.  Kamu ingin mengubah kode orang lain sesuka hati tanpa takut merusak repository aslinya.

### Syncing Fork (Upstream)

Masalah utama saat melakukan Fork adalah: repository-mu tidak akan otomatis update jika pemilik asli mengupdate kodenya. Kamu perlu menyinkronkannya manual.

1.  **Tambahkan remote "upstream"** (alamat repository asli):
    Saat clone dari fork, remote `origin` menunjuk ke fork kamu. Kita perlu menambah remote baru (biasanya disebut `upstream`) yang menunjuk ke repo asli.
    ```bash
    git remote add upstream git@github.com:pemilik-asli/repo.git
    ```

2.  **Ambil perubahan dari upstream**:
    ```bash
    git fetch upstream
    ```

3.  **Gabungkan ke branch kamu**:
    Pastikan kamu berada di branch utama, lalu merge perubahan dari upstream.
    ```bash
    git checkout main
    git merge upstream/main
    ```

### Mengirim Perubahan ke Repository Asli

Bagaimana jika kamu sudah selesai mengedit di repository fork-mu dan ingin mengirimkan perubahan tersebut kembali ke repository asli?

Kamu **tidak bisa** langsung melakukan `git push` ke repository asli (`upstream`) karena biasanya kamu tidak memiliki izin tulis (Write Access).

Mekanisme yang digunakan adalah **Pull Request**.

1.  Lakukan `git push` ke repository fork milikmu sendiri (`origin`).
2.  Buka GitHub dan buat **Pull Request** dari fork-mu ke repository asli.

!!! info "Pembahasan Lanjut"
    Detail lengkap tentang tata cara membuat **Pull Request** dan kolaborasi tim akan dibahas lebih lanjut.

---

## Next Step

Sekarang kamu sudah bisa push dan pull, mari pelajari pola kerja (workflow) standar saat berkolaborasi dalam tim.

[Lanjut ke Workflows](04_workflows.md){ .md-button .md-button--primary }
