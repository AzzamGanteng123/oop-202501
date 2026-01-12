# Laporan Praktikum Minggu 5
Topik: Abstraction (Abstract Class & Interface)

## Identitas
- Nama  : Azzam Zain Zaidan Sudiyono
- NIM   : 240202854
- Kelas : 3IKKA

## Tujuan
Tujuan dari praktikum ini adalah agar mahasiswa mampu memahami dan menerapkan konsep abstraction dalam pemrograman berorientasi objek menggunakan abstract class dan interface, serta mampu mengimplementasikan multiple inheritance melalui interface pada studi kasus sistem Agri-POS khususnya pada modul pembayaran.

## Dasar Teori
-Abstraksi adalah proses menyederhanakan sistem dengan menampilkan fungsi penting dan menyembunyikan detail implementasi.
-Abstract class tidak dapat diinstansiasi dan dapat memiliki method abstrak maupun method konkret serta menyimpan state (field).
-Interface merupakan kontrak yang berisi deklarasi method dan mendukung multiple inheritance.
-Abstract class digunakan ketika terdapat perilaku dan state bersama, sedangkan interface digunakan untuk mendefinisikan kemampuan lintas kelas.
-Abstraksi meningkatkan fleksibilitas, keterbacaan, dan kemudahan pengembangan sistem.

## Langkah Praktikum
-Membuat abstract class Pembayaran dengan field invoiceNo dan total.
-Mendefinisikan method abstrak biaya() dan prosesPembayaran() serta method konkret totalBayar().
-Membuat interface Validatable dan Receiptable sebagai kontrak perilaku.
-Mengimplementasikan class Cash sebagai subclass dari Pembayaran dan implementasi Receiptable.
-Mengimplementasikan class EWallet sebagai subclass dari Pembayaran serta implementasi Validatable dan Receiptable.
-Membuat class MainAbstraction untuk mendemonstrasikan penggunaan polymorphism dan abstraction.
-Menjalankan program dan mengamati hasil eksekusi.

## Kode Program
Pembayaran.java
package com.upb.agripos.model.pembayaran;

public abstract class Pembayaran {
    protected String invoiceNo;
    protected double total;

    public Pembayaran(String invoiceNo, double total) {
        this.invoiceNo = invoiceNo;
        this.total = total;
    }

    public abstract double biaya();               // fee/biaya tambahan
    public abstract boolean prosesPembayaran();   // proses spesifik tiap metode

    public double totalBayar() {
        return total + biaya();
    }

    public String getInvoiceNo() { return invoiceNo; }
    public double getTotal() { return total; }
}

Cash.java
package com.upb.agripos.model.pembayaran;

import com.upb.agripos.model.kontrak.Receiptable;

public class Cash extends Pembayaran implements Receiptable {
    private double tunai;

    public Cash(String invoiceNo, double total, double tunai) {
        super(invoiceNo, total);
        this.tunai = tunai;
    }

    @Override
    public double biaya() {
        return 0.0;
    }

    @Override
    public boolean prosesPembayaran() {
        return tunai >= totalBayar(); // sederhana: cukup uang tunai
    }

    @Override
    public String cetakStruk() {
        return String.format("INVOICE %s | TOTAL: %.2f | BAYAR CASH: %.2f | KEMBALI: %.2f",
                invoiceNo, totalBayar(), tunai, Math.max(0, tunai - totalBayar()));
    }
}

E Wallet.java
package com.upb.agripos.model.pembayaran;

import com.upb.agripos.model.kontrak.Validatable;
import com.upb.agripos.model.kontrak.Receiptable;

public class EWallet extends Pembayaran implements Validatable, Receiptable {
    private String akun;
    private String otp; // sederhana untuk simulasi

    public EWallet(String invoiceNo, double total, String akun, String otp) {
        super(invoiceNo, total);
        this.akun = akun;
        this.otp = otp;
    }

    @Override
    public double biaya() {
        return total * 0.015; // 1.5% fee
    }

    @Override
    public boolean validasi() {
        return otp != null && otp.length() == 6; // contoh validasi sederhana
    }

    @Override
    public boolean prosesPembayaran() {
        return validasi(); // jika validasi lolos, anggap berhasil
    }

    @Override
    public String cetakStruk() {
        return String.format("INVOICE %s | TOTAL+FEE: %.2f | E-WALLET: %s | STATUS: %s",
                invoiceNo, totalBayar(), akun, prosesPembayaran() ? "BERHASIL" : "GAGAL");
    }
}

MainAbstrac.java
package com.upb.agripos;

import com.upb.agripos.model.pembayaran.*;
import com.upb.agripos.model.kontrak.*;
import com.upb.agripos.util.CreditBy;

public class MainAbstraction {
    public static void main(String[] args) {
        Pembayaran cash = new Cash("INV-001", 100000, 120000);
        Pembayaran ew = new EWallet("INV-002", 150000, "user@ewallet", "123456");

        System.out.println(((Receiptable) cash).cetakStruk());
        System.out.println(((Receiptable) ew).cetakStruk());

    CreditBy.print("[NIM]", "[Nama Mahasiswa]");
    }
}
## Hasil Eksekusi
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/81b9e19e-6859-4bba-b48a-55228795a77f" />


## Analisis
Pada praktikum ini, abstraction diterapkan dengan menjadikan Pembayaran sebagai abstract class yang mendefinisikan struktur umum pembayaran. Setiap metode pembayaran memiliki cara perhitungan biaya dan proses yang berbeda sehingga method biaya() dan prosesPembayaran() dibuat abstrak dan diimplementasikan oleh subclass.

Class Cash dan EWallet mewarisi Pembayaran dan memberikan implementasi spesifik sesuai kebutuhan masing-masing. Selain itu, penggunaan interface Validatable dan Receiptable memungkinkan penerapan multiple inheritance, di mana EWallet dapat memiliki kemampuan validasi dan pencetakan struk secara bersamaan.

Dibandingkan praktikum minggu sebelumnya (polymorphism), pada praktikum ini fokus diperluas dengan pemisahan antara kontrak (interface) dan kerangka dasar (abstract class). Kendala yang dihadapi adalah memahami kapan menggunakan abstract class dan kapan menggunakan interface, yang diatasi dengan melihat kebutuhan shared state dan kemampuan lintas kelas.

## Kesimpulan
Dari praktikum ini dapat disimpulkan bahwa penggunaan abstract class dan interface sangat membantu dalam menerapkan konsep abstraction pada sistem berbasis OOP. Abstract class memungkinkan penyediaan struktur dan perilaku dasar, sedangkan interface memungkinkan penerapan kemampuan tambahan dan multiple inheritance. Dengan pendekatan ini, sistem Agri-POS menjadi lebih modular, fleksibel, dan mudah dikembangkan di masa depan.

## Quiz
1. Jelaskan perbedaan konsep dan penggunaan abstract class dan interface.
Abstract class digunakan untuk merepresentasikan kelas dasar yang memiliki state (field) dan perilaku umum yang dapat diwariskan oleh subclass. Abstract class dapat memiliki method abstrak dan non-abstrak, serta cocok digunakan ketika terdapat kesamaan struktur dan logika dasar antar kelas turunan.
Interface digunakan untuk mendefinisikan kontrak atau kemampuan yang harus dimiliki oleh suatu kelas tanpa memaksakan hierarki tertentu. Interface tidak menyimpan state (kecuali konstanta) dan mendukung multiple inheritance, sehingga cocok untuk mendefinisikan perilaku lintas kelas yang tidak selalu berada dalam satu garis keturunan.

2. Mengapa multiple inheritance lebih aman dilakukan dengan interface pada Java?
Multiple inheritance lebih aman dilakukan dengan interface karena interface tidak memiliki implementasi state dan tidak menyebabkan konflik pewarisan seperti diamond problem. Java membatasi pewarisan class hanya satu superclass untuk menghindari ambiguitas method dan field. Dengan interface, sebuah class dapat mengimplementasikan banyak kontrak perilaku tanpa risiko konflik implementasi, sehingga desain sistem menjadi lebih aman dan terkontrol.

3. Pada contoh Agri-POS, bagian mana yang paling tepat menjadi abstract class dan mana yang menjadi interface? Jelaskan alasannya.
Pada contoh Agri-POS, bagian yang paling tepat dijadikan abstract class adalah Pembayaran karena memiliki state bersama seperti invoiceNo dan total, serta perilaku dasar yang sama untuk semua jenis pembayaran.
Sementara itu, Validatable dan Receiptable paling tepat dijadikan interface karena keduanya merepresentasikan kemampuan tambahan (validasi dan pencetakan struk) yang tidak semua jenis pembayaran harus miliki. Dengan menggunakan interface, kelas seperti EWallet dapat mengimplementasikan lebih dari satu kemampuan tanpa terikat pada satu hierarki class.
