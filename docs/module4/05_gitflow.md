# LOG ENTRY #REMOTE-05

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## GitFlow: Manajeman Branch Tingkat Lanjut

Di proyek enterprise, workflow Feature Branch mungkin tidak cukup. Kita butuh cara mengelola versi rilis, hotfix, dan development. Inilah **GitFlow**.

GitFlow membagi branch menjadi beberapa peran spesifik.

---

## Struktur Cabang GitFlow

1.  **Main (Master)**: Hanya berisi kode produksi yang stabil. Tidak boleh commit langsung ke sini.
2.  **Develop**: Branch utama untuk development. Semua fitur baru masuk ke sini dulu.
3.  **Feature**: Cabang dari `develop`. Setiap fitur punya branch sendiri (e.g., `feature/payment-gw`).
4.  **Release**: Cabang dari `develop` saat persiapan rilis baru (e.g., `release/v1.0`). Untuk testing akhir.
5.  **Hotfix**: Cabang dari `main` untuk perbaikan bug darurat di production (e.g., `hotfix/login-bug`).

---

## Simulasi GitFlow Sederhana

### 1. Memulai Fitur Baru
Branch dari `develop`:
```bash
git checkout develop
git checkout -b feature/user-profile
```
...kerja... commit...

### 2. Selesai Fitur
Merge kembali ke `develop`:
```bash
git checkout develop
git merge feature/user-profile
```

### 3. Persiapan Rilis
Jika `develop` sudah punya fitur cukup untuk rilis v1.0, buat release branch:
```bash
git checkout develop
git checkout -b release/v1.0
```
Disini hanya boleh fix bug kecil, dilarang tambah fitur.

### 4. Rilis (Merge ke Main dan Develop)
Saat `release/v1.0` stabil:
```bash
# Merge ke Main untuk produksi
git checkout main
git merge release/v1.0

# Merge balik ke Develop agar develop juga dapet fix-nya
git checkout develop
git merge release/v1.0
```

---

## Kapan Pakai GitFlow?

-   **YA**, jika proyekmu punya siklus rilis terjadwal (misal rilis tiap 2 minggu).
-   **TIDAK**, jika proyekmu butuh Continuous Deployment (setiap commit langsung deploy ke production). Untuk ini, gunakan **Trunk Based Development**.

---

## Next Step

Bagaimana menandai titik rilis `v1.0` secara permanen? Kita akan menggunakan Tagging.

[Lanjut ke Tags & Releases](06_tags_releases.md){ .md-button .md-button--primary }
