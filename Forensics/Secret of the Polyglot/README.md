<div align="center">

# 🚩 Write-Up: Secret of the Polygot

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
| **Challenge Name** | Secret of the Polygot |

### 📝 Description
> *"The Network Operations Center (NOC) of your local institution picked up a suspicious file, they're getting conflicting information on what type of file it is. They've brought you in as an external expert to examine the file. Can you extract all the information from this strange file?
Download the suspicious file here.

>HINT:
> 1. This problem can be solved by just opening the file in different ways
."*
---

## 🔍 Step 1: Reconnaissance & Analysis

Pada tantangan ini, kita diberikan challenge dengan connect menggunakan ssh

Langkah awal analisis:
1. Cek isi pdf dan ternyata ada bagian belakang flag: 1n_pn9_&_pdf_96385309}
2. Lalu kita menggunakan perintah tesseract untuk membaca dan mengekstrak teks yang ada di dalam gambar: tesseract 
flag2of2-final.pdf stdout (stdout digunakan supaya langsung keluar di terminal outputnya)
3. Keluar bagian depan flag: academy(f1u3n7_

FLAG: academy{f1u3n7_1n_pn9_&_pdf_96385309}
