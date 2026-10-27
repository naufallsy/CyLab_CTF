<div align="center">

# 🚩 Write-Up: DISKO 3

![Category](https://img.shields.io/badge/Category-Forensics-blue?style=for-the-badge&logo=target)
![Platform](https://img.shields.io/badge/Platform-CyLab_Academy-red?style=for-the-badge&logo=security)
![Difficulty](https://img.shields.io/badge/Difficulty-Medium-orange?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Solved-success?style=for-the-badge)

</div>

---

## 📌 Challenge Overview

| Property | Value |
| :--- | :--- |
| **Platform** | CyLab Security Academy |
| **Category** | Forensics |
| **Difficulty** | Medium |
| **Challenge Name** | DISKO 3 |

### 📝 Description
> *"Can you find the flag in this disk image? This time, its not as plain as you think it is! Download the disk image here.
> 
>HINT:
> 1. How will you search and extract files in a partition?
."*
---

## 🔍 Step 1: Reconnaissance & Analysis

Pada tantangan ini, kita diberikan file berupa dd.gz.

Langkah awal analisis:
1. Ekstrak isi file zip dengan perintah: gunzip disko-3.dd.gz
2. Cek isi tabel partisi dengan perintah: mmls disko-3.dd, hasilnya kosong yang berarti berisi partisi tunggal
3. Lalu gunakan perintah: fls -r disko-3.dd untuk melihat daftar file dan direktori
parameter -r berarti memerintahkan fls untuk masuk ke dalam semua sub-direktori atau folder secara otomatis dari tingkat paling atas (root) sampai ke dalam-dalamnya
4. Terdapat file yang bernama flag.gz dengan alamat 522628
5. Ambil file flag.gz tadi dengan perintah: icat disko-3.dd 522628 > flag.gz, 522628 merupakan alamat file yang akan kita ambil 
6. Ekstrak file yang barusan kita ambil (flag.gz) dengan perintah: gunzip flag.gz
7. Buka isi file flag dengan perintah: cat flag
┌──(kali㉿kali)-[~/Downloads]
└─$ cat flag              
Here is your flag
academy{n3v3r_z1p_2_h1d3_2f899900}

FLAG: academy{n3v3r_z1p_2_h1d3_2f899900}
