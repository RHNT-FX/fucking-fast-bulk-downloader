FuckingFast Bulk Downloader
Skrip Python sederhana untuk mendownload banyak file sekaligus dari FuckingFast ("Fucking Fast File Hosting Service") secara otomatis dan berurutan, cukup dengan menempelkan (paste) semua link ke dalam satu file input.txt.
Dibuat karena kalau download manual satu-satu di web tersebut cukup ribet — harus klik dan mantengin setiap link satu per satu. Dengan skrip ini, kamu tinggal kumpulkan semua link, jalankan skrip, dan biarkan proses download berjalan otomatis sampai selesai.
Fitur

📥 Download banyak file sekaligus secara berurutan (sequential)
📋 Cukup salin-tempel semua link ke input.txt
📊 Progress bar untuk setiap file yang sedang didownload
🎨 Output log berwarna (info, success, error, warning) biar enak dibaca
🗑️ Link yang sudah berhasil didownload otomatis dihapus dari input.txt
📂 File hasil download otomatis tersimpan rapi di folder downloads/

Instalasi
Pastikan Python 3 sudah terinstall, lalu install dependency yang dibutuhkan:
pip install requests beautifulsoup4 tqdm colorama
Cara Pakai

Buat file input.txt di folder yang sama dengan skrip.
Isi input.txt dengan link-link FuckingFast, satu link per baris. Contoh:
https://fuckingfast.co/xxxxxxxx
https://fuckingfast.co/yyyyyyyy
https://fuckingfast.co/zzzzzzzz
Jalankan skrip:
python main.py
Skrip akan memproses link satu per satu:

Mengambil halaman dari link
Mencari nama file dan URL download asli
Mendownload file ke folder downloads/
Menghapus link yang sudah sukses dari input.txt


Semua file hasil download bisa ditemukan di folder downloads/.

Cara Kerja

Skrip membaca semua link dari input.txt.
Untuk setiap link, skrip melakukan request ke halaman tersebut dan mem-parsing HTML-nya dengan BeautifulSoup.
Skrip mencari <meta name="title"> untuk menentukan nama file, dan mencari fungsi JavaScript download() di dalam tag <script> untuk mengekstrak URL download asli (lewat window.open(...)).
Jika URL download ditemukan, file akan didownload langsung dengan progress bar.
Setelah berhasil, link tersebut otomatis dihapus dari input.txt supaya tidak didownload ulang jika skrip dijalankan kembali (berguna kalau proses sempat terhenti di tengah jalan).

Struktur Folder
.
├── main.py
├── input.txt          # Daftar link yang mau didownload
└── downloads/          # Hasil download otomatis tersimpan di sini
Catatan

Jika sebuah link gagal diproses (halaman tidak bisa diakses, fungsi download tidak ditemukan, dll), skrip akan menampilkan pesan error dan lanjut ke link berikutnya tanpa menghentikan seluruh proses.
Link yang gagal tidak akan dihapus dari input.txt, sehingga bisa dicoba ulang di run berikutnya.
Gunakan skrip ini secara bertanggung jawab dan sesuai dengan ketentuan layanan yang berlaku.
