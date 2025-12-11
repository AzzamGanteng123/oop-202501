# Laporan Praktikum Minggu 3
Topik: Inheritance (Pewarisan Class)

## Identitas
- Nama  : Azzam Zain Zaidan Sudiyono
- NIM   : 240202854
- Kelas : 3IKKA

## Tujuan
Mahasiswa memahami konsep inheritance dalam OOP di Java dan dapat membuat class dengan pewarisan — yaitu membuat superclass dan subclass, serta menggunakan kembali properti/metode dari superclass melalui subclass.


## Dasar Teori
-Inheritance (pewarisan) memungkinkan sebuah class (“subclass”) mewarisi properti dan metode dari class lain (“superclass”). 
-Dengan inheritance, kita bisa memanfaatkan kembali kode (code reusability), sehingga tidak perlu menulis ulang properti/metode yang sama di banyak class. 
-Hubungan antara subclass dan superclass di Java dinyatakan dengan keyword extends. Subclass “adalah” superclass — ini disebut “is-a relationship”. 
-Subclass dapat menambah properti/metode baru, atau menimpa (override) metode dari superclass sesuai kebutuhan. 
-Notasi dasar untuk inheritance:


## Langkah Praktikum
-Membuat superclass Produk (menggunakan class dari Bab 2).
-Membuat subclass:
    -Benih → atribut tambahan: varietas
    -Pupuk → atribut tambahan: jenis
    -AlatPertanian → atribut tambahan: material
-Menambahkan konstruktor di masing-masing subclass dan memanggil konstruktor superclass dengan super().
-Membuat class MainInheritance untuk menginstansiasi objek dari setiap subclass.
-Menampilkan data produk menggunakan method getter.
-Memanggil CreditBy.print() untuk menampilkan identitas mahasiswa.
-Menjalankan program dan mengambil screenshot hasil.
-Commit dengan pesan week3-inheritance.

## Kode Program
package com.upb.agripos;

import com.upb.agripos.model.*;
import com.upb.agripos.util.CreditBy;

public class MainInheritance {
    public static void main(String[] args) {
        Benih b = new Benih("BNH-001", "Benih Padi IR64", 25000, 100, "IR64");
        Pupuk p = new Pupuk("PPK-101", "Pupuk Urea", 350000, 40, "Urea");
        AlatPertanian a = new AlatPertanian("ALT-501", "Cangkul Baja", 90000, 15, "Baja");

        System.out.println("Benih: " + b.getNama() + " Varietas: " + b.getVarietas());
        System.out.println("Pupuk: " + p.getNama() + " Jenis: " + p.getJenis());
        System.out.println("Alat Pertanian: " + a.getNama() + " Material: " + a.getMaterial());

        CreditBy.print("240202854", "Azzam Zain");
    }
}
---

## Hasil Eksekusi
<img width="1919" height="413" alt="image" src="https://github.com/user-attachments/assets/e5583f7f-4496-4c7e-a445-bbbc9447cdb3" />


## Analisis
- Jelaskan bagaimana kode berjalan.
  Program memuat superclass Produk yang berisi atribut dasar produk.
  Subclass (Benih, Pupuk, AlatPertanian) mewarisi atribut dan method dari Produk.
  Saat objek dibuat, constructor subclass memanggil constructor superclass menggunakan super(), kemudian mengisi atribut tambahannya.
  Method getter seperti getNama() berasal dari superclass, sedangkan getVarietas() berasal dari subclass.
  Output menunjukkan bahwa setiap subclass dapat memanfaatkan atribut umum dari Produk sekaligus atribut khususnya masing-masing.
- Apa perbedaan pendekatan minggu ini dibanding minggu sebelumnya.
  Minggu sebelumnya, setiap class bersifat mandiri dan tidak berhubungan, sehingga atribut yang sama harus ditulis ulang.
  Minggu ini menggunakan inheritance, di mana atribut umum disimpan satu kali di Produk, dan subclass cukup menambah atribut khusus.
  Kode lebih singkat, terstruktur, dan mudah dikembangkan tanpa duplikasi.
- Kendala yang dihadapi dan cara mengatasinya.
  Error constructor Produk tidak ditemukan
    ➜ Sebab: lupa menuliskan super(kode, nama, harga, stok)
    ➜ Solusi: panggil constructor superclass dengan parameter yang benar.
  Atribut superclass tidak bisa diakses
    ➜ Sebab: modifier private.
    ➜ Solusi: akses melalui getter/setter.
  Import class error
    ➜ Solusi: pastikan struktur package benar dan import menggunakan:
    import com.upb.agripos.model.*;
  Folder struktur Maven salah
    ➜ Solusi: semua file Java harus berada di
    src/main/java/com/upb/agripos/... 


## Kesimpulan
Inheritance memungkinkan reuse kode melalui hubungan “is-a”.
Subclass dapat mewarisi atribut dan method dari superclass tanpa menulis ulang.
Program yang menggunakan inheritance menjadi lebih modular, rapi, dan mudah diperluas.
Konsep super sangat penting untuk memanggil konstruktor superclass.

## Quiz
    1.Apa keuntungan menggunakan inheritance dibanding membuat class terpisah?
        Inheritance menghindari duplikasi kode, membuat struktur lebih rapi, dan memudahkan pengembangan.
    
    2.Bagaimana cara subclass memanggil konstruktor superclass?
        Dengan keyword:
        super(parameter);

    3.Berikan contoh lain produk POS pertanian yang dapat dijadikan subclass.
        Contoh:
        Pestisida
        Obat Tanaman
        Mesin Pertanian (power sprayer, cultivator)
        Pakan Ternak
        
