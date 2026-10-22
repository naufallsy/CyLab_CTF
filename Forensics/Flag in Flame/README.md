<div align="center">

# 🚩 Write-Up: Flag in Flame

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
| **Challenge Name** | Flag in Flame |

### 📝 Description
> *"The SOC team discovered a suspiciously large log file after a recent breach. When they opened it, they found an enormous block of encoded text instead of typical logs. Could there be something hidden within? Your mission is to inspect the resulting file and reveal the real purpose of it. The team is relying on your skills to uncover any concealed information within this unusual log. Download the encoded data here: Logs Data
. Be prepared—the file is large, and examining it thoroughly is crucial.
> 
>HINT:
> 1. Use base64 to decode the data and generate the image file.
."*
---

## 🔍 Step 1: Reconnaissance & Analysis

Pada tantangan ini, kita diberikan file berupa txt.

Langkah awal analisis:
1. Memeriksa isi file menggunakan perintah file
2. Terdapat kode enkripsi base 64 yang sangat banyak
3. Decode base64 dan generate gambar menggunakan perintah : base64 -d logs.txt > flag.png
4. Buka gambar dan ada enkripsi code dari Hex
5. Salin tulisan menggunakan perintah tesseract flag.png result
6. Decrypt hasil decode dan ketemu flagnya

FLAG: academy{forensics_analysis_is_amazing_2043dbd1}
