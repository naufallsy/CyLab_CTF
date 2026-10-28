<div align="center">

# 🚩 Write-Up: Forensics git 0

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
| **Challenge Name** | Forensics git 0 |

### 📝 Description
> *"Can you find the flag in this disk image? Download the disk image here.
> 
>HINT:
> 1. How can you extract the directory from the disk image?
."*
---

## 🔍 Step 1: Reconnaissance & Analysis

Pada tantangan ini, kita diberikan file berupa img.gz.

Langkah awal analisis:
1. Ekstrak isi file zip dengan perintah: gunzip disk.img.gz
   
2. Cek partisi dengan perintah: mmls disk.img
  Terdapat banyak partisi, cek langsung partisi linux 004 dengan inode: 1140736
  
3. Cek isi file menggunakan perintah: fls -o 1140736 -r disk.img | grep -i "messages"
  Cek messages untuk mencari petunjuk

4. Simpan isi file messages menggunakan perintah: icat -o 1140736 disk.img 65279 > messages (65279 merupakan inode dari messages, cek menggunakan perintah nomor 3)
   Terdapat petunjuk berupa "ctf-player"

5. Cek isi file menggunakan perintah: fls -o 1140736 -r disk.img | grep -i "ctf-player"
   Ternyata ada
   
7. Cek lagi isi dari ctf-player menggunakan perintah: fls -o 1140736 -r disk.img 64771
   Terdapat file note.txt yang patut kita lihat 
   
8. Ternyata di dalam file note.txt terdapat petunjuk berupa: The CyLab Academy flag format is 'academy{}' where there is some leetspeak phrase in between the curly braces

9. Lanjut periksa isi file COMMIT_EDITMSG di dalam folder ctf-player tadi menggunakan perintah: icat -o 1140736 disk.img 65700 > commit
   Setelah di buka ternyata isinya: Wrap this phrase in the flag format: g17_1n_7h3_d15k_041217d8

Karena di petunjuk tadi menunjukkan format flag adalah 'academy{}', maka kita masukkan flag tersebut ke dalam academy, menjadi academy{g17_1n_7h3_d15k_041217d8}

FLAG: academy{g17_1n_7h3_d15k_041217d8}
