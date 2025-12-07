# Laporan Praktikum Minggu 1 (sesuaikan minggu ke berapa?)
Topik: [Tuliskan judul topik, misalnya "Class dan Object"]

## Identitas
- Nama  : Azzam Zain Zaidan Sudiyono
- NIM   : 240202854
- Kelas : 3IKKA

---

## Tujuan
Mahasiswa memahami konsep inheritance dalam OOP di Java dan dapat membuat class dengan pewarisan — yaitu membuat superclass dan subclass, serta menggunakan kembali properti/metode dari superclass melalui subclass.


## Dasar Teori
-Inheritance (pewarisan) memungkinkan sebuah class (“subclass”) mewarisi properti dan metode dari class lain (“superclass”). 
-Dengan inheritance, kita bisa memanfaatkan kembali kode (code reusability), sehingga tidak perlu menulis ulang properti/metode yang sama di banyak class. 
-Hubungan antara subclass dan superclass di Java dinyatakan dengan keyword extends. Subclass “adalah” superclass — ini disebut “is-a relationship”. 
-Subclass dapat menambah properti/metode baru, atau menimpa (override) metode dari superclass sesuai kebutuhan. 
-Notasi dasar untuk inheritance:


## Langkah Praktikum
-Siapkan file Java: buat superclass dan subclass sesuai struktur pewarisan.
-Implementasikan properti/metode di superclass, lalu di subclass tambahkan atau override sesuai kebutuhan.
-Buat objek dari subclass di kelas main, dan panggil metode — baik yang diwarisi maupun yang spesifik di subclass.
-Jalankan program, amati output sebagai bukti pewarisan berjalan.
-Simpan kode di repository (jika menggunakan version control), dengan commit message misalnya: Add inheritance example – superclass & subclass.

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
  
- Apa perbedaan pendekatan minggu ini dibanding minggu sebelumnya.  
- Kendala yang dihadapi dan cara mengatasinya.  


## Kesimpulan
(Tuliskan kesimpulan dari praktikum minggu ini.  
Contoh: *Dengan menggunakan class dan object, program menjadi lebih terstruktur dan mudah dikembangkan.*)

---

## Quiz
(1. [Tuliskan kembali pertanyaan 1 dari panduan]  
   **Jawaban:** …  

2. [Tuliskan kembali pertanyaan 2 dari panduan]  
   **Jawaban:** …  

3. [Tuliskan kembali pertanyaan 3 dari panduan]  
   **Jawaban:** …  )
