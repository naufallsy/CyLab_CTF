<div align="center">

# 🚩 Write-Up: Riddle Registry

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
| **Challenge Name** | Riddle Registry |

### 📝 Description
> *"Hi, intrepid investigator! 📄🔍 You've stumbled upon a peculiar PDF filled with what seems like nothing more than garbled nonsense. But beware! Not everything is as it appears. Amidst the chaos lies a hidden treasure—an elusive flag waiting to be uncovered. Find the PDF file here Hidden Confidential Document
and uncover the flag within the metadata.
> 
>HINT:
> 1. Don't be fooled by the visible text; it’s just a decoy!
> 2. Look beyond the surface for hidden clues
."*
---

## 🔍 Step 1: Reconnaissance & Analysis

Pada tantangan ini, kita diberikan file berupa pdf.

Langkah awal analisis:
1. Memeriksa isi file menggunakan perintah exiftool
2. Terdapat kode enkripsi base 64
3. Decrypt kode enkripsi base 64 di Cyber Chef

FLAG: academy{puzzl3d_m3tadata_f0und!_3cc7cea9}

```text
01000011 01011001 01001100 01000001 01000010 ...
