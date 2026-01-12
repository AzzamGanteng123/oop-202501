# Laporan Praktikum Minggu 7
Topik:Java Collections dan Implementasi Keranjang Belanja (Shopping Cart)

## Identitas
- Nama  : Azzam Zain Zaidan Sudiyono
- NIM   : 240202854
- Kelas : 3IKKA

## Tujuan
Tujuan dari praktikum ini adalah agar mahasiswa mampu memahami dan menerapkan Java Collections Framework, khususnya penggunaan List (ArrayList) dan Map (HashMap) untuk mengelola data objek secara dinamis, serta mengimplementasikannya dalam studi kasus keranjang belanja (shopping cart) pada sistem Agri-POS.

## Dasar Teori
-Java Collections Framework menyediakan struktur data siap pakai untuk menyimpan dan mengelola kumpulan objek secara efisien.
-List (ArrayList) menyimpan data secara terurut dan memperbolehkan elemen duplikat.
-Map (HashMap) menyimpan data dalam bentuk pasangan key–value dan cocok untuk pengelolaan data berbasis kuantitas.
-Collections mendukung operasi dasar seperti tambah, hapus, dan iterasi data.
-Penggunaan collection yang tepat dapat meningkatkan efisiensi dan kejelasan kode dalam aplikasi POS.

## Langkah Praktikum
-Membuat class Product sebagai representasi data produk dengan atribut kode, nama, dan harga.
-Mengimplementasikan class ShoppingCart menggunakan ArrayList<Product> untuk menyimpan produk.
-Membuat method untuk menambah produk, menghapus produk, menampilkan isi keranjang, dan menghitung total harga.
-Mengimplementasikan alternatif ShoppingCartMap menggunakan HashMap<Product, Integer> untuk menangani quantity produk.
-Membuat class MainCart sebagai program utama untuk menguji fungsi keranjang belanja.
-Menjalankan program dan mengamati hasil eksekusi.
-Menyimpan screenshot hasil eksekusi ke folder screenshots

## Kode Program
Product.java
package com.upb.agripos;

public class Product {
    private final String code;
    private final String name;
    private final double price;

    public Product(String code, String name, double price) {
        this.code = code;
        this.name = name;
        this.price = price;
    }

    public String getCode() { return code; }
    public String getName() { return name; }
    public double getPrice() { return price; }
}

ShoppingCart.java
package com.upb.agripos;

import java.util.ArrayList;

public class ShoppingCart {
    private final ArrayList<Product> items = new ArrayList<>();

    public void addProduct(Product p) { items.add(p); }
    public void removeProduct(Product p) { items.remove(p); }

    public double getTotal() {
        double sum = 0;
        for (Product p : items) {
            sum += p.getPrice();
        }
        return sum;
    }

    public void printCart() {
        System.out.println("Isi Keranjang:");
        for (Product p : items) {
            System.out.println("- " + p.getCode() + " " + p.getName() + " = " + p.getPrice());
        }
        System.out.println("Total: " + getTotal());
    }
}

ShoppingCartMap.java
package com.upb.agripos;

import java.util.HashMap;
import java.util.Map;

public class ShoppingCartMap {
    private final Map<Product, Integer> items = new HashMap<>();

    public void addProduct(Product p) { items.put(p, items.getOrDefault(p, 0) + 1); }

    public void removeProduct(Product p) {
        if (!items.containsKey(p)) return;
        int qty = items.get(p);
        if (qty > 1) items.put(p, qty - 1);
        else items.remove(p);
    }

    public double getTotal() {
        double total = 0;
        for (Map.Entry<Product, Integer> entry : items.entrySet()) {
            total += entry.getKey().getPrice() * entry.getValue();
        }
        return total;
    }

    public void printCart() {
        System.out.println("Isi Keranjang (Map):");
        for (Map.Entry<Product, Integer> e : items.entrySet()) {
            System.out.println("- " + e.getKey().getCode() + " " + e.getKey().getName() + " x" + e.getValue());
        }
        System.out.println("Total: " + getTotal());
    }
}

Main.java
package com.upb.agripos;

public class MainCart {
    public static void main(String[] args) {
        System.out.println("Hello, I am [Nama]-[NIM] (Week7)");

        Product p1 = new Product("P01", "Beras", 50000);
        Product p2 = new Product("P02", "Pupuk", 30000);

        ShoppingCart cart = new ShoppingCart();
        cart.addProduct(p1);
        cart.addProduct(p2);
        cart.printCart();

        cart.removeProduct(p1);
        cart.printCart();
    }
}


## Hasil Eksekusi
<img width="1918" height="1079" alt="image" src="https://github.com/user-attachments/assets/73819eef-a6cd-4ce8-8b46-9f640b179063" />


## Analisis
Pada praktikum ini, ArrayList digunakan untuk menyimpan daftar produk dalam keranjang belanja. Setiap kali produk ditambahkan atau dihapus, isi collection langsung berubah secara dinamis tanpa perlu menentukan ukuran awal. Perhitungan total dilakukan dengan melakukan iterasi pada seluruh elemen di dalam list.

Sebagai pengembangan, digunakan HashMap untuk menyimpan pasangan produk dan jumlah (quantity). Pendekatan ini lebih efisien untuk kasus pembelian produk yang sama lebih dari satu kali karena tidak perlu menyimpan objek produk secara berulang. Total harga dihitung dengan mengalikan harga produk dengan quantity masing-masing.

Dibandingkan dengan praktikum sebelumnya yang berfokus pada abstraction dan interface, praktikum ini lebih menekankan pada pengelolaan data dan efisiensi struktur data. Kendala yang dihadapi adalah pemilihan collection yang tepat untuk kebutuhan tertentu, yang diatasi dengan membandingkan kelebihan ArrayList dan HashMap dalam konteks keranjang belanja.

## Kesimpulan
Dari praktikum ini dapat disimpulkan bahwa Java Collections Framework sangat membantu dalam pengelolaan data aplikasi POS. Penggunaan ArrayList cocok untuk penyimpanan data sederhana, sedangkan HashMap lebih efektif untuk pengelolaan data berbasis quantity. Dengan memilih collection yang tepat, sistem Agri-POS menjadi lebih efisien, fleksibel, dan mudah dikembangkan.

## Quiz
1. Jelaskan perbedaan mendasar antara List, Map, dan Set.
-List menyimpan kumpulan data secara terurut dan mengizinkan duplikasi elemen.
-Set menyimpan data tanpa duplikasi dan umumnya tidak menjamin urutan elemen.
-Map menyimpan data dalam bentuk pasangan key–value, di mana setiap key harus unik dan digunakan untuk mengakses value dengan cepat.

2. Mengapa ArrayList cocok digunakan untuk keranjang belanja sederhana?
ArrayList cocok digunakan untuk keranjang belanja sederhana karena mudah digunakan, mendukung penyimpanan data secara dinamis, dan memungkinkan elemen duplikat. Hal ini sesuai untuk kasus di mana setiap produk ditambahkan satu per satu tanpa perlu pengelolaan quantity secara khusus.

3. Bagaimana struktur Set mencegah duplikasi data?
Set mencegah duplikasi data dengan menggunakan mekanisme pengecekan kesamaan objek melalui method equals() dan hashCode(). Jika terdapat objek baru yang dianggap sama dengan objek yang sudah ada, maka objek tersebut tidak akan ditambahkan ke dalam Set.

4. Kapan sebaiknya menggunakan Map dibandingkan List? Jelaskan dengan contoh.
Map sebaiknya digunakan ketika data perlu diakses berdasarkan key unik atau ketika setiap data memiliki pasangan nilai tertentu.
Contohnya pada keranjang belanja dengan quantity, Map<Product, Integer> lebih efektif karena satu produk hanya disimpan sekali sebagai key, sementara jumlah pembeliannya disimpan sebagai value, sehingga pengelolaan data menjadi lebih efisien dibandingkan List.
