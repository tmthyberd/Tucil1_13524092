# Tucil1 - Queens Game Solver (Brute Force)

**13524092 - Timothy Bernard Soeharto**

## Notes Penting

Pastikan berada di folder bin saat menjalankan main.exe karena fixed pathing ke folder input.
Pastikan juga queen.png berada di folder yang sama dengan main.exe, karena fixed pathing dan main.exe butuh queen.png saat save image.

## Deskripsi Program

Program ini merupakan solver untuk permainan Queens, yaitu permainan meletakkan sejumlah ratu pada papan berwarna sehingga memenuhi aturan berikut:

- Setiap ratu harus berada di warna yang berbeda
- Tidak ada dua ratu yang boleh berada di baris yang sama
- Tidak ada dua ratu yang boleh berada di kolom yang sama
- Tidak ada dua ratu yang boleh bersentuhan satu sama lain, termasuk secara diagonal (jarak 1 langkah)

Program menggunakan algoritma **brute force murni** dengan cara menghasilkan semua kemungkinan kombinasi posisi ratu secara rekursif dan memeriksa satu per satu apakah kombinasi tersebut valid.

Program mendukung dua jenis input:

- **Input teks**: file `.txt` berisi representasi karakter dari papan
- **Input gambar**: file `.png` atau `.jpg` berisi gambar papan berwarna

Setelah solusi ditemukan, program menampilkan waktu pencarian dan jumlah kombinasi yang diperiksa, lalu menawarkan opsi untuk menyimpan hasil dalam bentuk **file `.txt`** dan/atau **file gambar `.png`**.

---

## Requirements

### Bahasa & Runtime

- [Go](https://go.dev/dl/) versi **1.21** atau lebih baru

### External Package

- [`github.com/disintegration/imaging`](https://github.com/disintegration/imaging) — untuk resize dan overlay gambar ratu

### File Tambahan

- `queen.png` — gambar ikon ratu dengan background transparan, diletakkan di folder `src/`

### Struktur Folder

```
Tucil1_13524092/
├── src/
│   ├── main.go
│   ├── queen.png
│   ├── go.mod
│   └── go.sum
└── test/
    ├── input/
    │   └── (letakkan file input di sini)
    └── output/
        └── (hasil output akan tersimpan di sini)
```

---

## Instalasi

### 1. Clone / Download repository

```bash
git clone https://github.com/<username>/Tucil1_13524092.git
cd Tucil1_13524092/src
```

### 2. Inisialisasi Go module dan install dependency

```bash
go mod init tucil1
go get github.com/disintegration/imaging
```

### 3. Buat folder output

**Windows:**

```bash
mkdir ..\test\output
```

**Linux / Mac:**

```bash
mkdir -p ../test/output
```

---

## Kompilasi

### Windows

```bash
cd src
go build -o main.exe main.go
```

### Linux / Mac

```bash
cd src
go build -o main main.go
```

---

## Cara Menjalankan

### Menggunakan `go run` (tanpa kompilasi)

```bash
cd src
go run main.go
```

### Menggunakan hasil kompilasi

**Windows:**

```bash
.\main.exe
```

**Linux / Mac:**

```bash
./main
```

---

## Cara Penggunaan

### Input Teks

```
Input type (text/image): text
Enter filename (make sure file is in test/input): contoh.txt
```

Format file `.txt` (setiap karakter merepresentasikan satu warna pada sel):

```
AAABB
AABBB
BBBCC
BBCCC
```

### Input Gambar

```
Input type (text/image): image
Enter image filename (in test/input/): board.png
Enter board size (n for nxn board): 4
```

- Gambar harus berupa papan kotak `n x n` dengan sel berwarna solid
- Program otomatis mendeteksi warna tiap sel dari titik tengah sel
- Papan harus memiliki garis grid yang jelas antar sel

### Menyimpan Hasil

Setelah solusi ditemukan, program akan menampilkan hasil dan bertanya secara terpisah:

```
Do you want to save results to txt? (y/n): y
Input filename for .txt file: hasil

Do you want to save results to image? (y/n): y
Input filename for image file: hasil
```

- File `.txt` disimpan ke `../test/output/<filename>.txt`
- File gambar disimpan ke `../test/output/<filename>.png`
- Kedua opsi tersedia untuk input teks maupun gambar

---

## Format Output

### Output Terminal

```
Starting brute force search for 4 queens on 4x4 grid...

Search time: 12 ms
Number of combinations tried: 1820 combinations
Result:
A # A B
A A B B
C C # D
C C D #
```

### Output .txt

```
A#AB
AABB
CC#D
CCD#
Waktu pencarian: 12 ms
Banyak kasus yang ditinjau: 1820 kasus
```

### Output Gambar

File `.png` berisi papan berwarna dengan ikon ratu yang ditempatkan pada posisi solusi. Untuk input teks, warna tiap karakter menggunakan palet warna yang telah ditentukan (A=Merah, B=Biru, C=Hijau, dst. hingga Z).

---

## Konfigurasi

Di bagian atas `main.go` terdapat konstanta yang bisa diubah:

```go
const queenImagePath = "queen.png" // Path ke gambar ikon ratu
const cellSize      = 100          // Ukuran sel output gambar (pixel)
const gridLineSize  = 2            // Ketebalan garis grid output (pixel)
```
