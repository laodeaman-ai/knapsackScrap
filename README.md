# README: KnapsackFamily Data Scraper

## Deskripsi

Skrip ini digunakan untuk mengambil data dari situs web KnapsackFamily berdasarkan kata kunci organisme. Data yang diperoleh berupa tabel yang kemudian diekstrak, diformat, dan disimpan dalam file CSV. Skrip ini juga dapat mengambil representasi SMILES dari senyawa yang teridentifikasi.

## Fitur Utama

- Mengambil data tabel dari KnapsackFamily berdasarkan kata kunci organisme.
- Mengekstrak informasi dari tabel HTML.
- Menyimpan data dalam format CSV.
- Mengambil representasi SMILES dari senyawa terkait.
- Menggunakan `ThreadPoolExecutor` untuk mempercepat pengambilan data SMILES secara paralel.

## Persyaratan

Skrip ini memerlukan pustaka berikut:

- `requests` (untuk mengambil data dari web)
- `BeautifulSoup4` (untuk memproses data HTML)
- `csv` (untuk menyimpan data dalam file CSV)
- `concurrent.futures` (untuk eksekusi paralel)
- `os` (untuk operasi file)

Pastikan pustaka yang diperlukan telah terinstal sebelum menjalankan skrip:

```sh
pip install requests beautifulsoup4
```

## Cara Penggunaan

1. Pastikan semua pustaka yang dibutuhkan telah terinstal.
2. Jalankan skrip dengan kata kunci yang diinginkan:
   ```python
   keywords = ['Escherichia coli', 'Homo sapiens']  # Ganti dengan organisme yang diinginkan
   knapsackfamily(keywords)
   ```
3. Data hasil scraping akan disimpan dalam file `data_knapsack.csv`.

## Struktur Kode

- `fetch_table_from_url(base_url, keyword)`: Mengambil tabel dari halaman web berdasarkan kata kunci.
- `parse_table(table)`: Mengekstrak isi tabel menjadi format yang dapat diproses lebih lanjut.
- `save_to_csv(data, filename)`: Menyimpan data dalam format CSV.
- `fetch_smiles_data(row)`: Mengambil representasi SMILES dari senyawa berdasarkan ID.
- `knapsackfamily(keywords)`: Fungsi utama untuk menjalankan scraping.
- `get_smiles_from_id(row_id)`: Mengambil SMILES dari halaman detail senyawa.

## Output

Setelah skrip dijalankan, akan dihasilkan file CSV `data_knapsack.csv` yang berisi informasi dari KnapsackFamily berdasarkan organisme yang dicari. Jika tersedia, data SMILES juga akan ditambahkan ke dalam file.

## Catatan

- Jika tidak ada tabel yang ditemukan untuk suatu organisme, maka akan ditampilkan pesan peringatan.
- Jika file `data_knapsack.csv` sudah ada, maka akan dihapus sebelum menyimpan data baru.
- Karena scraping dilakukan secara paralel, waktu eksekusi lebih cepat dibandingkan metode sekuensial.

## Lisensi

Kode ini dilisensikan di bawah Lisensi MIT. Silakan lihat file `LICENSE` untuk detail lebih lanjut.



