<div align="center">

# 🚩 Write-Up: Scan Surprise

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
| **Challenge Name** | Scan Surprise |

### 📝 Description
> *"I've gotten bored of handing out flags as text. Wouldn't it be cool if they were an image instead?
You can download the challenge files here:
challenge.zip

> 
>HINT:
> 1. QR codes are a way of encoding data. While they're most known for storing URLs, they can store other things too.
> 2. Mobile phones have included native QR code scanners in their cameras since version 8 (Oreo) and iOS 11
> 3. If you don't have access to a phone, you can also use zbar-tools to convert an image to text
."*
---

## 🔍 Step 1: Reconnaissance & Analysis

Pada tantangan ini, kita diberikan challenge berupa connect ke ssh.

Langkah awal analisis:
1. Sambungkan ke ssh dengan perintah: ssh -p 37989 ctf-player@xebec.cylabacademy.net dan password: 647e170e
2. Cek isi file dengan perintah: ls, terdapat file dengan nama flag.png
3. Sesuai dengan hint, gunakan perintah: zbarimg flag.png untuk mengubah gambar (QR Code) menjadi teks

FLAG: academy{p33k_@_b00_36769c4b}
