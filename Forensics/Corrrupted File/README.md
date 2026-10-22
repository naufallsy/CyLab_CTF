<div align="center">

# 🚩 Write-Up: Corrupted File

![Category](https://img.shields.io/badge/Category-Forensics-blue?style=for-the-badge&logo=target)
![Platform](https://img.shields.io/badge/Platform-CyLab_Academy-red?style=for-the-badge&logo=security)
![Difficulty](https://img.shields.io/badge/Difficulty-Easy-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Solved-success?style=for-the-badge)

</div>

---

## 📌 Challenge Overview

| Property | Value |
| :--- | :--- |
| **Platform** | CyLab Security Academy |
| **Category** | Forensics |
| **Difficulty** | Easy |
| **Challenge Name** | Corrupted File |

### 📝 Description
> *"This file seems broken... or is it? Maybe a couple of bytes could make all the difference. Can you figure out how to bring it back to life? Download the file here
.
> 
>HINT:
> 1. Try checking the file’s header.
> 2. JPEG
> 3. Tools like xxd or hexdump can help you inspect and edit file bytes.
."*
---

## 🔍 Step 1: Reconnaissance & Analysis

Pada tantangan ini, kita diberikan file berupa txt.

Langkah awal analisis:
1. Memeriksa isi file menggunakan perintah: xxd file
2. Lalu karena diberi clude bahwa file asli merupakan JPEG maka kita ubah biner baris pertama di depan menjadi FF D8 menggunakan perintah: hexedit file
3. Setelah itu kita buka filenya dengan perintah: xdg-open file

FLAG: academy{r3st0r1ng_th3_by73s_69066302}
