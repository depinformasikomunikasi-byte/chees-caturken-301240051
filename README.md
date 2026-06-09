# ♟️ Chess Adversarial AI

> **Tugas 10 — Pencarian Adversarial (Game Playing)**  
> Mata Kuliah Kecerdasan Buatan | S1 Teknik Informatika  
> Muhammad Fadillah Ramadhan — 301240051

![Chess AI Demo](https://img.shields.io/badge/Status-Ready-success?style=flat-square)
![Algorithm](https://img.shields.io/badge/Algorithm-Minimax%20%2B%20Alpha--Beta-7c6af7?style=flat-square)
![Tech](https://img.shields.io/badge/Tech-HTML%20%2B%20CSS%20%2B%20JS-f59e0b?style=flat-square)
![No Dependencies](https://img.shields.io/badge/Dependencies-Zero-10b981?style=flat-square)

---

## 🔗 Demo & Repository

| | Link |
|---|---|
| 🌐 **Live Demo** | `https://chess-ai.namaanda.my.id` *(ganti dengan domain kamu)* |
| 📁 **Repository** | `https://github.com/username/adversarial-search-301240051` |

---

## 📋 Deskripsi Project

Aplikasi web interaktif permainan **Catur 8×8 lengkap** dengan bot AI menggunakan algoritma **Minimax** dan **Alpha-Beta Pruning**. Dibuat sebagai implementasi konsep Adversarial Search dalam Kecerdasan Buatan.

Bot AI mampu:
- Mengevaluasi ribuan kemungkinan langkah ke depan
- Memilih langkah terbaik secara optimal
- Memangkas cabang game tree yang tidak relevan (Alpha-Beta)
- Mempertimbangkan nilai material + posisi bidak (Piece-Square Tables)

---

## ✅ Fitur Lengkap

### Fitur Wajib
| No | Fitur | Status |
|---|---|---|
| 1 | Human vs AI — Minimax Algorithm | ✅ |
| 2 | Alpha-Beta Pruning sebagai optimasi Minimax | ✅ |
| 3 | Visualisasi Game Tree (3 level kedalaman) | ✅ |
| 4 | Counter node dievaluasi Minimax vs Alpha-Beta | ✅ |
| 5 | Toggle: Minimax murni vs Minimax + Alpha-Beta | ✅ |
| 6 | Pengaturan kedalaman pencarian (depth 1–4) | ✅ |
| 7 | Indikator giliran & status permainan | ✅ |
| 8 | Tampilan responsif (desktop & mobile) | ✅ |

### Fitur Bonus
| No | Fitur | Status |
|---|---|---|
| 9 | Human vs Human mode | ✅ Bonus +5 |
| 10 | Highlight langkah AI + node dipangkas | ✅ Bonus +5 |

### Fitur Tambahan
- ♟️ Semua aturan catur: castling, en passant, promosi pion
- ↩️ Undo langkah
- ⇅ Flip board
- 📊 Riwayat langkah (notasi algebraik)
- 🏆 Skor menang/seri/kalah
- 📐 Pseudocode algoritma aktif secara real-time
- 💡 Bidak SVG kustom — putih krem vs hitam gelap, jelas dan kontras

---

## 🧠 Algoritma

### Minimax
```
function minimax(board, depth, isMax):
  if depth == 0 or gameOver:
    return evaluate(board)

  if isMax:
    best = -∞
    for move in legalMoves(board):
      val = minimax(apply(move), depth-1, False)
      best = max(best, val)
    return best
  else:
    best = +∞
    for move in legalMoves(board):
      val = minimax(apply(move), depth-1, True)
      best = min(best, val)
    return best
```

### Alpha-Beta Pruning
```
function alphabeta(board, depth, α, β, isMax):
  if depth == 0 or gameOver:
    return evaluate(board)

  if isMax:
    for move in legalMoves(board):
      val = alphabeta(apply(move), depth-1, α, β, False)
      α = max(α, val)
      if β ≤ α: break  # β-cutoff (pangkas)
    return α
  else:
    for move in legalMoves(board):
      val = alphabeta(apply(move), depth-1, α, β, True)
      β = min(β, val)
      if β ≤ α: break  # α-cutoff (pangkas)
    return β
```

### Fungsi Evaluasi
```
evaluate(board) = Σ (nilai_material + nilai_posisi) untuk semua bidak

Nilai material:
  Pion   = 100   Kuda  = 320   Gajah = 330
  Benteng = 500  Ratu  = 900   Raja  = 20000

Nilai posisi: Piece-Square Tables (PST)
  Mendorong AI untuk mengontrol pusat, mengembangkan bidak,
  dan menempatkan bidak di posisi strategis.
```

---

## 🚀 Cara Menjalankan

### Langsung di Browser (Paling Mudah)
```
1. Download / clone repository ini
2. Double-click file index.html
3. Buka di browser — selesai! ✅
```
> Tidak butuh server, tidak butuh install apapun.

### Atau via Local Server
```bash
# Python (sudah terinstall di kebanyakan komputer)
python -m http.server 8000

# Buka browser → http://localhost:8000
```

### Deploy ke Internet
```bash
# 1. Push ke GitHub
git init
git add .
git commit -m "Chess Adversarial AI"
git remote add origin https://github.com/username/adversarial-search-301240051
git push -u origin main

# 2. Deploy ke Netlify
# - Buka netlify.com
# - Drag & drop folder ini
# - Dapat link publik otomatis

# 3. Arahkan domain .my.id ke Netlify
# - Beli domain .my.id di Niagahoster
# - Tambahkan custom domain di Netlify
```

---

## 🗂️ Struktur File

```
adversarial-search-301240051/
│
├── index.html        ← Seluruh aplikasi (HTML + CSS + JS)
└── README.md         ← Dokumentasi ini
```

> Satu file HTML saja — zero dependencies, zero backend, zero framework.

---

## 🛠️ Stack Teknologi

| Layer | Teknologi |
|---|---|
| Tampilan | HTML5 + CSS3 (CSS Grid, CSS Variables) |
| Logika | Vanilla JavaScript (ES6+) |
| Bidak | SVG kustom (inline, tidak butuh gambar eksternal) |
| Font | Google Fonts (Space Mono + Sora) |
| Hosting | Netlify / GitHub Pages + domain .my.id |
| Backend | ❌ Tidak ada (pure frontend) |
| Library | ❌ Zero dependencies |

---

## 📊 Perbandingan Performa Algoritma

| Metrik | Minimax | Alpha-Beta Pruning |
|---|---|---|
| Node dievaluasi (depth 3) | ~5.000–15.000 | ~800–3.000 |
| Node dipangkas | 0 | 60–80% dari total |
| Efisiensi | Baseline | **~70% lebih efisien** |
| Kualitas keputusan | Optimal | **Identik dengan Minimax** |
| Kompleksitas waktu | O(b^d) | O(b^(d/2)) terbaik |

> Alpha-Beta Pruning menghasilkan keputusan yang **sama dengan Minimax**, namun dengan jauh lebih sedikit node yang dievaluasi.

---

## 📸 Screenshot

*(Tambahkan screenshot aplikasi di sini setelah deploy)*

```
Cara tambah screenshot:
1. Screenshot aplikasi yang berjalan
2. Simpan di folder /screenshots/
3. Ganti teks ini dengan: ![Screenshot](screenshots/demo.png)
```

---

## 📚 Referensi

1. Russell, S. & Norvig, P. (2020). *Artificial Intelligence: A Modern Approach* (4th ed.). Pearson.
2. Shannon, C. (1950). Programming a Computer for Playing Chess. *Philosophical Magazine*, 41(314), 256–275.
3. Knuth, D. E. & Moore, R. W. (1975). An Analysis of Alpha-Beta Pruning. *Artificial Intelligence*, 6(4), 293–326.
4. Millington, I. & Funge, J. (2009). *Artificial Intelligence for Games* (2nd ed.). Morgan Kaufmann.
5. Laramée, F. D. (2000). Chess Programming Part IV: Basic Search. *GameDev.net*.

---

## 👤 Identitas

| | |
|---|---|
| **Nama** | Muhammad Fadillah Ramadhan |
| **NIM** | 301240051 |
| **Mata Kuliah** | Kecerdasan Buatan |
| **Topik** | Pencarian Adversarial (Game Playing) |
| **Tugas** | Tugas 10 — Project Simulasi |

# chees-caturken-301240051
