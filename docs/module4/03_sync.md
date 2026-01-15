# LOG ENTRY #REMOTE-03

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Sync: Push, Pull, Clone

Inti dari remote repository adalah sinkronisasi. Bagaimana mengirim kodemu ke server, dan bagaimana mengambil kode terbaru dari server.

---

## 1. Menambahkan Remote: `git remote`

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

## 2. Mengirim Kode: `git push`

Mengupload commit dari lokal ke remote server.

```bash
git push -u origin main
```
- `-u` (upstream): Mengikat branch lokal `main` dengan branch `main` di `origin`.
- Untuk push selanjutnya, cukup ketik `git push`.

## 3. Mengambil Kode Proyek Baru: `git clone`

Jika kamu ingin mendownload repository yang sudah ada di GitHub (misal repository open source atau tugas teman).

```bash
git clone git@github.com:username/repo.git
```
Perintah ini otomatis melakukan `git init`, `git remote add origin`, dan mendownload semua file.

## 4. Update Kode: `git pull` vs `git fetch`

Bagaimana jika temanmu melakukan push perubahan baru ke GitHub, dan kamu ingin mengambilnya?

### A. git fetch (Aman)
Mendownload info perubahan dari remote, TAPI tidak langsung menggabungkannya ke kodemu.
```bash
git fetch origin
```
Ini aman untuk melihat apa yang baru tanpa mengubah kodemu.

### B. git pull (Cepat)
Mendownload DAN langsung menggabungkan (merge) ke kodemu.
```bash
git pull origin main
```
Sama dengan `git fetch` + `git merge`.

---

## 5. Syncing Fork (Upstream)

Jika kamu melakukan **Fork** repository orang lain, repository-mu tidak akan otomatis update jika pemilik asli mengupdate kodenya. Kamu perlu menyinkronkannya manual.

1.  **Tambahkan remote "upstream"** (alamat repository asli):
    ```bash
    git remote add upstream git@github.com:pemilik-asli/repo.git
    ```

2.  **Ambil perubahan dari upstream**:
    ```bash
    git fetch upstream
    ```

3.  **Gabungkan ke branch kamu**:
    ```bash
    git checkout main
    git merge upstream/main
    ```

---

## Next Step

Sekarang kamu sudah bisa push dan pull, mari pelajari pola kerja (workflow) standar saat berkolaborasi dalam tim.

[Lanjut ke Workflows](04_workflows.md){ .md-button .md-button--primary }
