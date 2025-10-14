# Laporan Praktikum Minggu 1 (sesuaikan minggu ke berapa?)
Topik: [Tuliskan judul topik, misalnya "Class dan Object"]

## Identitas
- Nama  : Azzam Zain Zaidan Sudiyono
- NIM   : 240202854
- Kelas : 3IKKA

---

## Tujuan
-Mahasiswa memahami konsep dasar paradigma pemrograman, terutama perbedaan antara prosedural dan berorientasi objek (OOP).
-Mahasiswa mampu menyiapkan proyek OOP di lingkungan pengembangan (IDE).
-Mahasiswa dapat melakukan setup GitHub untuk pengumpulan tugas dan manajemen versi.

---

## Dasar Teori
-Paradigma pemrograman adalah gaya atau pendekatan dalam menulis program untuk menyelesaikan masalah menggunakan bahasa pemrograman tertentu.
-Pemrograman Prosedural menekankan pada fungsi dan langkah-langkah berurutan dalam menyelesaikan suatu tugas.
-Pemrograman Berorientasi Objek (OOP) berfokus pada objek yang memiliki data (atribut) dan perilaku (metode).
-OOP memiliki empat pilar utama: Encapsulation, Abstraction, Inheritance, dan Polymorphism.
-Penggunaan Git dan GitHub penting untuk kolaborasi, pencatatan perubahan (commit), dan pengumpulan tugas secara terstruktur.

## Langkah Praktikum
1.	Membuka Visual Code dan membuat project baru bernama oop-pos-240202854.
2.	Membuat struktur folder seperti berikut:
3.	src/main/java/com/upb/agripos/
4.	Membuat tiga file Java:
HelloProcedural.java
HelloFunctional.java
HelloOOP.java
6.	Menulis kode untuk masing-masing pendekatan.
7.	Menjalankan setiap file dengan klik kanan → Run.

## Kode Program
// HelloProcedural.java
public class HelloProcedural {
   public static void main(String[] args) {
      String nim = "240202854";
      String nama = "Azzam Zain";
      String[] produk = {"Beras", "Pupuk", "Benih"};
      int[] harga = {10000, 15000, 12000};
      int total = 0;
      System.out.println("Hello POS World");
      System.out.println("NIM: " + nim + ", Nama: " + nama);
      System.out.println("Daftar Produk:");
      for (int i = 0; i < produk.length; i++) {
         System.out.println("- " + produk[i] + ": " + harga[i]);
         total += harga[i];
      }
      System.out.println("Total harga semua produk: " + total);
   }
}
________________________________________
// HelloFunctional.java
import java.util.*;
import java.util.stream.*;
public class HelloFunctional {
   public static void main(String[] args) {
      String nim = "240202854";
      String nama = "Azzam Zain";
      List<String> produk = Arrays.asList("Beras", "Pupuk", "Benih");
      List<Integer> harga = Arrays.asList(10000, 15000, 12000);
      System.out.println("Hello POS World");
      System.out.println("NIM: " + nim + ", Nama: " + nama);
      System.out.println("Daftar Produk:");
      IntStream.range(0, produk.size())
         .forEach(i -> System.out.println("- " + produk.get(i) + ": " + harga.get(i)));
      int total = harga.stream().mapToInt(Integer::intValue).sum();
      System.out.println("Total harga semua produk: " + total);
   }
}
_________________________________
// HelloOOP.java
class Produk {
   String nama;
   int harga;
   Produk(String nama, int harga) {
      this.nama = nama;
      this.harga = harga;
   }
}

public class HelloOOP {
   public static void main(String[] args) {
      String nim = "240202854";
      String namaMhs = "Azzam Zain";
      Produk[] daftar = {
         new Produk("Beras", 10000),
         new Produk("Pupuk", 15000),
         new Produk("Benih", 12000)
      };
      int total = 0;
      System.out.println("Hello POS World");
      System.out.println("NIM: " + nim + ", Nama: " + namaMhs);
      System.out.println("Daftar Produk:");
      for (Produk p : daftar) {
         System.out.println("- " + p.nama + ": " + p.harga);
         total += p.harga;
      }
      System.out.println("Total harga semua produk: " + total);
   }
}


## Hasil Eksekusi
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/86dd6079-79b5-487d-a0c0-6f0146cd3348" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/7ca2d9c6-4fc8-42e4-956f-ad09ebd9e629" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/538ebb42-b733-4f27-8f77-c6d272efc98c" />
contoh output
Hello POS World
NIM: 240202854, Nama: Azzam Zain
Daftar Produk:
- Beras: 10000
- Pupuk: 15000
- Benih: 12000
Total harga semua produk: 37000


## Analisis
(
- Jelaskan bagaimana kode berjalan.
  Langkah Eksekusi Program

Deklarasi Class

Program dimulai dari class HelloProcedural, yang berisi fungsi utama main().

main() adalah titik masuk program Java — di sinilah eksekusi dimulai.

Inisialisasi Data

Variabel nim dan nama berisi identitas mahasiswa.

Array produk berisi tiga nama produk: "Beras", "Pupuk", "Benih".

Array harga menyimpan harga masing-masing produk: 10000, 15000, dan 12000.

Menampilkan Informasi Awal

Program menampilkan:

Hello POS World
NIM: 240202854, Nama: Azzam Zain
Daftar Produk:


Perulangan (Loop)

for (int i = 0; i < produk.length; i++) digunakan untuk menelusuri semua elemen array produk.

Dalam setiap iterasi, program menampilkan nama produk dan harganya.

Nilai harga juga ditambahkan ke variabel total agar bisa menghitung jumlah keseluruhan.

Contoh hasil dalam terminal:

- Beras: 10000
- Pupuk: 15000
- Benih: 12000


Menampilkan Total Harga

Setelah loop selesai, program menampilkan total semua harga:

Total harga semua produk: 37000 

- Apa perbedaan pendekatan minggu ini dibanding minggu sebelumnya.
  Program ini menggunakan pendekatan prosedural, artinya semua logika dijalankan dalam satu fungsi besar (main) tanpa adanya class atau object terpisah.
  Pendekatan ini cocok untuk program kecil, tapi akan sulit dikelola saat program bertambah besar.
  Minggu-minggu berikutnya akan mengubah gaya kode ini menjadi OOP (Object-Oriented Programming) dengan memisahkan data dan perilaku ke dalam class seperti Produk.
- Kendala yang dihadapi dan cara mengatasinya.
  Kendala: Awalnya program tidak bisa dijalankan karena salah memilih Run Configuration,
  Solusi: Klik kanan pada file yang berisi main() → pilih Run ‘HelloProcedural.main(),

)
---

## Kesimpulan
  -Paradigma OOP berbeda dengan paradigma prosedural karena berfokus pada objek.
  -Setup proyek dan pengenalan GitHub penting untuk mempermudah pengumpulan dan pemantauan progres praktikum.
  -Lingkungan pengembangan yang siap akan mempercepat proses pembelajaran dan implementasi konsep OOP ke depannya.

## Quiz
1. Apa perbedaan utama antara paradigma prosedural dan OOP?
    Jawaban: Paradigma prosedural berfokus pada urutan langkah (fungsi), sedangkan OOP berfokus pada objek yang memiliki atribut dan perilaku.

2. Sebutkan empat pilar utama dalam OOP!
    Jawaban: Encapsulation, Abstraction, Inheritance, Polymorphism.

3. Apa fungsi Git dalam pengumpulan tugas praktikum?
    Jawaban: Git digunakan untuk mencatat perubahan, melakukan kolaborasi, dan mempermudah pengumpulan tugas melalui sistem versi di GitHub.
