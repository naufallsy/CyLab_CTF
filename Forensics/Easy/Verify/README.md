<div align="center">

# 🚩 Write-Up: Verify

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
| **Challenge Name** | Verify |

### 📝 Description
> *"People keep trying to trick my players with imitation flags. I want to make sure they get the real thing! I'm going to provide the SHA-256 hash and a decrypt script to help you know that my flags are legitimate. ssh -p 37989 ctf-player@xebec.cylabacademy.net
Using the password 13792798. Accept the fingerprint with yes, and ls once connected to begin. Remember, in a shell, passwords are hidden!
Checksum: bf7701262e3fce45531b13d9866fb0913847a669823064aec1f60be7c2591ba8
To decrypt the file once you've verified the hash, run ./decrypt.sh files/<file>.

> 
>HINT:
> 1. Checksums let you tell if a file is complete and from the original distributor. If the hash doesn't match, it's a different file.
> 2. You can create a SHA checksum of a file with sha256sum <file> or all files in a directory with sha256sum <directory>/*.
> 3. Remember you can pipe the output of one command to another with |. Try practicing with the 'First Grep' challenge if you're stuck!
."*
---

## 🔍 Step 1: Reconnaissance & Analysis

Pada tantangan ini, kita diberikan challenge dengan connect menggunakan ssh

Langkah awal analisis:
1. Connect terlebih dahulu dengan perintah: ssh -p 37989 ctf-player@xebec.cylabacademy.net dan passwordnya: 13792798
2. Lalu verifikasi nilai checksum semua file dengan perintah: sha256sum files/*
3. Cari nama file yang nilai sha256 nya cocok dengan checksum: bf7701262e3fce45531b13d9866fb0913847a669823064aec1f60be7c2591ba8 dengan perintah: sha256sum files/* | grep "bf7701262e3fce45531b13d9866fb0913847a669823064aec1f60be7c2591ba8"
4. Lalu decrypt file dengan menggunakan perintah: ./decrypt.sh files/b6225255 (files/b6225255 merupakan nama file yang cocok dengan checksum)

FLAG: academy{trust_but_verify_b6225255}
