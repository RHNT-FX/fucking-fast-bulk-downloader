# FuckingFast Bulk Downloader

Skrip Python sederhana untuk mendownload banyak file sekaligus dari **FuckingFast** ("Fucking Fast File Hosting Service") secara otomatis dan berurutan, cukup dengan menempelkan (paste) semua link ke dalam satu file `input.txt`.

Dibuat karena kalau download manual satu-satu di web tersebut cukup ribet — harus klik dan mantengin setiap link satu per satu. Dengan skrip ini, kamu tinggal kumpulkan semua link, jalankan skrip, dan biarkan proses download berjalan otomatis sampai selesai.

## Fitur

- 📥 Download banyak file sekaligus secara berurutan (sequential)
- 📋 Cukup salin-tempel semua link ke `input.txt`
- 📊 Progress bar untuk setiap file yang sedang didownload
- 🎨 Output log berwarna (info, success, error, warning) biar enak dibaca
- 📂 File hasil download otomatis tersimpan rapi di folder `downloads/`

## Instalasi

Pastikan Python 3 sudah terinstall, lalu install dependency yang dibutuhkan:

`pip install requests beautifulsoup4 tqdm colorama`

## Cara Pakai

1. Buat file `input.txt` di folder yang sama dengan skrip.
2. Isi `input.txt` dengan link-link FuckingFast, satu link per baris. Contoh:
`https://fuckingfast.co/uniqueid#blablabla_--_.part07.rar`
`https://fuckingfast.co/uniqueid#blablabla_--_.part08.rar`
`https://fuckingfast.co/uniqueid#blablabla_--_.part09.rar`
`https://fuckingfast.co/uniqueid#blablabla_--_.part10.rar`
3. Jalankan skrip:
   `python main.py`
4. Skrip akan memproses link satu per satu:
   - Mengambil halaman dari link
   - Mencari nama file dan URL download asli
   - Mendownload file ke folder `downloads/`
   - Menghapus link yang sudah sukses dari `input.txt`
5. Semua file hasil download bisa ditemukan di folder `downloads/`.

## Cara Kerja

1. Skrip membaca semua link dari `input.txt`.
2. Untuk setiap link, skrip melakukan request ke halaman tersebut dan mem-parsing HTML-nya dengan BeautifulSoup.
3. Skrip mencari meta tag title untuk menentukan nama file, dan mencari fungsi JavaScript download() di dalam tag script untuk mengekstrak URL download asli (lewat window.open).
4. Jika URL download ditemukan, file akan didownload langsung dengan progress bar.
5. Setelah berhasil, link tersebut otomatis dihapus dari `input.txt` supaya tidak didownload ulang jika skrip dijalankan kembali (berguna kalau proses sempat terhenti di tengah jalan).

## Struktur Folder

- main.py
- input.txt (Daftar link yang mau didownload)
- downloads/ (Hasil download otomatis tersimpan di sini)

## Catatan

- Jika sebuah link gagal diproses (halaman tidak bisa diakses, fungsi download tidak ditemukan, dll), skrip akan menampilkan pesan error dan lanjut ke link berikutnya tanpa menghentikan seluruh proses.
- Link yang gagal **tidak** akan dihapus dari `input.txt`, sehingga bisa dicoba ulang di run berikutnya.
- Gunakan skrip ini secara bertanggung jawab dan sesuai dengan ketentuan layanan yang berlaku.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# FuckingFast Bulk Downloader

A simple Python script to download multiple files at once from **FuckingFast** ("Fucking Fast File Hosting Service") automatically and sequentially, just by pasting all the links into a single `input.txt` file.

This was built because manually downloading one file at a time on that site is tedious — you have to click and babysit every single link. With this script, you just collect all the links, run it, and let the download process run automatically until it's done.

## Features

- 📥 Download multiple files sequentially in one run
- 📋 Just copy-paste all links into `input.txt`
- 📊 Progress bar for each file being downloaded
- 🎨 Colored log output (info, success, error, warning) for easy reading
- 📂 Downloaded files are neatly saved in the `downloads/` folder

## Installation

Make sure Python 3 is installed, then install the required dependencies:

`pip install requests beautifulsoup4 tqdm colorama`

## How to Use

1. Create an `input.txt` file in the same folder as the script.
2. Fill `input.txt` with FuckingFast links, one link per line. Example:
`https://fuckingfast.co/uniqueid#blablabla_--_.part07.rar`
`https://fuckingfast.co/uniqueid#blablabla_--_.part08.rar`
`https://fuckingfast.co/uniqueid#blablabla_--_.part09.rar`
`https://fuckingfast.co/uniqueid#blablabla_--_.part10.rar`
3. Run the script:
   `python main.py`
4. The script will process each link one by one:
   - Fetch the page from the link
   - Find the file name and the actual download URL
   - Download the file into the `downloads/` folder
   - Remove the successfully processed link from `input.txt`
5. All downloaded files can be found in the `downloads/` folder.

## How It Works

1. The script reads all links from `input.txt`.
2. For each link, it sends a request to that page and parses the HTML with BeautifulSoup.
3. It looks for the meta title tag to determine the file name, and searches for the JavaScript download() function inside a script tag to extract the real download URL (via window.open).
4. Once the download URL is found, the file is downloaded directly with a progress bar shown.
5. After a successful download, the link is automatically removed from `input.txt` so it won't be downloaded again if the script is run again (useful if the process gets interrupted midway).

## Folder Structure

- main.py
- input.txt (list of links to download)
- downloads/ (downloaded files are automatically saved here)

## Notes

- If a link fails to process (page unreachable, download function not found, etc.), the script will print an error message and move on to the next link without stopping the whole process.
- Failed links will **not** be removed from `input.txt`, so they can be retried on the next run.
- Use this script responsibly and in accordance with the applicable terms of service.
