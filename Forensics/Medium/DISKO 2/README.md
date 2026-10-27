<div align="center">

# 🚩 Write-Up: DISKO 2

![Category](https://img.shields.io/badge/Category-Forensics-blue?style=for-the-badge&logo=target)
![Platform](https://img.shields.io/badge/Platform-CyLab_Academy-red?style=for-the-badge&logo=security)
![Difficulty](https://img.shields.io/badge/Difficulty-Medium-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Solved-success?style=for-the-badge)

</div>

---

## 📌 Challenge Overview

| Property | Value |
| :--- | :--- |
| **Platform** | CyLab Security Academy |
| **Category** | Forensics |
| **Difficulty** | Easy |
| **Challenge Name** | DISKO 2 |

### 📝 Description
> *"Can you find the flag in this disk image? The right one is Linux! One wrong step and its all gone! Download the disk image here.
> 
>HINT:
> 1. How can you extract/isolate a partition?
."*
---

## 🔍 Step 1: Reconnaissance & Analysis

Pada tantangan ini, kita diberikan file berupa dd.gz.

Langkah awal analisis:
1. Ekstrak isi file zip dengan perintah: gunzip disko-2.dd.gz
2. Lihat tabel partisi dengan perintah: mmls disko-2.dd, muncul:
┌──(kali㉿kali)-[~/Downloads]
└─$ mmls disko-2.dd 
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000053247   0000051200   Linux (0x83)
003:  000:001   0000053248   0000118783   0000065536   Win95 FAT32 (0x0b)
004:  -------   0000118784   0000204799   0000086016   Unallocated

3. Karena sudah diberi clue yang kita cari itu Linux maka kita isolasi Linux dengan perintah: dd if=disko-2.dd of=partisi_linux.img bs=512 skip=2048 (skip=2048, 2048 merupakan angka awal atau start dari hasil mmls pada linux)
4. Cari flag dengan menggunakan perintah: strings partisi_linux.img | grep -i "academy"
5. Karena hasilnya sangat banyak maka kita cari apa yang menonjol dengan perintah: strings partisi_linux.img | grep -oE "academy\{[^}]+\}" | sort | uniq -c | sort -nr
Penjelasan perintah:
-o (only-matching): Hanya mencetak bagian teks yang cocok saja, mengabaikan kalimat panjang di sebelah kiri/kanannya.
-E (extended-regexp): Mengizinkan penggunaan aturan Regex tingkat lanjut.
-"academy\{[^}]+\}": Pola pencariannya:
    academy = Harus ada kata "academy".
    \{ dan \} = Mencari kurung kurawal asli { dan }.
    [^}] = Artinya "karakter apa saja selain kurung kurawal tutup (})".
    + = Berarti karakter di dalam kurung tersebut harus ada 1 atau lebih.
6. Outputnya:
┌──(kali㉿kali)-[~/Downloads]
└─$ strings partisi_linux.img | grep -oE "academy\{[^}]+\}" | sort | uniq -c | sort -nr
      2 academy{4_P4Rt_1t_i5_3d183cc0}
      1 academy{4_P4Rt_1t_i5_dcc30183}
      1 academy{4_P4Rt_1t_i5_dc38c310}
      1 academy{4_P4Rt_1t_i5_dc30318c}
      1 academy{4_P4Rt_1t_i5_d8cc3103}
      1 academy{4_P4Rt_1t_i5_d3013cc8}
      1 academy{4_P4Rt_1t_i5_d1cc3083}
      1 academy{4_P4Rt_1t_i5_d1803c3c}
      1 academy{4_P4Rt_1t_i5_d13380cc}
      1 academy{4_P4Rt_1t_i5_d13038cc}
      1 academy{4_P4Rt_1t_i5_cd83103c}
      1 academy{4_P4Rt_1t_i5_cd3c3108}
      1 academy{4_P4Rt_1t_i5_cc81330d}
      1 academy{4_P4Rt_1t_i5_cc338d01}
      1 academy{4_P4Rt_1t_i5_cc10d383}
      1 academy{4_P4Rt_1t_i5_cc0318d3}
      1 academy{4_P4Rt_1t_i5_c8d313c0}
      1 academy{4_P4Rt_1t_i5_c8d033c1}
      1 academy{4_P4Rt_1t_i5_c83c130d}
      1 academy{4_P4Rt_1t_i5_c81d30c3}
      1 academy{4_P4Rt_1t_i5_c803cd31}
      1 academy{4_P4Rt_1t_i5_c3cd1083}
      1 academy{4_P4Rt_1t_i5_c33c018d}
      1 academy{4_P4Rt_1t_i5_c31c30d8}
      1 academy{4_P4Rt_1t_i5_c3013c8d}
      1 academy{4_P4Rt_1t_i5_c1d308c3}
      1 academy{4_P4Rt_1t_i5_c1c833d0}
      1 academy{4_P4Rt_1t_i5_c1c0d833}
      1 academy{4_P4Rt_1t_i5_c138c3d0}
      1 academy{4_P4Rt_1t_i5_c1330dc8}
      1 academy{4_P4Rt_1t_i5_c0cd3813}
      1 academy{4_P4Rt_1t_i5_c03d31c8}
      1 academy{4_P4Rt_1t_i5_c038dc13}
      1 academy{4_P4Rt_1t_i5_c013c8d3}
      1 academy{4_P4Rt_1t_i5_8dc3103c}
      1 academy{4_P4Rt_1t_i5_8d3cc031}
      1 academy{4_P4Rt_1t_i5_8c3cd310}
      1 academy{4_P4Rt_1t_i5_8c3c3d10}
      1 academy{4_P4Rt_1t_i5_8c30d3c1}
      1 academy{4_P4Rt_1t_i5_83c1cd03}
      1 academy{4_P4Rt_1t_i5_81d3c0c3}
      1 academy{4_P4Rt_1t_i5_80cdc331}
      1 academy{4_P4Rt_1t_i5_3dc83c01}
      1 academy{4_P4Rt_1t_i5_3dc01c38}
      1 academy{4_P4Rt_1t_i5_3d8c01c3}
      1 academy{4_P4Rt_1t_i5_3d80cc31}
      1 academy{4_P4Rt_1t_i5_3d103cc8}
      1 academy{4_P4Rt_1t_i5_3cd381c0}
      1 academy{4_P4Rt_1t_i5_3ccd3018}
      1 academy{4_P4Rt_1t_i5_3ccd0138}
      1 academy{4_P4Rt_1t_i5_3cc8103d}
      1 academy{4_P4Rt_1t_i5_3cc30d18}
      1 academy{4_P4Rt_1t_i5_3cc138d0}
      1 academy{4_P4Rt_1t_i5_3c81c3d0}
      1 academy{4_P4Rt_1t_i5_3c38d10c}
      1 academy{4_P4Rt_1t_i5_3c13cd08}
      1 academy{4_P4Rt_1t_i5_38cd310c}
      1 academy{4_P4Rt_1t_i5_380d3cc1}
      1 academy{4_P4Rt_1t_i5_338cd0c1}
      1 academy{4_P4Rt_1t_i5_31c0dc83}
      1 academy{4_P4Rt_1t_i5_3130dcc8}
      1 academy{4_P4Rt_1t_i5_3103dc8c}
      1 academy{4_P4Rt_1t_i5_30dc8c13}
      1 academy{4_P4Rt_1t_i5_30dc13c8}
      1 academy{4_P4Rt_1t_i5_30d18c3c}
      1 academy{4_P4Rt_1t_i5_30c31cd8}
      1 academy{4_P4Rt_1t_i5_30831dcc}
      1 academy{4_P4Rt_1t_i5_303cdc81}
      1 academy{4_P4Rt_1t_i5_303c8dc1}
      1 academy{4_P4Rt_1t_i5_3018cc3d}
      1 academy{4_P4Rt_1t_i5_1d3c8c03}
      1 academy{4_P4Rt_1t_i5_1cc3d830}
      1 academy{4_P4Rt_1t_i5_1c3c0d83}
      1 academy{4_P4Rt_1t_i5_1c383dc0}
      1 academy{4_P4Rt_1t_i5_1c380dc3}
      1 academy{4_P4Rt_1t_i5_1c03d8c3}
      1 academy{4_P4Rt_1t_i5_183cc3d0}
      1 academy{4_P4Rt_1t_i5_13cdc380}
      1 academy{4_P4Rt_1t_i5_13cd803c}
      1 academy{4_P4Rt_1t_i5_13c3c08d}
      1 academy{4_P4Rt_1t_i5_133cc0d8}
      1 academy{4_P4Rt_1t_i5_1330ccd8}
      1 academy{4_P4Rt_1t_i5_130c8d3c}
      1 academy{4_P4Rt_1t_i5_108d33cc}
      1 academy{4_P4Rt_1t_i5_0cd318c3}
      1 academy{4_P4Rt_1t_i5_0c3c1d83}
      1 academy{4_P4Rt_1t_i5_0c31c3d8}
      1 academy{4_P4Rt_1t_i5_0c1d83c3}
      1 academy{4_P4Rt_1t_i5_0c1c83d3}
      1 academy{4_P4Rt_1t_i5_0c1c3d38}
      1 academy{4_P4Rt_1t_i5_0c13dc38}
      1 academy{4_P4Rt_1t_i5_0c13c3d8}
      1 academy{4_P4Rt_1t_i5_08c33dc1}
      1 academy{4_P4Rt_1t_i5_0833c1dc}
      1 academy{4_P4Rt_1t_i5_08313dcc}
      1 academy{4_P4Rt_1t_i5_081c33dc}
      1 academy{4_P4Rt_1t_i5_03dcc813}
      1 academy{4_P4Rt_1t_i5_03c31d8c}
      1 academy{4_P4Rt_1t_i5_038c13cd}
      1 academy{4_P4Rt_1t_i5_033c8d1c}
      1 academy{4_P4Rt_1t_i5_01c83c3d}
7. Terdapat flag yang muncul 2 kali, maka kita test flag tersebut dan benar
FLAG: 2 academy{4_P4Rt_1t_i5_3d183cc0}
