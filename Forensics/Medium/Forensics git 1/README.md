<div align="center">

# 🚩 Write-Up: Forensics git 1

![Category](https://img.shields.io/badge/Category-Forensics-blue?style=for-the-badge&logo=target)
![Platform](https://img.shields.io/badge/Platform-CyLab_Academy-red?style=for-the-badge&logo=security)
![Difficulty](https://img.shields.io/badge/Difficulty-Medium-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Solved-success?style=for-the-badge)

</div>

---

## 📌 Challenge Overview

| Property | Value |
| :--- | :--- |
| **Platform** | CyLab Security Academy |
| **Category** | Forensics |
| **Difficulty** | Easy |
| **Challenge Name** | Forensics git 1 |

### 📝 Description
> *"Can you find the flag in this disk image? Download the disk image here.
> 
>HINT:
> 1. How can you checkout the files of a previous commit?
."*
---

## 🔍 Step 1: Reconnaissance & Analysis

Pada tantangan ini, kita diberikan file berupa img.gz.

Langkah awal analisis:
1. Ekstrak isi file zip dengan perintah: gunzip disk.img.gz
   
2. Cek partisi dengan perintah: mmls disk.img
  Terdapat banyak partisi, cek langsung partisi linux 004 dengan inode: 1140736
  
3. Cek isi folder .git menggunakan perintah: fls -o 1140736 -r disk.img
   Lalu telusuri folder home/ctf-player/Code/secrets/.git

4. Telusuri folder .git dengan perintah: fls -o 1140736 disk.img 65662
   
5. Telusuri folder log dengan perintah: fls -o 1140736 disk.img 65705
   <img width="277" height="86" alt="image" src="https://github.com/user-attachments/assets/c64858f9-6b50-40c0-9741-2cb21c6e81cc" />

7. Simpan isi HEAD dan refs dengan perintah:
   HEAD: icat -o 1140736 disk.img 65706 > git_log_head
   refs: icat -o 1140736 disk.img 65709 > git_log_master 
   
9. Lalu didapatkan petunjuk bahwa commit:
   add: 2a25cc4
   remove: 852b30

10. Lanjut periksa isi folder objects di dalam folder .git dengan perintah: fls -o 1140736 disk.img 65689
    
11. Menelusuri folder objek 2a di dalam direktori objects (inode 65698) untuk mencari file objek commit pertama dengan perintah: fls -o 1140736 disk.img 65698
    Ditemukan file objek commit dengan inode 65699.
    
12. Karena objek Git disimpan dalam format kompresi zlib, ekstrak dan dekompresi objek commit tersebut menggunakan Python untuk melihat tree-nya dengan perintah: icat -o 1140736 disk.img 65699 | python3 -c "import zlib, sys; sys.stdout.buffer.write(zlib.decompress(sys.stdin.buffer.read()))"
    Dari sini kita mendapatkan hash tree yaitu 34670eb2b45b4e90de5bf107d8a3b1fef8a4f846.
    
13. Periksa folder objek 34 (inode 65696) untuk menemukan file tree (inode 65697), lalu dekompresi isinya dengan perintah: icat -o 1140736 disk.img 65697 | python3 -c "import zlib, sys; sys.stdout.buffer.write(zlib.decompress(sys.stdin.buffer.read()))"
    Hasil dekompresi menunjukkan nama file flag.txt beserta referensi hash blob-nya yang mengarah ke folder 86.

14. Periksa folder objek 86 (inode 65692) untuk menemukan file blob milik flag.txt (inode 65693) dengan perintah: fls -o 1140736 disk.img 65692

15. Ekstrak dan dekompresi file blob tersebut untuk membaca isi file yang telah dihapus dengan perintah: icat -o 1140736 disk.img 65693 | zlib-flate -uncompress

    
FLAG: academy{g17_r3m3mb3r5_d4ddf904}
