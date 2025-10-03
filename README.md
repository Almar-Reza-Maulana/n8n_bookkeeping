# Bot Catatan Pengeluaran: Workflow n8n untuk Bookkeeping Sederhana via Telegram
Halo Semuanya ! Selamat datang di repo ini. Proyek kali ini adalah workflow n8n sederhana yang saya buat untuk membantu mencatat pengeluaran keuangan secara mudah dan otomatis. Bayangkan punya asisten pribadi di Telegram yang bisa baca struk belanja dari foto, catat input manual, dan bahkan kasih laporan pengeluaran harian/mingguan/bulanan. Semuanya disimpan rapi di Google Sheets, tanpa ribet!

Kamu bisa import langsung ke akun n8n kamu untuk di coba sendiri. Bot ini saya buat karena sering banget dari kita lupa kalau catat belanja kecil-kecilan eh malah ga sadar, dan akhirnya budget jebol. Dengan bot ini, cukup kirim foto struk atau ketik "beli kopi 10rb", langsung tersimpan! 😊

## Kenapa Bot ini lebih baik dari pada pencatatan manual ?

1. Mudah Digunakan: Cukup chat di Telegram yang pasti ada di HP. Nggak perlu buka Excel atau app khusus setiap kali belanja.
2. Pintar dengan AI: Pakai Google Gemini untuk baca foto struk (ekstrak nama toko, total harga, daftar barang) atau parse input teks bebas (misal "jajan bakso 15ribu"). AI bikin semuanya otomatis dan akurat, tapi tetap sederhana.
3. Simpan Data Aman: Semua catatan masuk ke Google Sheets pribadi. Bisa diakses kapan saja untuk analisis lebih lanjut (misal hitung total bulanan pakai formula Sheets).
4. Gratis & Fleksibel: n8n open-source, Telegram gratis, dan API Gemini punya kuota gratis. Kalau mau modifikasi, tinggal edit node di n8n – no coding dibutuhkan!
5. Alternatif Lain? App seperti Money Manager bagus, tapi kurang integrasi dengan chat. Script manual butuh server, sementara n8n mudah deploy di cloud gratis seperti Render atau Vercel.

Intinya, ini solusi "set it and forget it" buat yang sibuk tapi pengen kelola keuangan lebih baik. Hemat waktu, kurangi lupa, dan bikin budgeting jadi fun! 🚀

## Cara Kerja Workflow
Workflow dimulai saat ada pesan masuk di Telegram (via Telegram Trigger). Lalu, Switch node bagi alur berdasarkan jenis input:

### Tahap 1 : Kirim Foto Struk Belanja 📸

  1. Bot download foto, lalu pakai AI (Google Gemini via HTTP Request) untuk baca isi struk.
  2. Ekstrak info: Nama toko, total harga (angka saja), daftar barang (pisah koma), tanggal (default hari ini kalau nggak kelihatan).
  3. Kalau foto blur/gagal dibaca, bot kasih tips foto ulang.
  4. Jika sudah maka data akan tersimpan ke Google Sheets dan mengirim konfirmasi: "✅ Data tersimpan! Toko: Alfamart, Total: Rp25.500, dll."

### Tahap 2 : Input Manual via Teks ✍️

1. Ketik aja seperti "beli telur 1kg 20rb di warung" atau "jajan es krim 15ribu".
2. Kalau nggak paham, bot bakalan kasih contoh formatnya. Kalau sudah sukses maka data akan disimpan ke sheets.

### Tahap 3 : Minta Laporan Pengeluaran 📊

1. Ketik /laporan hari ini, /laporan minggu ini, atau /laporan bulan ini.
2. AI ambil data dari Sheets, filter periode, hitung total & jumlah transaksi, urut dari terbaru.

### Tahap 4 : Butuh Bantuan? ❓

Ketik /help untuk panduan lengkap command dan tips.

## Cara Setup chatbot ini sendiri

1. Buat akun n8n : kalian bisa buat akun dengan dua cara yaitu lewat n8n cloud (Sumopod, Hostinger, n8n.io) atau memakai self hosted
2. Import Workflow: Copy JSON dari file di repo ini, paste ke n8n lewat import from file
3. Jangan lupa setup credentials : telegram, google sheets, google gemini
4. Execute workflow untuk menjalankan bot ini
5. Tinggal gunakan workflow ini lewat bot telegram yang telah kamu buat
6.  Selesai 😊

## Contoh Output

![img](https://github.com/Almar-Reza-Maulana/n8n_bookkeeping/blob/main/Screenshot%202025-10-03%20184849.png)

![img](https://github.com/Almar-Reza-Maulana/n8n_bookkeeping/blob/main/Screenshot%202025-10-03%20185456.png)

![img](https://github.com/Almar-Reza-Maulana/n8n_bookkeeping/blob/main/Screenshot%202025-10-03%20190110.png)

![img](https://github.com/Almar-Reza-Maulana/n8n_bookkeeping/blob/main/Screenshot%202025-10-03%20190336.png)

## Kontribusi & Masukan
Repo ini open buat semua! Kalau ada bug atau ide (misal tambah kategori pengeluaran) bisa kasih tau dan mari bikin tool ini lebih keren bareng. Terima kasih udah mampir,  semoga bermanfaat buat kelola keuanganmu! 💸❤️
