# 👗👜Manajemen Koleksi Fashion — Data Pribadi

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


![WhatsApp Image 2025-09-19 at 22 20 03_77dc90f1](https://github.com/user-attachments/assets/c7a69292-67ea-4b69-b8bf-c36009e1886d)

![WhatsApp Image 2025-09-19 at 22 20 22_54f64525](https://github.com/user-attachments/assets/7e91420e-3c6d-48c5-b150-23ad34800cd0)

Output program pada gambar menampilkan aplikasi Manajemen Koleksi Fashion berbasis menu teks yang berfungsi untuk mengelola koleksi pribadi. Saat dijalankan, pengguna disajikan pilihan menu seperti menambahkan item, menampilkan daftar, mencari, mengubah, menghapus, memfilter, hingga keluar dari program. Pada output ini, user memilih menu 1 (Tambahkan Koleksi Item), lalu mengisi data koleksi berupa Kaos Polo dengan kategori Atasan, ukuran M, S, L, warna Hitam, Putih, Pink, brand Polo, dan tahun 2023. Output tersebut menunjukkan program sudah berjalan sesuai fungsi dengan menampilkan kembali data yang diinput sehingga user dapat memastikan koleksi tersimpan dengan benar.

![WhatsApp Image 2025-09-19 at 22 19 37_b3f5040e](https://github.com/user-attachments/assets/747bf2f3-f24c-4937-b21a-1a34908c3cb0)

Output pada gambar menunjukkan hasil saat user memilih menu 2 (Tampilkan Daftar Item) pada aplikasi Manajemen Koleksi Fashion. Program menampilkan tabel berisi daftar koleksi fashion yang sudah tersimpan, lengkap dengan informasi ID, Nama, Kategori, Ukuran, Warna, Brand, dan Tahun. Dari hasil tersebut, terlihat ada 11 item fashion seperti Jaket Denim, Sneakers Canvas, Kaos Graphic, hingga Kaos Polo yang sebelumnya ditambahkan. Setiap data ditampilkan secara terstruktur sehingga memudahkan user untuk melihat detail koleksi berdasarkan atributnya. Tampilan tabel ini membuktikan bahwa fungsi menampilkan data berjalan dengan baik dan memfasilitasi user untuk mengelola koleksinya secara rapi dan jelas.

![WhatsApp Image 2025-09-19 at 22 21 26_65e6f020](https://github.com/user-attachments/assets/54c43bf4-f5e9-42a2-b5c7-19c8cca13fd8)

Output pada gambar menunjukkan hasil saat user memilih menu 3 (Cari ID/Nama) pada aplikasi Manajemen Koleksi Fashion. Setelah memilih menu, program meminta input berupa ID atau Nama Produk, lalu user memasukkan data “5 Dress Batik”. Namun, hasil pencarian menampilkan pesan “Tidak ditemukan” karena format input yang dimasukkan tidak sesuai dengan ketentuan pencarian, di mana seharusnya hanya memasukkan ID saja (misalnya angka 5) atau hanya nama produk (misalnya Dress Batik) tanpa digabungkan. Dari output ini terlihat bahwa sistem pencarian bekerja sesuai logika yang diterapkan, yaitu hanya menampilkan data jika input sesuai dengan format pencarian yang benar, sehingga membantu user memahami cara penggunaan fitur cari dengan lebih tepat.

![WhatsApp Image 2025-09-19 at 22 21 54_ddc4570b](https://github.com/user-attachments/assets/e8f09d6d-9792-4ad0-b5e2-fb23a547b221)

Output pada gambar memperlihatkan hasil ketika user memilih menu 3 (Cari ID/Nama) pada aplikasi Manajemen Koleksi Fashion. Setelah memilih menu, program meminta input ID atau Nama Produk, lalu user memasukkan angka 5. Sistem berhasil menemukan data sesuai ID tersebut dan menampilkan detail koleksi berupa Dress Batik dengan kategori Atasan, ukuran M, warna Maroon, brand Lokal, dan tahun 2023. Dari hasil ini terlihat bahwa fitur pencarian bekerja dengan baik karena mampu menampilkan informasi koleksi secara lengkap berdasarkan ID yang dimasukkan oleh user.

![WhatsApp Image 2025-09-19 at 22 23 10_1e174d7e](https://github.com/user-attachments/assets/5a19478e-70fc-4224-8ca8-6d15d90484f6)

Output pada gambar menunjukkan hasil saat user memilih menu 4 (Ubah Data Koleksi) pada aplikasi Manajemen Koleksi Fashion. Setelah memasukkan ID 8, program menampilkan data lama dari item dengan opsi untuk memperbarui setiap atribut, seperti Nama, Kategori, Ukuran, Warna, Brand, dan Tahun. Jika user ingin mempertahankan data sebelumnya, cukup menekan Enter tanpa mengetikkan input baru. Pada contoh ini, user memperbarui ukuran menjadi S, L, XL serta warna menjadi Hitam, Putih, Coklat, sementara atribut lain tetap dipertahankan. Setelah perubahan disimpan, program menampilkan pesan “Item berhasil diperbarui”, yang menandakan proses update koleksi berhasil dilakukan. Hal ini menunjukkan bahwa fitur edit koleksi berjalan dengan baik dan memberi fleksibilitas bagi user untuk mengubah data sesuai kebutuhan.

![WhatsApp Image 2025-09-19 at 22 38 11_a145efb3](https://github.com/user-attachments/assets/dec22722-723f-485b-9ca6-675eab2f7968)

Output pada gambar memperlihatkan hasil saat user memilih menu 5 (Hapus Koleksi) pada aplikasi Manajemen Koleksi Fashion. Program meminta input berupa ID dari item yang ingin dihapus, namun user memasukkan “11 Kaos Polo” yang berisi kombinasi ID dan nama produk. Sistem kemudian menampilkan pesan “Tidak Valid, Harap Masukkan ID!” karena input tidak sesuai format yang benar. Dari hasil ini terlihat bahwa fitur hapus koleksi hanya menerima input berupa angka ID saja, sehingga user perlu memasukkan angka 11 tanpa tambahan teks lain agar proses penghapusan dapat berhasil dijalankan.

![WhatsApp Image 2025-09-19 at 22 40 15_5593ced5](https://github.com/user-attachments/assets/7f09f8f1-d00a-4814-8131-00dcb58dc3cb)

Output pada gambar memperlihatkan hasil saat user memilih menu 5 (Hapus Koleksi) pada aplikasi Manajemen Koleksi Fashion. Setelah memasukkan ID 11, program menampilkan konfirmasi dengan menanyakan apakah user yakin ingin menghapus item “Kaos Polo”. User kemudian mengetik Y, dan sistem menampilkan pesan “Data dihapus.” sebagai tanda bahwa proses penghapusan berhasil dilakukan. Dari hasil ini terlihat bahwa fitur hapus koleksi sudah berjalan dengan baik karena program tidak hanya langsung menghapus data, tetapi juga memberikan langkah konfirmasi agar user dapat memastikan keputusan sebelum data benar-benar dihapus.

![WhatsApp Image 2025-09-19 at 22 40 57_8af381a3](https://github.com/user-attachments/assets/2d4bdd32-19b0-4ba0-b376-04bf171a3eb8)

Output pada gambar memperlihatkan hasil ketika user memilih menu 6 (Filter Koleksi) pada aplikasi Manajemen Koleksi Fashion. Program kemudian memberikan opsi filter, salah satunya Berdasarkan Kategori. User memilih opsi tersebut dan memasukkan kategori Bawahan, sehingga sistem menampilkan tabel berisi item koleksi yang sesuai dengan kategori tersebut. Dari hasil filter, muncul dua data yaitu Celana Chino dan Rok Plisket, lengkap dengan atribut ukuran, warna, brand, serta tahun. Hal ini menunjukkan bahwa fitur filter sudah berjalan dengan baik karena mampu menampilkan data koleksi sesuai kriteria yang dimasukkan user, sehingga memudahkan pengelolaan koleksi secara lebih spesifik.

![WhatsApp Image 2025-09-19 at 22 41 30_af3f498b](https://github.com/user-attachments/assets/ebd857d3-be8e-4a16-81a9-046a0a19c7ae)

Output pada gambar menunjukkan hasil ketika user memilih menu 6 (Filter Koleksi) pada aplikasi Manajemen Koleksi Fashion. Setelah memilih opsi filter Berdasarkan Kategori, user memasukkan kategori Atasan, dan sistem menampilkan daftar item yang sesuai dengan kategori tersebut. Hasil filter menampilkan dua data, yaitu Kaos Graphic dengan ukuran L, warna Hitam, brand Uniqlo, tahun 2023, serta Dress Batik dengan ukuran M, warna Maroon, brand Lokal, tahun 2023. Dari hasil ini terlihat bahwa fitur filter berhasil berjalan dengan baik karena mampu menampilkan koleksi sesuai kategori yang dimasukkan oleh user, sehingga mempermudah pengelolaan data koleksi berdasarkan jenis item.

![WhatsApp Image 2025-09-19 at 22 41 59_c094f67d](https://github.com/user-attachments/assets/a44213b0-df41-45c7-a4ed-6edc43d0f262)

Output pada gambar memperlihatkan hasil saat user memilih menu 6 (Filter Koleksi) pada aplikasi Manajemen Koleksi Fashion. Setelah memilih opsi filter Berdasarkan Kategori, user memasukkan kategori Aksesoris, dan sistem menampilkan daftar item yang sesuai. Hasil filter menunjukkan satu data yaitu Topi Bucket dengan kategori Aksesoris, ukuran All, warna Cream, brand Columbia, dan tahun 2020. Dari hasil ini dapat dilihat bahwa fitur filter sudah berjalan sesuai fungsi karena mampu menampilkan koleksi yang relevan dengan kategori yang dimasukkan oleh user, sehingga memudahkan dalam pengelolaan data secara lebih terarah.

![WhatsApp Image 2025-09-19 at 22 42 48_24b78c98](https://github.com/user-attachments/assets/54e208f2-ab46-4041-854f-6eba2484453b)

Output pada gambar menunjukkan hasil ketika user memilih menu 7 (Keluar dari Program) pada aplikasi Manajemen Koleksi Fashion. Setelah opsi tersebut dipilih, program menampilkan pesan “Terima kasih. Program selesai.” yang menandakan bahwa aplikasi telah dihentikan dengan benar. Selain itu, sistem juga menampilkan informasi BUILD SUCCESS beserta total waktu eksekusi dan waktu selesai program. Dari hasil ini terlihat bahwa fitur keluar berjalan sesuai fungsi, yaitu menutup aplikasi dengan aman setelah user selesai menggunakan program.

