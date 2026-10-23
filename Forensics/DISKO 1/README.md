<div align="center">

# 🚩 Write-Up: DISKO 1

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
| **Challenge Name** | DISKO 1 |

### 📝 Description
> *"Can you find the flag in this disk image?

Download the disk image here
.
> 
>HINT:
> 1. Maybe Strings could help? If only there was a way to do that?
."*
---

## 🔍 Step 1: Reconnaissance & Analysis

Pada tantangan ini, kita diberikan file berupa zip.

Langkah awal analisis:
1. Ekstrak isi file zip dengan perintah: gunzip disko-1.dd.gz
2. Cari kata kunci flag dengan string, perintah: string disko-1.dd | grep -i "aca"

FLAG: academy{1t5_ju5t_4_5tr1n9_19d7626c}
