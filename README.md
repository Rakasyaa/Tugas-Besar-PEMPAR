
# 🕹️ TUBES_PEMPAR: Paralel Processing on Game Dataset

Proyek ini mengeksplorasi pemrosesan data secara **paralel** menggunakan dua pendekatan:
- **MPI (Message Passing Interface)** untuk distribusi tugas dengan scatter/reduce.
- **PySpark** untuk pemrosesan RDD dan transformasi data dalam skala besar.

## 📁 Dataset
Dataset utama: `game_info.csv`  
Berisi informasi seputar game seperti:
- `title`, `platform`, `release_date`
- `metacritic` (skor kritik)
- `ratings_count` (jumlah rating pengguna)
- dan fitur lainnya.

## ⚙️ Requirements
- Python 3.x
- `mpi4py`
- `pandas`
- `pyspark`
- `notebook` / `jupyterlab`

Instalasi cepat (opsional):
```bash
pip install mpi4py pandas pyspark notebook
```

## 🚀 Cara Menjalankan

### 1. MPI Version (menggunakan scatter/filter/reduce)
```bash
mpiexec -n 4 python mpi_script.py
```

**Fungsi utama:**
- Membaca dataset dengan pandas.
- Menyebar (scatter) data ke tiap proses.
- Menyaring data dengan `metacritic > 80`.
- Menjumlahkan `ratings_count` dengan `reduce`.

### 2. PySpark Version (menggunakan RDD)
```bash
spark-submit pyspark_script.py
```

**Fungsi utama:**
- Membaca file sebagai RDD.
- Menghapus header.
- Memfilter game dengan `metacritic > 80`.
- Mengambil dan menjumlahkan kolom `ratings_count`.

## 📌 Contoh Output
```
Total ratings_count untuk metacritic > 80: 2,345,678
```

## 📎 Catatan Teknis
- Header pada RDD dihapus secara manual: `rdd.first()` atau `line.startswith("title")`.
- Parsing CSV dilakukan menggunakan `csv.reader` atau `pandas` untuk kenyamanan.
- Pastikan urutan kolom diketahui (misal: `ratings_count` di index ke-12).

## 👨‍💻 Kontributor
- Rakasya Yoga Surya Pratama
