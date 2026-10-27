<div align="center">

# 🚩 Write-Up: Information

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
| **Challenge Name** | Information |

### 📝 Description
> *"Files can always be changed in a secret way. Can you find the flag? cat.jpg

>HINT:
> 1. Look at the details of the file
> 2. Make sure to submit the flag as academy{XXXXX}
."*
---

## 🔍 Step 1: Reconnaissance & Analysis

Pada tantangan ini, kita diberikan challenge dengan format jpg.

Langkah awal analisis:
1. Cek metadata file dengan menggunakan perintah: exiftool cat.jph
2. Terdapat kode enkripsi dengan base64, lakukan decrypt


FLAG: academy{the_m3tadata_1s_modified}
