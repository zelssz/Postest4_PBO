🧥 Manajemen Koleksi Fashion — Data Pribadi

🚀 Fitur Utama

🆕 Tambah item baru (nama, kategori, ukuran, warna, brand, tahun).

📋 Lihat daftar koleksi dalam tabel rapi.

🔎 Cari cepat berdasarkan ID atau Nama.

✏️ Ubah sebagian/seluruh data item (field kosong = tetap).

🗑️ Hapus data dengan konfirmasi.

🧭 Filter berdasarkan Kategori (mis. Atasan, Bawahan, Aksesoris, Outer, Sepatu).

🧠 OOP: abstract class + interface, overloading & overriding.


1. Package koleksifashion (Model)
   
   Package ini berisi kelas-kelas inti yang mewakili data/entitas dalam sistem koleksi fashion. Di sini ada abstract class Item (menyimpan atribut umum seperti id, nama, kategori, ukuran, warna, brand, tahun, harga), interface Diskonable (kontrak perilaku diskon), serta kelas turunan Pakaian dan Aksesoris yang meng-override cara menghitung harga akhir dan deskripsi. Seluruh properti dibuat terenkapsulasi (melalui getter/setter), sehingga data tetap aman dan perubahan dilakukan terkontrol. Package ini sekaligus menjadi tempat penerapan konsep Abstraction (abstract class & interface) dan Polymorphism (overriding/overloading) karena perilaku tiap item berbeda sesuai tipenya.
