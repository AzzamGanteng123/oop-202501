# Laporan Praktikum Minggu 1 (sesuaikan minggu ke berapa?)
Topik: Polymorphism dalam Pemrograman Berorientasi Objek

## Identitas
- Nama  : Azzam Zain ZAidan Sudiyono
- NIM   : 240202854
- Kelas : 3IKKA

---

## Tujuan
Tujuan dari praktikum ini adalah agar mahasiswa memahami konsep polymorphism dalam pemrograman berorientasi objek, khususnya penggunaan inheritance dan method overriding, serta mampu menerapkannya dalam pembuatan program Java yang lebih fleksibel dan mudah dikembangkan.

## Dasar Teori
-Polymorphism adalah konsep OOP yang memungkinkan satu metode memiliki banyak bentuk.
-Polymorphism biasanya diterapkan melalui inheritance dan method overriding.
-Method overriding terjadi ketika subclass mendefinisikan ulang metode yang sudah ada pada superclass.
-Pemanggilan metode pada polymorphism ditentukan saat runtime (dynamic binding).
-Polymorphism meningkatkan fleksibilitas dan skalabilitas program.

## Langkah Praktikum
-Mempelajari materi Bab 4 tentang polymorphism pada pemrograman berorientasi objek.
-Membuat superclass sebagai kelas induk.
-Membuat beberapa subclass yang mewarisi superclass tersebut.
-Melakukan override method pada subclass.
-Membuat objek subclass menggunakan referensi superclass.
-Menjalankan program dan mengamati hasil eksekusi polymorphism.

## Kode Program
package com.upb.agripos;

import com.upb.agripos.model.*;
import com.upb.agripos.util.CreditBy;

public class MainPolymorphism {
    public static void main(String[] args) {
        Produk[] daftarProduk = {
                new Benih("BNH-001", "Benih Padi IR64", 25000, 100, "IR64"),
                new Pupuk("PPK-101", "Pupuk Urea", 350000, 40, "Urea"),
                new AlatPertanian("ALT-501", "Cangkul Baja", 90000, 15, "Baja")
        };

        for (Produk p : daftarProduk) {
            System.out.println(p.getInfo()); // Dynamic Binding
        }

        CreditBy.print("240202854", "Azzam Zain");
    }
}

## Hasil Eksekusi
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/dfd603f6-8387-4228-b822-1c9007e71c95" />


## Analisis
  Pada praktikum ini, konsep polymorphism diterapkan dengan membuat superclass Produk yang memiliki method getInfo(). Selanjutnya dibuat beberapa subclass yaitu Benih, Pupuk, dan AlatPertanian yang masing-masing melakukan override terhadap method getInfo() sesuai dengan karakteristik objeknya.

  Pada kelas MainPolymorphism, objek-objek dari subclass dibuat dan disimpan ke dalam array bertipe Produk. Hal ini menunjukkan bahwa satu tipe referensi (Produk) dapat merujuk ke berbagai bentuk objek yang berbeda. Ketika perulangan for dijalankan dan method getInfo() dipanggil, Java secara otomatis menentukan method mana yang dijalankan berdasarkan objek sebenarnya (runtime), bukan berdasarkan tipe referensi. Mekanisme ini disebut dynamic binding.

  Dibandingkan dengan praktikum minggu sebelumnya yang hanya menerapkan inheritance, pada praktikum ini terjadi pengembangan konsep dengan memanfaatkan method overriding sehingga setiap subclass memiliki perilaku yang berbeda walaupun menggunakan method dengan nama yang sama. Hal ini membuat program lebih fleksibel dan mudah dikembangkan ketika ingin menambahkan jenis produk baru tanpa mengubah kode utama.

  Kendala yang dihadapi pada praktikum ini adalah pemahaman mengenai bagaimana Java memilih method yang dijalankan saat menggunakan referensi superclass. Kendala tersebut diatasi dengan mempelajari kembali konsep polymorphism dan melakukan pengujian langsung melalui output program, sehingga terlihat bahwa method yang dijalankan berasal dari subclass masing-masing.

## Kesimpulan
Berdasarkan praktikum yang telah dilakukan, dapat disimpulkan bahwa konsep polymorphism dalam pemrograman berorientasi objek memungkinkan satu tipe referensi untuk merepresentasikan berbagai bentuk objek dengan perilaku yang berbeda. Hal ini diterapkan melalui penggunaan inheritance dan method overriding pada kelas Produk beserta subclass Benih, Pupuk, dan AlatPertanian.

Dengan menerapkan polymorphism, pemanggilan method getInfo() dapat dilakukan secara dinamis sesuai dengan jenis objek yang dijalankan saat runtime. Pendekatan ini membuat program menjadi lebih fleksibel, terstruktur, dan mudah dikembangkan, terutama ketika menambahkan jenis produk baru tanpa harus mengubah kode utama. Oleh karena itu, polymorphism merupakan salah satu konsep penting dalam membangun aplikasi berbasis OOP yang efisien dan mudah dipelihara.

## Quiz
1. Apa perbedaan overloading dan overriding?
Overloading adalah kondisi di mana beberapa method memiliki nama yang sama tetapi parameter berbeda (jumlah, tipe, atau urutan) dalam satu kelas, dan pemilihannya ditentukan saat compile time.
Sedangkan overriding adalah kondisi di mana subclass mendefinisikan ulang method yang sama dengan superclass dengan signature yang sama, dan pemilihannya ditentukan saat runtime.

2. Bagaimana Java menentukan method mana yang dipanggil dalam dynamic binding?
Java menentukan method yang dipanggil dalam dynamic binding berdasarkan tipe objek sebenarnya (runtime object), bukan berdasarkan tipe referensinya. Saat method dipanggil melalui referensi superclass, Java akan menjalankan method milik subclass yang melakukan override terhadap method tersebut.

3. Berikan contoh kasus polymorphism dalam sistem POS selain produk pertanian.
Contoh polymorphism dalam sistem POS adalah pada sistem pembayaran.
Misalnya terdapat superclass Pembayaran dengan method prosesBayar(), lalu subclass Cash, Transfer, dan EWallet yang masing-masing memiliki implementasi berbeda dari method tersebut. Ketika transaksi dilakukan, sistem memanggil prosesBayar() tanpa perlu mengetahui jenis pembayaran yang digunakan, karena Java akan menjalankan method sesuai dengan objek pembayaran yang dipilih.
