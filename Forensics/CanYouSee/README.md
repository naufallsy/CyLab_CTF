<div align="center">

# 🚩 Write-Up: CanYouSee

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
| **Challenge Name** | CanYouSee |

### 📝 Description
> *"How about some hide and seek?

Download this file here.

> 
>HINT:
> 1. How can you view the information about the picture?
> 2. If something isn't in the expected form, maybe it deserves attention?
."*
---

## 🔍 Step 1: Reconnaissance & Analysis

Pada tantangan ini, kita diberikan challenge berupa zip.

Langkah awal analisis:
1. Ekstrak file zip tersebut dengan perintah: unzip unknown.zip lalu akan menjadi file ukn_reality.jpg
2. Cek metadata ukn_reality.jpg dengan perintah: exiftool ukn_reality.jpg
3. Terdapat kode enkripsi base64, lakukan decrypt

FLAG: academy{ME74D47A_HIDD3N_927183b3}
