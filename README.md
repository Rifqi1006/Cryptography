# 🔐 Shamir's No-Key Protocol

Repository ini merealisasikan skema **Shamir's No-Key Protocol**, sebuah protokol kriptografi yang memungkinkan pertukaran kunci rahasia antara dua entitas **tanpa perlu berbagi kunci sebelumnya** melalui saluran yang tidak aman. Protokol ini mengandalkan kompleksitas komputasi **logaritma diskrit** dalam grup modular untuk menjaga keamanan distribusi kunci.

---

## 🎯 Tujuan
- Menunjukkan bagaimana **Shamir's No-Key Protocol** dapat diimplementasikan secara praktis menggunakan `Python`.  
- Mengevaluasi **keamanan** dan **efisiensi komputasi** berdasarkan ukuran bilangan prima (`p`).  

---

## 📜 Skema Protokol
Protokol mengikuti **tiga fase utama**:

### 1. 🔑 Inisialisasi
- Kedua pihak menyepakati bilangan prima besar `p` (bersifat publik).  
- Setiap pihak memilih kunci rahasia:  
  - A memilih `a` dengan syarat `1 ≤ a ≤ p-2` dan `gcd(a, p-1) = 1`.  
  - B memilih `b` dengan syarat `1 ≤ b ≤ p-2` dan `gcd(b, p-1) = 1`.  
- Hitung invers modular:  
  - `a_inv ≡ a⁻¹ mod (p-1)`  
  - `b_inv ≡ b⁻¹ mod (p-1)`

---

### 2. 📩 Pertukaran Pesan
1. **Langkah 1**: A → B :  
   `A1 ≡ K^a mod p`  
2. **Langkah 2**: B → A :  
   `B1 ≡ (A1)^b mod p ≡ K^(a*b) mod p`  
3. **Langkah 3**: A → B :  
   `A2 ≡ (B1)^(a_inv) mod p ≡ K^b mod p`  

---

### 3. 🔓 Pemulihan Kunci
- B menghitung kembali kunci:  
  `K ≡ (A2)^(b_inv) mod p`  

---

## 🛠️ Teknologi dan Peralatan
- **Bahasa Pemrograman**: `Python 3`  
- **Pustaka Kriptografi**: `Crypto.Util.number` → pembangkitan bilangan prima, uji primalitas, invers modular
- **Library Random**: `random` → pembangkitan kunci rahasia secara acak
- **Sistem & Utility**: `sys` → pengaturan sistem dan kompatibilitas eksekusi  
- **Pustaka Matematika**: `sympy` → komputasi simbolik, verifikasi koprima  
- **Random Generator**: `random` → pembangkitan kunci rahasia  
- **Pengukuran Waktu**: `time` → analisis performa komputasi  
- **Platform**: Google Colab  

---

## 🧪 Penelitian dan Eksperimen
Simulasi protokol dilakukan dengan tiga ukuran bilangan prima:  

- `512-bit`  
- `1024-bit`  
- `2048-bit`  

📌 **Hasil Eksperimen**:
- Protokol berhasil memulihkan kunci dengan **akurasi 100%** pada semua ukuran parameter.  
- Waktu komputasi meningkat seiring dengan ukuran parameter, sesuai dengan kompleksitas operasi modular.  
