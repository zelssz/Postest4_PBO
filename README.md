# 🧥 Manajemen Koleksi Fashion — Data Pribadi

🚀 Fitur Utama:

🆕 Tambah item baru (nama, kategori, ukuran, warna, brand, tahun).

📋 Lihat daftar koleksi dalam tabel rapi.

🔎 Cari cepat berdasarkan ID atau Nama.

✏️ Ubah sebagian/seluruh data item (field kosong = tetap).

🗑️ Hapus data dengan konfirmasi.

🧭 Filter berdasarkan Kategori (mis. Atasan, Bawahan, Aksesoris, Outer, Sepatu).

🧠 OOP: abstract class + interface, overloading & overriding.

# 🧥 Deskripsi Program

Program Manajemen Koleksi Fashion adalah aplikasi berbasis Java untuk mengelola data koleksi fashion pribadi—mulai dari pakaian, sepatu, hingga aksesori. Aplikasi ini menyediakan fitur CRUD lengkap (Create, Read, Update, Delete) ⚙️, dilengkapi pencarian cepat 🔎 (berdasarkan ID atau nama) serta filter 🧭 berdasarkan kategori agar koleksi mudah dikelompokkan dan ditinjau.

Di balik layar, program menerapkan konsep OOP 🧩: abstraction (kelas induk abstrak untuk item) dan polymorphism (perilaku khusus pada Pakaian/Aksesoris), sehingga struktur kode terjaga rapi, mudah dikembangkan, dan siap ditambah fitur baru. Data disimpan dalam koleksi memori yang aman diakses melalui layer service sehingga antarmuka konsol tetap bersih dan fokus pada pengalaman pengguna.

Dengan aplikasi ini, kamu dapat menata informasi penting seperti nama, ukuran, warna, brand, tahun, dan harga 💾; melakukan pembaruan sebagian (field yang dikosongkan tidak diubah) ✏️; serta menghapus data yang tidak diperlukan 🗑️. Tersedia juga seed awal 10 item sehingga pengguna bisa langsung mencoba tanpa input manual terlebih dahulu ⚡.

Manfaat utama bagi pengguna adalah keteraturan dan efisiensi: tidak perlu lagi catat manual di kertas atau spreadsheet terpisah. Semua koleksi dapat dicari, difilter, dan diringkas dalam tampilan tabel yang rapi 📋, membuat proses inventaris pribadi, kurasi outfit, atau persiapan jual-beli preloved menjadi lebih cepat, akurat, dan menyenangkan ✨.

## 📦 Penjelasan Package


1. Package koleksifashion (Model)
   
   Package ini berisi kelas-kelas inti yang mewakili data/entitas dalam sistem koleksi fashion. Di sini ada abstract class Item (menyimpan atribut umum seperti id, nama, kategori, ukuran, warna, brand, tahun, harga), interface Diskonable (kontrak perilaku diskon), serta kelas turunan Pakaian dan Aksesoris yang meng-override cara menghitung harga akhir dan deskripsi. Seluruh properti dibuat terenkapsulasi (melalui getter/setter), sehingga data tetap aman dan perubahan dilakukan terkontrol. Package ini sekaligus menjadi tempat penerapan konsep Abstraction (abstract class & interface) dan Polymorphism (overriding/overloading) karena perilaku tiap item berbeda sesuai tipenya.

2. Package koleksifashion (Service)
   
   Package ini berisi bagian yang mengurus data koleksi. Di sini ada kelas FashionService yang tugasnya menambah, menampilkan, mencari (pakai ID atau nama), mengubah, menghapus, dan mengelompokkan item berdasarkan kategori. Data disimpan sementara di memori, lalu dikirim kembali ke tampilan saat kamu memilih menu di aplikasi.

3. Package koleksifashion (Main)
   
   Package ini berisi pintu masuk program dan tampilan menu di console. Kelas FashionApp yang menampilkan pilihan menu, membaca input dari pengguna (tambah, lihat, cari, ubah, hapus, filter), lalu memanggil FashionService untuk menjalankan perintahnya. Bagian ini fokus pada interaksi pengguna: menampilkan tabel, mengecek input biar tidak salah, serta memberi pesan berhasil/gagal dan navigasi antar menu. Dengan memisahkan bagian tampilan di package ini, kode untuk UI tidak campur dengan logika pengolahan data, jadi struktur proyek lebih rapi dan gampang dirawat.
   
# 📌 Abstraction


<img width="742" height="605" alt="image" src="https://github.com/user-attachments/assets/1fb70b87-e1ce-41ff-b645-e62ff67975be" />


1. Class Item dijadikan abstract class karena berfungsi sebagai kerangka umum untuk semua jenis item fashion di aplikasi. Di dalamnya disimpan atribut dasar seperti id, nama, kategori, ukuran, warna, brand, tahun, dan harga, serta konstruktor untuk menginisialisasi nilai-nilai tersebut. Selain itu, Item mendefinisikan metode abstrak hitungHargaAkhir() (tidak diisi di kelas ini) karena cara menghitung harga akhir tiap kategori berbeda. Implementasi detail barunya diberikan pada subclass, yaitu Pakaian dan Aksesoris. Dengan cara ini, sistem tetap konsisten menggunakan struktur yang sama untuk semua item, namun tetap fleksibel menyesuaikan perilaku khusus tiap jenis barang.

   

<img width="766" height="297" alt="image" src="https://github.com/user-attachments/assets/fd775b8b-1856-4681-8a8a-5df4fd4ded54" />


2. Class Item dijadikan sebagai abstract class karena hanya berfungsi sebagai kerangka umum untuk semua jenis item fashion di aplikasi. Didalamnya ada atribut dasar seperti id, nama, kategori, ukuran, warna, brand, tahun, dan harga, serta satu metode abstrak hitungHargaAkhir(). Metode ini tidak punya isi di dalam Item, karena memang setiap jenis produk punya cara hitung harga akhir yang berbeda. Implementasi detailnya baru diberikan pada subclass, yaitu Pakaian dan Aksesoris (keduanya juga mengisi aturan diskon lewat interface Diskonable). Dengan cara ini, sistem tetap konsisten memakai struktur yang sama, tapi fleksibel menyesuaikan kebutuhan tiap kategori barang.


## 🧩 Kombinasi abstract class + interface (Nilai Tambah)


<img width="895" height="227" alt="image" src="https://github.com/user-attachments/assets/547321ac-490f-4f24-8d3d-5e1a701981f6" />


Pada baris public class Pakaian extends Item implements Diskonable, kelas Pakaian menggabungkan dua konsep OOP sekaligus (nilai tambah) mewarisi abstract class Item dan mengimplementasikan interface Diskonable. Dari Item, Pakaian otomatis mendapat kerangka data umum (id, nama, kategori, ukuran, warna, brand, tahun, harga) sekaligus kontrak hitungHargaAkhir() yang wajib diisi sesuai kebutuhan pakaian. Dari Diskonable, Pakaian berjanji memiliki kemampuan menghitung diskon lewat hitungDiskon(). Kombinasi ini membuat struktur data tetap seragam antar item, tetapi rumus diskon dan harga akhir bisa berbeda-beda per kategori. Hasilnya sistem jadi konsisten, fleksibel, dan mudah dikembangkan—kelas lain seperti Aksesoris atau nanti Sepatu cukup mengikuti pola yang sama tanpa mengubah kode yang sudah ada.



# 🌀 Polymorphism


## 🔄 Polymorphism — Overriding

<img width="866" height="422" alt="image" src="https://github.com/user-attachments/assets/ae70a2d5-b693-4c10-a3c8-2894cf34ab05" />



1. Polymorphism lewat overriding di kelas Pakaian. Pada hitungHargaAkhir(), rumus harga nett dihitung sederhana: harga awal dikurangi diskon (harga - (harga * hitungDiskon())), jadi tiap kategori bisa punya cara hitung diskonnya sendiri. Method deskripsiSingkat() memperluas tampilan dari kelas induk: ia memanggil super.deskripsiSingkat() agar tidak menulis ulang, lalu menambahkan info bahan dan harga nett dengan String.format(...), sehingga teks yang tampil lebih lengkap. Sementara itu, getHargaDasar() juga dioverride tetapi belum diimplementasikan; karena belum dipakai, ia melempar UnsupportedOperationException("Not supported yet.") sebagai tanda “belum tersedia”. Jika nanti dibutuhkan, method ini bisa diisi untuk mengembalikan harga sebelum diskon atau logika lain sesuai kebutuhan.


<img width="866" height="422" alt="image" src="https://github.com/user-attachments/assets/5d3984c5-1699-4284-9067-de20c05bfd10" />



2. Di kelas Aksesoris, terjadi overriding untuk menyesuaikan perilaku khusus aksesoris.hitungHargaAkhir() menghitung harga nett dengan pajak 5% dulu, lalu dikurangi diskon kelas ini. deskripsiSingkat() memanggil super.deskripsiSingkat() lalu menambah info material dan harga nett. getHargaDasar() sementara belum dipakai, jadi melempar UnsupportedOperationException sebagai penanda. Dua metode lain—getHargaFinal() dan hitungDiskon(double)—meneruskan ke default dari interface lewat Diskonable.super..., sehingga logika standar tetap konsisten namun bisa diganti nanti jika diperlukan.


## 🧩 Polymorphism — Overloading


<img width="839" height="143" alt="image" src="https://github.com/user-attachments/assets/a503f87b-bd2e-4f9d-ac27-6edda55cfc4a" />



1. Konstruktor kelas Pakaian, Fungsinya membuat objek pakaian baru dengan data lengkap: id, nama, ukuran, warna, brand, tahun, bahan, harga. Baris super(id, nama, "Pakaian", ukuran, warna, brand, tahun, harga); meneruskan data umum ke kelas induk Item sekaligus mengunci kategori menjadi "Pakaian" (jadi pemanggil tidak perlu mengisi kategori lagi dan tidak akan salah). Setelah itu, this.bahan = bahan; menyimpan bahan khusus milik Pakaian. Biasanya konstruktor ini dipasangkan dengan konstruktor overloading lain tanpa parameter harga (pakai harga default), sehingga kamu bisa membuat objek dengan atau tanpa menentukan harga di awal.



<img width="901" height="131" alt="image" src="https://github.com/user-attachments/assets/f39afa60-dd64-445e-9a75-de96c4c80209" />

<img width="817" height="113" alt="image" src="https://github.com/user-attachments/assets/56e78f2a-2429-49a5-96a5-1c46b1ff02e1" />



2. Dua konstruktor Aksesoris yang menunjukkan overloading. Konstruktor pertama tanpa parameter harga memudahkan membuat data aksesoris cepat ia otomatis memberi harga default 75.000 dengan cara memanggil konstruktor kedua lewat this(..., 75000). Konstruktor kedua adalah konstruktor utama semua data lengkap diteruskan ke kelas Item melalui super(...) sambil mengunci kategori menjadi "Aksesoris" agar tidak salah isi, lalu menyimpan nilai material khusus untuk aksesoris.


#  👗 👒 Alur Program 
