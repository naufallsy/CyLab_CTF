<div align="center">

# 🚩 Write-Up: RED

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
| **Challenge Name** | RED |

### 📝 Description
> *"RED, RED, RED, RED Download the image: red.png
.
> 
>HINT:
> 1. The picture seems pure, but is it though?
> 2. Red?Ged?Bed?Aed?
> 3. Check whatever Facebook is called now.
."*
---

## 🔍 Step 1: Reconnaissance & Analysis

Pada tantangan ini, kita diberikan file berupa png.

Langkah awal analisis:
1. Cek metadata dengan perintah: exiftool red.png
2. Deteksi data tersembunyi di Least Significant Bits (LSB) pada file PNG dengan perintah: zsteg red.png
3. Terdapat kode enkripsi dalam base64, lakukan decrypt

FLAG: academy{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}
