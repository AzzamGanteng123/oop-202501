# Laporan Praktikum Minggu 9
Topik: Exception Handling pada Java

## Identitas
- Nama  : Azzam Zain Zaidan Sudiyono
- NIM   : 240202854
- Kelas : 3IKKA

## Tujuan
Tujuan dari praktikum ini adalah agar mahasiswa memahami konsep exception handling pada Java, mampu menggunakan blok try-catch-finally, serta dapat menangani kesalahan (error) yang terjadi saat program dijalankan agar aplikasi berjalan lebih aman dan stabil.

## Dasar Teori
-Exception adalah kejadian tidak terduga yang terjadi saat runtime dan dapat menyebabkan program berhenti.
-Try-catch digunakan untuk menangkap dan menangani exception agar program tidak crash.
-Finally selalu dieksekusi, baik terjadi exception maupun tidak.
-Java menyediakan built-in exception seperti ArithmeticException dan NullPointerException.
-Exception handling meningkatkan keandalan dan keamanan program.

## Langkah Praktikum
-Mempelajari konsep exception handling pada Java berdasarkan Bab 9.
-Membuat program Java yang berpotensi menimbulkan error (misalnya pembagian dengan nol).
-Menggunakan blok try-catch untuk menangani exception.
-Menambahkan blok finally untuk eksekusi kode tambahan.
-Menjalankan program dan mengamati hasil eksekusi.

## Kode Program
package com.upb.agripos.week9;

public class MainExceptionDemo {
    public static void main(String[] args) {
        System.out.println("Hello, I am Azzam Zain-240202854 (Week9)");

        ShoppingCart cart = new ShoppingCart();
        Product p1 = new Product("P01", "Pupuk Organik", 25000, 3);

        try {
            cart.addProduct(p1, -1);
        } catch (InvalidQuantityException e) {
            System.out.println("Kesalahan: " + e.getMessage());
        }

        try {
            cart.removeProduct(p1);
        } catch (ProductNotFoundException e) {
            System.out.println("Kesalahan: " + e.getMessage());
        }

        try {
            cart.addProduct(p1, 5);
            cart.checkout();
        } catch (Exception e) {
            System.out.println("Kesalahan: " + e.getMessage());
        }
    }
}

## Hasil Eksekusi
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/ea3ab88f-669f-4ebf-b208-f2f0f967310e" />


## Analisis
-Pada praktikum ini, kode dijalankan di dalam blok try yang berisi operasi pembagian. Ketika terjadi pembagian dengan nol, Java secara otomatis melempar ArithmeticException dan program langsung masuk ke blok catch untuk menangani error tersebut. Hal ini mencegah program berhenti secara tiba-tiba.

-Dibandingkan dengan praktikum minggu sebelumnya yang berfokus pada Collections, praktikum ini lebih menekankan pada penanganan kesalahan runtime. Jika sebelumnya fokus pada pengelolaan data, pada praktikum ini fokus diarahkan pada kestabilan dan keamanan program.

-Kendala yang dihadapi adalah memahami jenis exception yang muncul dan bagaimana cara menanganinya. Kendala tersebut diatasi dengan mempelajari       dokumentasi Java dan melakukan percobaan langsung menggunakan berbagai jenis error.

## Kesimpulan
Dari praktikum ini dapat disimpulkan bahwa exception handling sangat penting dalam pemrograman Java untuk mencegah program berhenti secara tiba-tiba. Dengan menggunakan try-catch-finally, program menjadi lebih aman, stabil, dan mudah dikembangkan serta mampu menangani kesalahan secara terkontrol.

## Quiz
1. Jelaskan perbedaan error dan exception.
Jawaban:
Error adalah kesalahan serius yang terjadi pada sistem dan umumnya tidak dapat ditangani oleh program, seperti OutOfMemoryError atau StackOverflowError. Error biasanya disebabkan oleh masalah lingkungan atau sistem dan menandakan kondisi fatal.Sedangkan exception adalah kesalahan yang terjadi saat runtime dan dapat ditangani oleh program menggunakan mekanisme try-catch, seperti ArithmeticException atau NullPointerException.

2. Apa fungsi finally dalam blok try–catch–finally?
Jawaban:
Blok finally berfungsi untuk menjalankan kode yang harus dieksekusi, baik terjadi exception maupun tidak. Biasanya digunakan untuk menutup resource seperti file, koneksi database, atau menampilkan pesan penutup agar program tetap berjalan dengan baik.

3. Mengapa custom exception diperlukan?
Jawaban:
Custom exception diperlukan untuk menangani kesalahan yang spesifik terhadap kebutuhan bisnis aplikasi. Dengan custom exception, pesan kesalahan menjadi lebih jelas, terstruktur, dan mudah dipahami, serta membantu pengembang dalam melakukan debugging dan pengelolaan error sesuai konteks aplikasi.

4. Berikan contoh kasus bisnis dalam POS yang membutuhkan custom exception.
Jawaban:
Contoh kasus dalam sistem POS adalah ketika jumlah stok produk tidak mencukupi saat transaksi dilakukan. Dalam kondisi ini dapat dibuat custom exception seperti StokTidakCukupException yang akan muncul ketika pelanggan membeli barang melebihi stok yang tersedia, sehingga transaksi dapat dibatalkan atau disesuaikan secara terkontrol.
