<div align="center">

# 🚩 Write-Up: Hidden in Plainsight

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
| **Challenge Name** | Hidden in Plainsight |

### 📝 Description
> *"You’re given a seemingly ordinary JPG image. Something is tucked away out of sight inside the file. Your task is to discover the hidden payload and extract the flag. Download the jpg image here
.
> 
>HINT:
> 1. Download the jpg image and read its metadata
."*
---

## 🔍 Step 1: Reconnaissance & Analysis

Pada tantangan ini, kita diberikan file berupa img.

Langkah awal analisis:
1. Memeriksa isi file menggunakan perintah exiftool
2. Terdapat kode enkripsi base 64
3. Decrypt kode enkripsi base 64 di Cyber Chef
4. Lalu akan muncul: steghide:cEF6endvcmQ=
5. Setelah itu lakukan perintah steghide --info untuk melihat apakah ada file tersembunyi
6. Ketika diminta memasukkan passpharse kita akan memasukkan pAzzword yang di mana pAzzword merupakan hasil decript dari steghide:cEF6endvcmQ=
7. Ternyata ada file tesembunyi bernama "flag.txt"
8. Extract file img,jpg menggunakan perintah steghide extract -sf img.jpg
9. Lihat isi file "flag.txt"

FLAG: academy{h1dd3n_1n_1m4g3_45cfe9c1}

