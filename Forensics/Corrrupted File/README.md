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
> "*Flag: 
---

## 🔍 Step 1: Reconnaissance & Analysis

Pada tantangan ini, kita diberikan data berupa deretan angka biner (`0` dan `1`).

Langkah awal analisis:
1. Memeriksa isi file
2. Copy semua teks ASCII untuk didecrypt di CyberChef
3. Isi teks berubah menjadi gambar yang terdapat flag

FLAG: academy{h1dd3n_1n_th3_b1n4ry_5a7375c5}

```text
01000011 01011001 01001100 01000001 01000010 ...
