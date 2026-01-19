# Laporan Praktikum Minggu 10
Topik: Design Pattern (Singleton, MVC) dan Unit Testing Menggunakan JUnit

## Identitas
- Nama  : Azzam Zain Zaidan Sudiyono
- NIM   : 240202854
- Kelas : 3IKKA


## Tujuan
Tujuan dari praktikum minggu ke-10 ini adalah agar mahasiswa mampu memahami konsep design pattern dalam pengembangan perangkat lunak, khususnya Singleton dan Model–View–Controller (MVC), serta mampu membuat dan menjalankan unit testing menggunakan JUnit untuk memastikan kualitas dan kebenaran fungsi program.

## Dasar Teori
-Design Pattern adalah solusi umum yang telah terbukti efektif untuk menyelesaikan permasalahan desain perangkat lunak yang sering muncul.
-Singleton Pattern bertujuan memastikan sebuah class hanya memiliki satu instance selama aplikasi berjalan.
-MVC (Model–View–Controller) memisahkan logika bisnis, tampilan, dan pengendali agar kode lebih terstruktur dan mudah dikembangkan.
-Unit Testing digunakan untuk menguji bagian terkecil dari program secara terpisah.
-JUnit adalah framework testing pada Java yang digunakan untuk melakukan pengujian otomatis.

## Langkah Praktikum
-Membuat struktur direktori project sesuai standar Maven.
-Mengimplementasikan Singleton Pattern pada class DatabaseConnection.
-Membuat struktur MVC sederhana untuk fitur Product yang terdiri dari:
-Model (Product)
-View (ConsoleView)
-Controller (ProductController)
-Mengintegrasikan MVC pada class AppMVC.
-Membuat unit test menggunakan JUnit pada class ProductTest.
-Menjalankan program dan unit test.
-Mendokumentasikan hasil eksekusi dan unit testing.
-Melakukan commit ke repository GitHub.
## Kode Program
package com.upb.agripos;

import com.upb.agripos.model.Product;
import com.upb.agripos.view.ConsoleView;
import com.upb.agripos.controller.ProductController;

public class AppMVC {
    public static void main(String[] args) {
        System.out.println("Hello, I am Azzam Zain-240202854 (Week10)");
        Product product = new Product("P01", "Pupuk Organik");
        ConsoleView view = new ConsoleView();
        ProductController controller = new ProductController(product, view);
        controller.showProduct();
    }
}


## Hasil Eksekusi
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/1449676f-c772-4375-8864-83253f8746d4" />


## Analisis
-Program berjalan dengan alur Controller mengambil data dari Model dan menampilkannya melalui View.
-Singleton memastikan hanya satu instance koneksi database yang digunakan selama aplikasi berjalan.
-Pendekatan minggu ini lebih terstruktur dibanding minggu sebelumnya karena menggunakan pola desain dan pengujian otomatis.
-Kendala yang dihadapi adalah konfigurasi awal JUnit, namun dapat diatasi dengan memastikan dependensi dan anotasi @Test digunakan dengan benar.

## Kesimpulan
Berdasarkan praktikum minggu ke-10, dapat disimpulkan bahwa penerapan design pattern seperti Singleton dan MVC membuat struktur program lebih rapi, terorganisir, dan mudah dikembangkan. Selain itu, penggunaan unit testing dengan JUnit membantu memastikan fungsi program berjalan sesuai harapan serta meningkatkan kualitas dan keandalan perangkat lunak.

## Quiz
1. Mengapa constructor pada Singleton harus bersifat private?
  Constructor pada Singleton harus bersifat private agar tidak dapat diakses dari luar class.
  Dengan begitu, object tidak bisa dibuat menggunakan keyword new, sehingga jumlah instance dapat dikontrol dan dipastikan hanya satu instance yang   digunakan selama aplikasi berjalan. 
2. Jelaskan manfaat pemisahan Model, View, dan Controller (MVC)
   Pemisahan MVC memberikan beberapa manfaat utama:
  -Kode lebih terstruktur dan rapi karena setiap komponen memiliki tanggung jawab masing-masing.
  -Mudah dikembangkan dan dirawat, perubahan pada tampilan tidak memengaruhi logika bisnis.
  -Memudahkan pengujian (testing) karena Model dapat diuji tanpa bergantung pada View.
  -Mendukung kerja tim, karena pengembangan dapat dilakukan secara paralel.

3. Apa peran unit testing dalam menjaga kualitas perangkat lunak?
  Unit testing berperan untuk:
  -Memastikan setiap fungsi berjalan sesuai harapan.
  -Mendeteksi bug lebih awal sebelum aplikasi dijalankan secara penuh.
  -Meningkatkan kepercayaan terhadap kode saat dilakukan perubahan atau pengembangan lanjutan.
  -Mengurangi risiko error di lingkungan produksi.

4. Apa risiko jika Singleton tidak diimplementasikan dengan benar?
  Risiko yang dapat terjadi antara lain:
  -Terbentuk lebih dari satu instance, sehingga tujuan Singleton tidak tercapai.
  -Pemborosan resource, seperti koneksi database yang berlebihan.
  -Inkonsistensi data, karena banyak instance mengelola data yang sama.
  -Sulit melakukan debugging, terutama pada aplikasi berskala besar.
