<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f8c7b6cc-48b4-4551-910c-92a249762898" /><div align="center">

# 🚩 Write-Up: Rouge Tower

![Category](https://img.shields.io/badge/Category-Forensics-blue?style=for-the-badge&logo=target)
![Platform](https://img.shields.io/badge/Platform-CyLab_Academy-red?style=for-the-badge&logo=security)
![Difficulty](https://img.shields.io/badge/Difficulty-Medium-orange?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Solved-success?style=for-the-badge)

</div>

---

## 📌 Challenge Overview

| Property | Value |
| :--- | :--- |
| **Platform** | CyLab Security Academy |
| **Category** | Forensics |
| **Difficulty** | Medium |
| **Challenge Name** | Rouge Tower |

### 📝 Description
> *"A suspicious cell tower has been detected in the network. Analyze the captured network traffic to identify the rogue tower, find the compromised device, and recover the exfiltrated flag. Download the network capture file: here.
> 
>HINT:
> 1. Look for unauthorized test network broadcasts on UDP port 55000
> 2. Find the device that connected to the rogue tower by checking HTTP User-Agent headers
> 3. The encryption key is derived from the victim device's IMSI
> 4. The exfiltrated data is split across multiple HTTP POST requests
."*
---

## 🔍 Step 1: Reconnaissance & Analysis

Pada tantangan ini, kita diberikan file berupa .pcap

Langkah awal analisis:
1. Cek trafic menggunakan filter udp di wireshark
   <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e63eae3e-28a6-4031-a052-6b8f2e523e19" />
  Catat CELLID: 94714

2. Cek perangkat yang terhubung dengan menggunakan filter http
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4012e6f7-6f5c-4633-b8f7-5b873fa6f2f6" />
  CELLID sudah cocok dengan yang kita temukan tadi, lalu catat IMSI nya
  IMSI: 310410725669651
3. Lalu gunakan perintah: tshark -r rogue_tower.pcap \
  -Y 'http.request.method == "POST"' \
  -T fields \
  -e frame.number \
  -e http.request.uri \
  -e http.file_data

  Untuk menemukan data eksfiltrasi (sesuai hint nomor 4)
  Hasilnya:
  55315a58556c786254
  45704142564644436d
  6c57416c355a615549
  4a51515a4462564653
  556c304456774a5153
  413d3d
  
4. Gabungkan lalu decrypt ke Base64, hasilnya: U1ZXUlxbTEpABVFDCmlWAl5ZaUIJQQZDbVFSUl0DVwJQSA==

5. Decrypt kode base64 tersebut dengan XOR, keynya menggunakan IMSI yang telah kita catat tadi
   <img width="1474" height="876" alt="image" src="https://github.com/user-attachments/assets/c4e20135-3481-4fd1-be0c-46220b9b8739" />

   IMSI yang digunakan hanya bagian belakang karena dari berbagai perangkat tadi kode awal IMSI tidak berubah dan hanya berubah di kode akhir

FLAG: academy{r0gu3_c3ll_t0w3r_dddd5b3b}
