<div align="center">

# 🚩 Write-Up: Binary Digits

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
| **Challenge Name** | Binary Digits |

### 📝 Description
> *"Salin atau tulis deskripsi tantangan dari CyLab Security Academy di sini."*

---

## 🔍 Step 1: Reconnaissance & Analysis

Pada tantangan ini, kita diberikan data berupa deretan angka biner (`0` dan `1`).

Langkah awal analisis:
1. Memeriksa pola dan panjang data biner yang diberikan.
2. Mengelompokkan deretan biner menjadi per-8 bit (1 byte) untuk dikonversi ke karakter teks ASCII.

```text
01000011 01011001 01001100 01000001 01000010 ...
