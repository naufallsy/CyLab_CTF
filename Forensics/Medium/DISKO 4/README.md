<div align="center">

# 🚩 Write-Up: DISKO 4

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
| **Challenge Name** | DISKO 4 |

### 📝 Description
> *"Can you find the flag in this disk image? This time I deleted the file! Let see you get it now! Download the disk image here.
> 
>HINT:
> 1. How would you look for deleted files?
."*
---

## 🔍 Step 1: Reconnaissance & Analysis

Pada tantangan ini, kita diberikan file berupa dd.gz.

Langkah awal analisis:
1. Ekstrak isi file zip dengan perintah: gunzip disko-4.dd.gz
2. Cek isi tabel partisi dengan perintah: mmls disko-3.dd, hasilnya kosong yang berarti berisi partisi tunggal
3. Lalu gunakan perintah: fls -r -d disko-4.dd untuk melihat daftar file dan direktori (bahkan yang sudah terhapus)
parameter -r berarti memerintahkan fls untuk masuk ke dalam semua sub-direktori atau folder secara otomatis dari tingkat paling atas (root) sampai ke dalam-dalamnya
parameter -d berarti menunjukkan file yang sudah terhapus
4. Terdapat file yang bernama:
log/messages dengan alamat 522629
log/dont-delete.gz dengan alamat 532021
6. Ambil file log/dont-delete tadi dengan perintah: icat disko-4.dd 532021 > dont-delete.gz, 532021 merupakan alamat file yang akan kita ambil 
7. Ekstrak file yang barusan kita ambil (dont-delete.gz) dengan perintah: gunzip dont-delete.gz
8. Buka isi file dont-delete dengan perintah: cat dont-delete
┌──(kali㉿kali)-[~/Downloads]
└─$ cat dont-delete 
Here is your flag
academy{d3l_d0n7_h1d3_w3ll_d257c742}

FLAG: academy{d3l_d0n7_h1d3_w3ll_d257c742}
