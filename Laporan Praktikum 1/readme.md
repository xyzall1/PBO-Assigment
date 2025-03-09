# <h1 align="center">Laporan Praktikum (Object-Oriented Programming/OOP)</h1>
<p align="center">Rosa Nur Aliana Sawafi</p>

## Dasar Teori
1. Pemograman Berorientasi Objek atau (Object-Oriented Programming/OOP)
    - Pengertian 
    Pemrograman Berorientasi Objek (Object-Oriented Programming/OOP) adalah paradigma pemrograman yang berfokus pada konsep objek, di mana setiap objek memiliki atribut (data) dan metode (fungsi) untuk berinteraksi. OOP memungkinkan pengembangan perangkat lunak yang lebih modular, fleksibel, serta mudah dipelihara dan dikembangkan.

    - Konsep Dasar PBO atau (Object-Oriented Programming/OOP)
    OOP didasarkan pada beberapa konsep utama yang membentuk fondasi dalam pengembangannya, yaitu:

        - Class: Merupakan cetak biru (blueprint) atau template untuk membuat objek. Class mendefinisikan atribut (variabel) dan metode (fungsi) yang akan dimiliki oleh objek.
        - Object: Merupakan instance dari sebuah class. Objek adalah entitas nyata yang memiliki karakteristik (atribut) dan perilaku (metode) sesuai dengan definisi pada class.
        - Encapsulation: Konsep yang menyembunyikan detail implementasi suatu objek dan hanya mengekspos bagian yang diperlukan kepada pengguna, sehingga meningkatkan keamanan dan keteraturan kode.
        - Inheritance: Konsep pewarisan di mana sebuah class dapat mewarisi atribut dan metode dari class lain, memungkinkan kode lebih terstruktur dan dapat digunakan kembali.
        - Polymorphism: Konsep yang memungkinkan satu metode atau fungsi memiliki berbagai bentuk dan dapat digunakan untuk berbagai tipe data yang berbeda, sehingga meningkatkan fleksibilitas dalam pengembangan sistem.
        - Abstraction: Konsep yang menyederhanakan kompleksitas dengan hanya menampilkan informasi yang relevan kepada pengguna, sementara detail implementasi disembunyikan, sehingga mempermudah penggunaan dan pemeliharaan sistem.

2. Penjelasan Kelas BankAccount
    Pada program ini, terdapat kelas BankAccount yang merepresentasikan sebuah akun bank. Kelas ini memiliki atribut utama, yaitu:

    - Nama pemilik akun, yang menyimpan identitas pemilik rekening.
    - Saldo, yang menunjukkan jumlah uang yang tersedia di akun tersebut.
    Selain atribut, kelas ini juga memiliki metode-metode untuk melakukan operasi perbankan, seperti:

    - Deposit → Menambahkan saldo ke dalam akun.
    - Tarik Tunai → Mengurangi saldo dari akun jika jumlah saldo mencukupi.
    - Cek Saldo → Menampilkan jumlah saldo saat ini.

3. Kelas Latihanguided (Main)
    Program utama berfungsi sebagai penggerak atau eksekutor dari sistem akun bank yang telah dibuat. Dalam kelas ini:

    - Dibuat dua objek dari kelas BankAccount, yaitu satu akun untuk pemilik bernama Alice dan satu lagi untuk Abdul.
    - Dilakukan beberapa transaksi, seperti setoran uang, penarikan uang, dan transfer saldo antara dua akun.
    - Menampilkan saldo akhir, untuk memastikan bahwa semua transaksi berjalan sesuai harapan.

4. Hubungan antara Kelas dan Objek dalam Program
    +------------+---------------------------------------------------------------+
    | Konsep     | Penjelasan dalam Program                                      |
    +------------+---------------------------------------------------------------+
    | Class      | BankAccount adalah blueprint yang mendefinisikan struktur dan |
    |            | perilaku akun bank.                                           |
    +------------+---------------------------------------------------------------+
    | Object     | akun1 dan akun2 adalah objek dari kelas BankAccount, yang     |
    |            | merepresentasikan akun milik Alice dan Abdul.                 |
    +------------+---------------------------------------------------------------+
    | Atribut    | namaPemilik dan Saldo menyimpan data setiap akun bank.        |
    +------------+---------------------------------------------------------------+
    | Metode     | deposit(), tariktunai(), dan tampilansaldo() digunakan untuk  |
    |            | memodifikasi atau menampilkan data objek.                     |
    +------------+---------------------------------------------------------------+
    | Instansiasi| new BankAccount("Alice", 1000); membuat objek baru dengan     |
    |            | nilai awal.                                                   |
    +------------+---------------------------------------------------------------+


## Guided 
### Class

```Java
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package latihanguided;

/**
 *
 * @author ASUS
 */
public class BankAccount {
    // deklarasi variable
    String namaPemilik;
    double Saldo;
    
    // kontruktor akun bank (inisiasi)
    BankAccount(String nama,  double saldoAwal){
        namaPemilik = nama;
        Saldo = saldoAwal;
    }
    
    //metode take uang dari rekening
    void deposit(double jumlah) {  // Menggunakan jumlah sebagai parameter
    Saldo += jumlah;  // Pastikan Saldo sudah dideklarasikan di kelas
    System.out.println(namaPemilik + " menyetor " + jumlah + ". Saldo Sekarang: " + Saldo);
}
    
    // metode ambil uang
    void tariktunai (double jumlah){
        if (Saldo >= jumlah) {
            Saldo -= jumlah;
            System.out.println(namaPemilik + "menarik" + jumlah +
            "saldo sekarang " + Saldo);
        }else {
            System.out.println(namaPemilik + "gagal menarik " + jumlah +
            "tidak mencukupi ");
        }
    }
    
    //metode cek saldo uang
    
    void tampilansaldo() {
        System.out.println("Saldo " + namaPemilik + " : " + Saldo);
    }
}

```

### Main
```Java

/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Main.java to edit this template
 */
package latihanunguided;

/**
 *
 * @author ASUS
 */
public class Latihanunguided {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        
        BankAccount akun1 = new BankAccount("Alice", 1000);
        BankAccount akun2 = new BankAccount("Abdul", 500);
        
        // Melakukan transaksi
        akun1.deposit(200); // Alice menyetor 200
        akun2.tariktunai(300); // Abdul tarik tunai 300
        akun1.tariktunai(500); // Alice tarik tunai 500
        akun2.deposit(100); // Abdul menyetor 100
        
        // Transfer saldo
        akun1.transfer(akun2, 300); // Alice transfer 300 ke Abdul
        akun2.transfer(akun1, 200); // Abdul transfer 200 ke Alice
        
        // Menampilkan saldo akhir
        akun1.tampilansaldo(); // Menampilkan saldo Alice
        akun2.tampilansaldo(); // Menampilkan saldo Abdul
    }
    
}

```

#### Output:
![Image](https://github.com/user-attachments/assets/978613da-39d8-404f-b4b8-534d0b6690cc)

- Kelas digunakan untuk mendefinisikan atribut dan metode suatu entitas, dalam hal ini akun bank.
- Objek dibuat berdasarkan kelas dan memiliki data serta perilaku sendiri.
- Program ini menggunakan konsep OOP untuk merepresentasikan sistem perbankan sederhana, di mana setiap akun memiliki fungsi transaksi sendiri.
- Interaksi antar objek menunjukkan bagaimana data dalam suatu sistem dapat berubah dan dikelola dengan baik.



## Unguided 

### 1. Modifikasi program ini agar memiliki fitur transfer saldo antar akun bank.Buatlah metode tambahan dalam kelas BankAccount

### Class
```Java
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package latihanunguided;

/**
 *
 * @author ASUS
 */
public class BankAccount {
    // Deklarasi variabel
    String namaPemilik;
    double saldo;
    
    // Konstruktor akun bank (inisiasi)
    public BankAccount(String nama, double saldoAwal) {
        namaPemilik = nama;
        saldo = saldoAwal;
    }
    
    // Metode setor uang ke rekening
    void deposit(double jumlah) {
        saldo += jumlah;
        System.out.println(namaPemilik + " menyetor " + jumlah + ". Saldo sekarang: " + saldo);
    }
    
    // Metode tarik tunai
    void tariktunai(double jumlah) {
        if (saldo >= jumlah) {
            saldo -= jumlah;
            System.out.println(namaPemilik + " menarik " + jumlah + ". Saldo sekarang: " + saldo);
        } else {
            System.out.println(namaPemilik + " gagal menarik " + jumlah + ". Saldo tidak mencukupi.");
        }
    }
    
    // Metode cek saldo
    void tampilansaldo() {
        System.out.println("Saldo " + namaPemilik + " : " + saldo);
    }
    
    // Metode transfer saldo antar akun bank
    void transfer(BankAccount tujuan, double jumlah) {
        if (saldo >= jumlah) {
            saldo -= jumlah;
            tujuan.saldo += jumlah;
            System.out.println(namaPemilik + " mentransfer " + jumlah + " ke " + tujuan.namaPemilik + ".");
            System.out.println("Saldo " + namaPemilik + " sekarang: " + saldo);
            System.out.println("Saldo " + tujuan.namaPemilik + " sekarang: " + tujuan.saldo);
        } else {
            System.out.println(namaPemilik + " gagal mentransfer " + jumlah + ". Saldo tidak mencukupi.");
        }
    }
}

```

### Main
```Java
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Main.java to edit this template
 */
package latihanunguided;

/**
 *
 * @author ASUS
 */
public class Latihanunguided {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        
        BankAccount akun1 = new BankAccount("Alice", 1000);
        BankAccount akun2 = new BankAccount("Abdul", 500);
        
        // Melakukan transaksi
        akun1.deposit(200); // Alice menyetor 200
        akun2.tariktunai(300); // Abdul tarik tunai 300
        akun1.tariktunai(500); // Alice tarik tunai 500
        akun2.deposit(100); // Abdul menyetor 100
        
        // Transfer saldo
        akun1.transfer(akun2, 300); // Alice transfer 300 ke Abdul
        akun2.transfer(akun1, 200); // Abdul transfer 200 ke Alice
        
        // Menampilkan saldo akhir
        akun1.tampilansaldo(); // Menampilkan saldo Alice
        akun2.tampilansaldo(); // Menampilkan saldo Abdul
    }
    
}
```

#### Penjelasan Kelas dan Objek dalam Program BankAccount 
- Penjelasan BankAccount
    Kelas ini bertanggung jawab untuk merepresentasikan akun bank. Terdiri dari:

    - Atribut
        - namaPemilik: Menyimpan nama pemilik akun.
        - saldo: Menyimpan jumlah saldo dalam akun.
    - Metode (Fungsi)
        - deposit(double jumlah) → Menambah saldo akun.
        - tariktunai(double jumlah) → Mengurangi saldo jika cukup.
        - transfer(BankAccount tujuan, double jumlah) → Memindahkan saldo ke akun lain.
        - tampilansaldo() → Menampilkan saldo akun.
- Penjelasan Kelas Latihanunguided (Main)
    - Membuat objek akun bank untuk Alice dan Abdul.
    - Melakukan transaksi, seperti setoran, tarik tunai, dan transfer saldo.
    - Menampilkan saldo akhir setelah semua transaksi selesai.

#### Output:
![Image](https://github.com/user-attachments/assets/c57fa77d-2877-4ecb-9b78-9819d21dba0d)

- Kelas BankAccount digunakan sebagai template untuk membuat akun bank dengan fitur transaksi dasar.
- Objek akun1 dan akun2 merepresentasikan akun milik Alice dan Abdul.
- Metode dalam kelas memungkinkan objek untuk berinteraksi, seperti transfer saldo antar akun.
- Program ini menerapkan konsep OOP, seperti enkapsulasi dan interaksi antar objek.



## Kesimpulan
- OOP membuat pengembangan perangkat lunak lebih rapi, mudah dikelola, dan dikembangkan.
- Class dan Object membantu program lebih terstruktur dan bisa digunakan kembali.
- Kelas BankAccount sebagai template akun bank dengan fitur transaksi dasar.
- Enkapsulasi diterapkan agar data penting (namaPemilik, saldo) hanya bisa diubah lewat metode tertentu.
- Objek akun1 (Alice) dan akun2 (Abdul) punya atribut unik dan bisa berinteraksi.
- Metode deposit(), tariktunai(), dan transfer() merupakan contoh transaksi antar akun.
- transfer() menunjukkan bagaimana satu objek bisa mengubah atribut objek lain.
- Program menerapkan konsep OOP: enkapsulasi, instansiasi, dan interaksi antar objek.
- Sistem perbankan berbasis OOP lebih fleksibel dan efisien dalam pengelolaan akun.


## Referensi
[1] H. Schildt, Java: The Complete Reference, 11th ed. McGraw-Hill, 2018.
[2] Oracle, "Java Tutorials," 2023. [Online]. Available: https://docs.oracle.com/javase/tutorial/.

