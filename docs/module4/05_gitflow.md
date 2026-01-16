# LOG ENTRY #REMOTE-05

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## GitFlow

Di proyek besar, workflow Feature Branch mungkin tidak cukup. Kita butuh cara mengelola versi rilis, hotfix, dan development. Inilah **GitFlow**.

GitFlow membagi branch menjadi beberapa peran spesifik.

---

## Struktur Cabang GitFlow

1.  **Main (Master)**: Hanya berisi kode produksi yang stabil. Tidak boleh commit langsung ke sini.
2.  **Develop (dev)**: Branch utama untuk development. Semua fitur baru masuk ke sini dulu.
3.  **Feature (feat)**: Cabang dari `develop`. Setiap fitur punya branch sendiri (e.g., `feature/payment-gw`).
4.  **Bugfix**: Cabang dari `develop`. Mirip dengan feature, tapi khusus untuk perbaikan bug semasa development (bukan production).
5.  **Release**: Cabang dari `develop` saat persiapan rilis baru (e.g., `release/v1.0`). Untuk testing akhir.
6.  **Hotfix**: Cabang dari `main` untuk perbaikan bug darurat di production (e.g., `hotfix/login-bug`).

---

## Simulasi GitFlow Sederhana

### 1. Memulai Fitur Baru atau BugFix
Buat Feature atau Bugfix Branch dari `develop`:
```bash
git checkout develop
git checkout -b feature/user-profile
```

### 2. Selesai Fitur
Merge kembali ke `develop`:

!!! danger "Gunakan Pull Request"
    Di lingkungan tim profesional, **JANGAN** merge manual ke `develop` atau `main` di lokal seperti perintah di bawah ini.
    Sebaiknya Push branch kamu, lalu buat **Pull Request (PR)** agar direview oleh tim. Perintah di bawah hanya untuk contoh sederhana.

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
Saat `release/v1.0` stabil (Gunakan PR untuk ini juga!):
```bash
# Merge ke Main untuk produksi
git checkout main
git merge release/v1.0

# Merge balik ke Develop agar develop juga dapet fix-nya
git checkout develop
git merge release/v1.0
```

---

## Strategi History: Merge vs Rebase

Apa bedanya Merge biasa dengan Rebase?

### 1. Merge Commit (`--no-ff`)
GitFlow standar sangat menyarankan penggunaan Merge Commit (Default).

-   Kelebihan: Terlihat jelas kapan sebuah fitur dimulai dan berakhir.
-   Kapan dipakai: Saat menggabungkan `feature` yang sudah selesai ke `develop`, atau `release` ke `main` dan `develop`.

### 2. Rebase Strategy
Rebase memindah commit-mu ke ujung depan history.

-   Kelebihan: History menjadi **garis lurus (linear)** dan sangat rapi. Tidak ada percabangan kompleks.
-   Kapan dipakai:
    -   Merapikan branch `feature` lokal SEBELUM di-push atau di-merge (agar history bersih).
    -   Update branch kamu dengan perubahan terbaru dari `develop` (`git pull --rebase`).

!!! tip "Rekomendasi"
    *   Gunakan **Rebase** di branch lokalmu agar tidak tertinggal dari upstream.
    *   Gunakan **Merge (PR)** saat fitur sudah final dan masuk ke `develop` agar jejak fiturnya terekam.

---

## Kapan Pakai GitFlow?

-   **YA**, jika proyekmu punya siklus rilis terjadwal (misal rilis tiap 2 minggu).
-   **TIDAK**, jika proyekmu butuh Continuous Deployment (setiap commit langsung deploy ke production). Untuk ini, gunakan [**Trunk Based Development**](99_additional.md/#trunk-based-development).

---

## Next Step

Bagaimana menandai commit rilis `v1.0` secara permanen? Kita akan menggunakan Tagging.

[Lanjut ke Tags & Releases](06_tags_releases.md){ .md-button .md-button--primary }
