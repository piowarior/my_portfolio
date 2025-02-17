![image](https://github.com/user-attachments/assets/4c693c2b-e514-460c-8039-67b7508f845b)# my_portfolio

# 🌍 Panduan Lengkap: Menghubungkan GitHub ke Git di WSL + Instalasi Zsh 🎯

## 📌 Pendahuluan

GitHub adalah platform yang digunakan untuk menyimpan dan mengelola kode menggunakan sistem version control Git. Untuk mempermudah pengelolaan kode di Windows, kita dapat menggunakan **WSL (Windows Subsystem for Linux)**, yang memungkinkan kita menjalankan lingkungan Linux langsung di dalam Windows. 🏆

Dalam panduan ini, kita akan:

✅ Membuat akun GitHub dan repository
✅ Menginstal WSL dan Git di Windows
✅ Menghubungkan GitHub dengan SSH Key
✅ Menggunakan Git di WSL untuk mengelola kode
✅ Menginstal Zsh dan Oh My Zsh untuk terminal yang lebih menarik ✨

---

# 🔹 1. Membuat Akun GitHub 📝

Jika kamu belum punya akun GitHub, ikuti langkah-langkah berikut:

1. **Buka GitHub** ➝ Pergi ke [https://github.com](https://github.com) 🌐
2. **Klik "Sign up"** di pojok kanan atas 📌
3. **Isi Data:**  
   - **Username:** Pilih nama unik untuk akun GitHub
   - **Email:** Masukkan email aktif kamu 📧
   - **Password:** Buat kata sandi yang kuat 🔒
4. **Klik "Create account"** 🆕
5. **Verifikasi akun** melalui email yang dikirim oleh GitHub 📩

Sekarang akun GitHub kamu sudah siap digunakan! 🚀

---

# 🔹 2. Membuat Repository di GitHub 📂

Repository adalah tempat menyimpan kode di GitHub. Berikut cara membuatnya:

1. **Login ke GitHub** dan klik ikon **+** di pojok kanan atas ➝ **New repository**
2. **Isi detail repository:**  
   - **Repository name** ➝ Misalnya: `project-wsl` 📁
   - **Description** (opsional) ➝ Contoh: "Repositori latihan Git di WSL" ✏️
   - **Public atau Private** ➝ Pilih **Public** jika ingin terbuka, atau **Private** jika ingin rahasia 🔑
   - **Jangan centang "Initialize this repository with a README"** (agar kita bisa menambahkannya nanti)
3. **Klik "Create repository"** ✅

Setelah repository dibuat, catat URL repository-nya! Kamu akan melihat opsi **HTTPS** dan **SSH**, gunakan **SSH** untuk koneksi yang lebih aman.

---

# 🔹 3. Menginstal WSL di Windows 🖥️

## ✅ a. Aktifkan WSL
Buka **PowerShell sebagai administrator** dan jalankan perintah:
```powershell
wsl --install
```
Perintah ini akan menginstal WSL dengan distribusi default (biasanya **Ubuntu**). Jika ingin memilih distribusi lain:
```powershell
wsl --list --online
wsl --install -d <nama_distro>
```
Misalnya, untuk menginstal Ubuntu:
```powershell
wsl --install -d Ubuntu
```
Setelah proses selesai, **restart komputer** jika diminta.

## ✅ b. Cek Instalasi WSL
Buka **PowerShell** dan jalankan:
```powershell
wsl
```
Pastikan WSL berjalan dengan perintah:
```bash
uname -a
```
Jika tampil informasi kernel Linux, berarti WSL sudah berhasil terinstal! 🎉

---

# 🔹 4. Menginstal Git di WSL 🔗

Setelah WSL aktif, buka terminal WSL (Ubuntu) dan jalankan:
```bash
sudo apt update && sudo apt install git -y
```
Cek apakah Git sudah terinstal dengan:
```bash
git --version
```
Git kini sudah siap digunakan! 🎯

---

# 🔹 5. Menghubungkan GitHub ke Git di WSL 🔐

Agar Git di WSL bisa terhubung dengan GitHub, kita perlu membuat **SSH Key**.

## ✅ a. Buat SSH Key
Di terminal WSL, jalankan:
```bash
ssh-keygen -t ed25519 -C "email_kamu@gmail.com"
```
- **Gantilah "email_kamu@gmail.com"** dengan email GitHub kamu.
- Tekan **Enter** untuk lokasi penyimpanan (gunakan default `~/.ssh/id_ed25519`).
- Tekan **Enter** lagi untuk passphrase (opsional).

SSH Key berhasil dibuat! 🔑

## ✅ b. Tambahkan SSH Key ke GitHub
1. Tampilkan SSH key yang baru dibuat:
   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```
2. **Salin seluruh isi** SSH Key tersebut ✂️
3. **Buka GitHub** ➝ **Settings** ➝ **SSH and GPG keys** ➝ **New SSH key**
4. **Paste SSH key** ➝ Klik **Add SSH key** ✅

## ✅ c. Tes Koneksi
Jalankan:
```bash
ssh -T git@github.com
```
Jika sukses, akan muncul pesan:
```
Hi <username>! You've successfully authenticated...
```
Selamat! GitHub sudah terhubung dengan Git di WSL. 🎉

---

# 🔹 6. Clone Repository ke WSL 🖇️

Masuk ke folder tempat menyimpan proyek:
```bash
cd ~
```
Clone repository yang sudah dibuat:
```bash
git clone git@github.com:username/project-wsl.git
```
Gantilah `username` dengan akun GitHub kamu.

Masuk ke folder repository:
```bash
cd project-wsl
```

---

# 🔹 7. Menggunakan Git di WSL ⚙️

## ✅ a. Buat File Baru
```bash
echo "Hello WSL" > hello.txt
```

## ✅ b. Tambahkan ke Git
```bash
git add .
```

## ✅ c. Commit Perubahan
```bash
git commit -m "Menambahkan file hello.txt"
```

## ✅ d. Kirim ke GitHub
```bash
git push origin main
```
Sekarang file **hello.txt** sudah diunggah ke GitHub! 🚀

---

# 🔹 8. Instalasi Zsh dan Oh My Zsh 🐚

Agar terminal lebih menarik, kita bisa menggunakan **Zsh** dan **Oh My Zsh**.

## ✅ a. Instal Zsh
```bash
sudo apt install zsh -y
```

Jadikan Zsh sebagai shell default:
```bash
chsh -s $(which zsh)
```
Keluar dan masuk kembali ke WSL untuk melihat perubahan.

## ✅ b. Instal Oh My Zsh
Jalankan perintah ini:
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
Sekarang terminal kamu lebih keren! 😎

---

# 🎯 Kesimpulan

✅ Membuat akun dan repository GitHub
✅ Menginstal WSL dan Git di Windows
✅ Menghubungkan GitHub dengan SSH Key
✅ Menggunakan Git di WSL untuk mengelola kode
✅ Menginstal Zsh dan Oh My Zsh

Sekarang kamu siap menggunakan GitHub dengan WSL secara profesional! 🚀🔥




---

```masih dalam pengembangan ```
```sama masih cari bakat```

### 🎮
<p align="center">
  <img width="200px" src="https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExaWNsOWo3N3RpbHJ0cTl3cjE1NHg2ajhsbjlvamcwb29veTlwOXJ4aSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/11lxCeKo6cHkJy/giphy.gif">
</p>
