# Laporan Praktikum Minggu 1 (sesuaikan minggu ke berapa?)
Topik: Class dan Object

## Identitas
- Nama  : Azzam Zain Zaidan Sudiyono
- NIM   : 240202854
- Kelas : 3IKKA

---

## Tujuan
Mahasiswa memahami konsep dasar Object-Oriented Programming (OOP), khususnya mengenai class dan object, serta mampu membuat class Produk dengan menggunakan enkapsulasi (atribut bersifat privat dengan akses melalui getter dan setter).



## Dasar Teori
- Class adalah rancangan (blueprint) untuk membentuk objek yang berisi atribut (data) dan method (perilaku).
- Object adalah hasil nyata (instance) dari sebuah class yang dapat digunakan di program.
- Enkapsulasi bertujuan membatasi akses langsung ke atribut agar lebih aman.
- Constructor digunakan untuk menginisialisasi nilai awal objek saat dibuat.
- Dengan konsep OOP, kode menjadi lebih modular, efisien, dan mudah dikembangkan.



## Langkah Praktikum
- Buka IntelliJ IDEA, buat Project baru Java dengan nama OOP-Praktikum.
- Buat package bernama model.
- Di dalam package model, buat file baru Produk.java.
- Tambahkan atribut kode, nama, harga, dan stok dengan modifier private.
- Tambahkan constructor, getter, dan setter untuk setiap atribut.
- Tambahkan method tampilkanInfo() untuk menampilkan data produk.
- Buat file baru Main.java (di luar package atau di package model juga boleh).
- Lakukan instansiasi objek Produk dan tampilkan hasilnya ke console.
- Jalankan program menggunakan tombol Run ▶️ di IntelliJ.
- Commit dan push hasil ke GitHub dengan pesan


## Kode Program
model/Produk.java
package com.upb.agripos.model;

public class Produk {
    private String kode;
    private String nama;
    private double harga;
    private int stok;

    public Produk(String kode, String nama, double harga, int stok) {
        this.kode = kode;
        this.nama = nama;
        this.harga = harga;
        this.stok = stok;
    }

    public String getKode() { return kode; }
    public void setKode(String kode) { this.kode = kode; }

    public String getNama() { return nama; }
    public void setNama(String nama) { this.nama = nama; }

    public double getHarga() { return harga; }
    public void setHarga(double harga) { this.harga = harga; }

    public int getStok() { return stok; }
    public void setStok(int stok) { this.stok = stok; }

    public void tambahStok(int jumlah) {
        this.stok += jumlah;
    }

    public void kurangiStok(int jumlah) {
        if (this.stok >= jumlah) {
            this.stok -= jumlah;
        } else {
            System.out.println("Stok tidak mencukupi!");
        }
    }
}

util/MainProduk.java
package com.upb.agripos;

import com.upb.agripos.util.CreditBy;

public class MainProduk {
    public static void main(String[] args) {
        com.upb.agripos.model.Produk p1 = new com.upb.agripos.model.Produk("BNH-001", "Benih Padi IR64", 25000, 100);
        com.upb.agripos.model.Produk p2 = new com.upb.agripos.model.Produk("PPK-101", "Pupuk Urea 50kg", 350000, 40);
        com.upb.agripos.model.Produk p3 = new com.upb.agripos.model.Produk("ALT-501", "Cangkul Baja", 90000, 15);

        System.out.println("Kode: " + p1.getKode() + ", Nama: " + p1.getNama() + ", Harga: " + p1.getHarga() + ", Stok: " + p1.getStok());
        System.out.println("Kode: " + p2.getKode() + ", Nama: " + p2.getNama() + ", Harga: " + p2.getHarga() + ", Stok: " + p2.getStok());
        System.out.println("Kode: " + p3.getKode() + ", Nama: " + p3.getNama() + ", Harga: " + p3.getHarga() + ", Stok: " + p3.getStok());

        // Tampilkan identitas mahasiswa
        CreditBy.print("240202854", "Azzam Zain");
    }
}

## Hasil Eksekusi
MainProduk.java
<img width="1919" height="359" alt="image" src="https://github.com/user-attachments/assets/83ff419b-d25e-4603-8bca-d1133121edf9" />


## Analisis
- Program berjalan dengan baik di IntelliJ IDEA tanpa error.
- Konsep class dan object diterapkan dengan benar melalui Produk sebagai blueprint dan p1, p2 sebagai objeknya.
- Enkapsulasi membuat data hanya bisa diubah melalui setter, menjaga keamanan data.
- Kendala awal: IntelliJ tidak mengenali package model saat pertama kali run. Solusi: lakukan rebuild project atau pastikan struktur folder sesuai (src/model/Produk.java).

## Kesimpulan
Melalui praktikum ini, mahasiswa memahami bagaimana membuat dan menggunakan class serta object dalam Java.
Konsep enkapsulasi membantu menjaga keamanan data dan membuat program lebih rapi, modular, dan mudah dikembangkan.

## Quiz
1. Mengapa atribut sebaiknya dideklarasikan sebagai private dalam class?
  Jawaban:
  Agar data tidak bisa diakses atau dimodifikasi secara langsung dari luar class.
  Dengan menjadikan atribut private, kita menjaga keamanan dan konsistensi data (data tidak berubah sembarangan) serta menerapkan prinsip enkapsulasi dalam OOP.  

2. Apa fungsi getter dan setter dalam enkapsulasi?
  Jawaban:
  Getter digunakan untuk mengambil (membaca) nilai atribut privat.
  Setter digunakan untuk mengubah (menulis) nilai atribut privat secara terkendali.
  Keduanya berfungsi sebagai jembatan antara data yang disembunyikan dengan dunia luar, sehingga akses terhadap data tetap aman dan terkontrol. 

3. Bagaimana cara class Produk mendukung pengembangan aplikasi POS yang lebih kompleks?
  Jawaban:
  Class Produk dapat menjadi komponen dasar dalam sistem POS (Point of Sale) karena menyimpan informasi penting tentang barang seperti kode, nama, harga, dan stok.
  Dengan adanya class ini, sistem bisa dikembangkan lebih lanjut untuk:
  Mengelola daftar produk secara dinamis,
  Menghitung total belanja,
  Mengurangi stok otomatis setelah transaksi,
  Dan berintegrasi dengan modul lain seperti transaksi, laporan penjualan, atau database.
