# LOG ENTRY #REMOTE-APPENDIX

<div class="stamp-box">Status: <span class="redacted">ARCHIVED</span></div>
<div class="stamp-box">Clearance: <span class="redacted">AUTHORIZED PERSONNEL ONLY</span></div>

---

## Project Management Tools

Remote repository modern seperti GitHub dan GitLab bukan sekadar tempat simpan kode. Mereka adalah platform manajemen proyek lengkap.

### 1. Issues
Tempat melaporkan bug, mendiskusikan fitur baru, atau tanya jawab.
-   Developer bisa assign issue ke orang tertentu.
-   Bisa pakai label (e.g., `bug`, `enhancement`, `wontfix`).
-   Issue bisa ditutup otomatis lewat commit message: `Fixes #12`.

### 2. Projects (Kanban Board)
Papan visual untuk mengatur tugas (To Do, In Progress, Done). Mirip Trello tapi terintegrasi langsung dengan Issues dan Pull Request.

### 3. Wiki
Tempat menulis dokumentasi panjang yang terpisah dari kode. Cocok untuk panduan teknis yang kompleks.

---

## .gitignore: Mengabaikan File

File `.gitignore` memberi tahu Git file mana yang **JANGAN** dilacak.
Sangat penting untuk mencegah file sampah masuk repository (seperti folder `node_modules`, file build `.exe`, atau kunci rahasia `.env`).

Contoh isi `.gitignore`:
```text
# Abaikan folder node_modules
node_modules/

# Abaikan file log
*.log

# Abaikan file environment (Rahasasia!)
.env
```

---

## Referensi Cepat Remote

| Perintah | Fungsi |
| :--- | :--- |
| `git remote -v` | Cek daftar remote URL |
| `git push -u origin main` | Upload kode pertama kali |
| `git pull` | Download update dan merge |
| `git fetch` | Download update tanpa merge |
| `git clone [url]` | Download repo baru |
| `git tag [verso]` | Buat tag versi |

[Kembali ke Menu Utama](../index.md){ .md-button .md-button--primary }
