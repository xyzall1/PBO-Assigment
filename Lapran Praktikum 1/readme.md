# <h1 align="center">Laporan Praktikum Modul Priority dan Queue</h1>
<p align="center">Rosa Nur Aliana Sawafi</p>

## Dasar Teori
1. Pengertian Queue & Heap
    - Pengertian Queue
    Priority Queue merupakan struktur data khusus yang memungkinkan kita dapat menyimpan elemen-elemen dengan nilai prioritas tertentu [1]. Konsep dasar Priority Queue mirip dengan antrean biasa, namun perbedaan adalah setiap elemen dalam Proirity Queue memilki nilai prioritas yang menentukan urutan elemen saat diambil. Elemen dengan nilai prioritas tertinggi diambil terlebih dahulu, bukan elemen yang paling lama berada dalam antrean [5].

    - Pengertian Heap
    Heap yaitu pohon biner lengkap atau hampiir lengkap yang memenuhi atau struktur data unik yang terutama digunakan saat mengelola kumpulan data.

        Heap sendiri dapat divisualisasikan sebagai hampir selesai pohon biner, dan beroperasi berdasarkan aturan ketat yang menjadikannya salah satu pilihan optimal dalam hal tugas seperti metode pengurutan, antrean prioritas, atau program penjadwalan. 
        - Pohon biner yaitu struktur di mana simpul induk paling banyak dapat mempunyai dua simpul anak.
        - Struktur data heap selesai jika, untuk ketinggalan tertentu, semua level terisi sleruuhnya, kecuali kemungkinan level terakhir yang diisi dari kiri kanan [4].


2. Cara Kerja Priority Queue
    Priority Queue dapat diimplementasikan dengan menggunakan struktur data dasar seperti heap atau binary search tree yang memungkinkan kita untuk melakukan operasi penyisipan (insert) serta penghapusan (delete) dalam waktu logaritmik. Dengan struktur data ini, kita dapat dengan mudah mengakses elemen dengan nilai prioritas tertinggi tanpa harus memindahkan seluruh elemen lainnya  [2].

3. Penggunaan dalam Algoritma
    Priority Queue banyak digunakan dalam berbagai macam algoritma untuk memecahkan berbagai masalah. Beberapa penggunaan Priority Queue dalam algoritma antara lain:

    - Algoritma Dijkstra : digunakan untuk menemukan jalur terpendak dalam graf berbobot positif. Priority Queue memungkinkan pemilihan simpul berikutnya dengan bobot terkecil selama proses pencarian jalur terpendek.
    - Algoritma A (A-Star) : sering digunakan dalam permasalahan pencarian jarak terpendek dengan heuristik. Priority Queue membantu memilih simpul berikutnya berdasarkan nilai fungsi heuristik serta jarak yang sudah dilalui.
    - Algoritma Huffman : digunakan dalam kompresi data, di mana elemen-elemen dengan frekuensi kemunculan yang lebih tinggi diberikan prioritas lebih tinggi saat pembuatan pohon Huffman.
    - Penjadwalan Tugas : Prority Queue membantu dalam menentukan urutan penjadwalan tugas berdasarkan prioritas yang telah digunakan [3].
    
4. Jenis-jenis Heap
Adapun jenis-jenis heap diantaranya :
- Max-Heap : kunci atau nilai yang ada di simpul manapun harus lebih besar dari kunci/nilai yang ada di kedua simpul anaknya. Kunci terbesar ada di simpul akar (root node) [6].

    ![image](https://github.com/xyzall1/Struktur-Data-Assigment/assets/161272189/110c8bce-20eb-4861-b658-b5298733b43f)

- Min-Heap : merupakan kunci yang ada di simpul di mana pun harus lebih kecil dari kunci yang ada di kedua anaknya. Kunci terkecil ada di simpul akar.

    ![image](https://github.com/xyzall1/Struktur-Data-Assigment/assets/161272189/7a448356-9f92-4aa8-ae63-dc139f777795)

5. Operasi-operasi pada Struktur Data Heap
Operasi umum yang terlibat dalam heap di antaranya:
- Heapify : Proses untuk mengatur ulang heap untuk mempertahankan prpoperti heap.
- Find-max (Find - min) : Menemukan item maksimum dari max - heap, atau item minuman dari min-heap.
- Insertion : Menambahkan item baru di heap.
- Delection : Mengahapus item dari heap.
- Extract Min-Max : Mengembalikan dan menghapus elemen maksimum atau minimum masing-masing di max-heap serta min-heap.

6. Karakteristik Struktur Data Heap
- Sistem menetapkan heap identifier unik untuk setiap heap dalam grup aktivasi. Heap identifier untuk heap default selalu bernilai nol
- Ukuran heap diperluas secara dinamis untuk memenuhi permintaan alokasi. Ukuran maksimum heap adalah (4GB – 512KB). Ukuran tersebut adalah ukuran heap maksimum jika jumlah total alokasi (pada satu waktu) tidak melebihi 128.000.
- Ukuran maksimum alokasi tunggal apa pun dari heap dibatasi hingga (16MB – 64KB) [6].


## Guided 

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

#### Interpretasi
Kode di atas menggunakan kode dengan struktur data heap. Berikut penjelasan beberapa fungsi dari kode di atas seperti:

- parent(int i) : diguankan untuk mengembalikan indeks induk dari node pada indeks 'i' yang ada pada dalam heap biner.
- leftChild(int i) : bergungsi untuk mengembalikan indeks dari arah kiri lalu node pada indels 'i' dalam heap biner pula.
- rightChild(int i) : digunakan untuk mengembalikan indeks dari kanan lalu node pada indeks 'i' dalam heap biner.
- shiftUpDown(int i) : berguna untuk mempertahankan properti heap dengan setelan menghapus elemen dengan prioritas tertinggi.
- insert(int p) : digunakan untuk memasukkan elemen baru dengan prioritas 'p' ke dalam antrean prioritas.
- extractMax() : digunakan untuk menghapus dan mengembalikan elemen prioritas yang berada dalam urutan tertinggi dari antrean proritas.
- changePriority(int  i, int p) : berfungsi untuk mengubah elemen pada indeks 'i' menjadi 'p'
- getMax() : berfungsi untuk mengembalikan proritas elemen tertinggi dari antrean prioritas.
- remove(int i) : digunakan untuk menghapus elemen indeks pada 'i' dari antrean prioritas.

#### Output:
![Guided 1](https://github.com/xyzall1/Struktur-Data-Assigment/assets/161272189/06560732-ea45-4f64-a59f-8435d7ded04f)

Pada output di atas akan ditampilkan sebuah sebuah priority queue yang berisikan [45 31 14 13 20 7 11 12 7] lalu dalam node tersebut akan dicari nilai maksimal prioritas nya yaitu ditemukan 45, setelah itu node akan di ekstrak untuk nilai maksimum setelah itu node akan merubah prioritas yang terbaru serta menjadi susunan [49 20 31 13 7 7 11 12] setelah itu kode akan menjalankan penghapusan elemen menjadi [49 12 31 20 7 7 11].

## Unguided 

### 1. Modifikasi guided di atas yang mana heap dikonstruksi secara manual berdasarkan user.

```C++
#include <iostream>
#include <algorithm>

int H[50];
int heapSize = -1;

int parent(int i) {
    return (i - 1) / 2;
}

int leftChild(int i) {
    return ((2 * i) + 1);
}

int rightChild(int i) {
    return ((2 * i) + 2);
}

void shiftUp(int i) {
    while (i > 0 && H[parent(i)] < H[i]) {
        std::swap(H[parent(i)], H[i]);
        i = parent(i);
    }
}

void shiftDown(int i) {
    int maxIndex = i;
    int l = leftChild(i);
    if (1 <= heapSize && H[l] > H[maxIndex]) {
        maxIndex = 1;
    }
    int r = rightChild(i);
    if (r <= heapSize && H[r] > H[maxIndex]) {
        maxIndex = r;
    }
    if (i != maxIndex) {
        std::swap(H[i], H[maxIndex]);
        shiftDown(maxIndex);
    }
}

void insert(int p) {
    heapSize = heapSize + 1;
    H[heapSize] = p;
    shiftUp(heapSize);
}

int extractMax() {
    int result = H[0];
    H[0] = H[heapSize];
    heapSize = heapSize - 1;
    shiftDown(0);
    return result;
}

void changePriority(int i, int p) {
    int oldp = H[i];
    H[i] = p;
    if (p > oldp) {
        shiftUp(i);
    } else {
        shiftDown(i);
    }
}

int getMax() {
    return H[0];
}

void remove(int i) {
    H[i] = getMax() + 1;
    shiftUp(i);
    extractMax();
}

int main() {
    int n;
    std::cout << "Input the number of elements: ";
    std::cin >> n;

    for (int i = 0; i < n; ++i) {
        int p;
        std::cout << "Input element " << i + 1 << ": ";
        std::cin >> p;
        insert(p);
    }

    std::cout << "Priority Queue : ";
    for (int i = 0; i <= heapSize; ++i) {
        std::cout << H[i] << " ";
    }    
    std::cout << "\n";

    std::cout << "Node with maximum priority : " << extractMax() << "\n";

    std::cout << "Priority queue after extracting maximum : ";
    for (int i = 0; i <= heapSize; ++i) {
        std::cout << H[i] << " ";
    }
    std::cout << "\n";

    int i;
    std::cout << "Input the index of the element to change priority: ";
    std::cin >> i;
    int p;
    std::cout << "Input the new priority: ";
    std::cin >> p;
    changePriority(i, p);

    std::cout << "Priority queue after priority change : ";
    for (int i = 0; i <= heapSize; ++i) {
        std::cout << H[i] << " ";
    }
    std::cout << "\n";
    
    std::cout << "Input the index of the element to remove: ";
    std::cin >> i;
    remove(i);

    std::cout << "Priority queue after removing the element : ";
    for (int i = 0; i <= heapSize; ++i) {
        std::cout << H[i] << " ";
    }
    return 0;
}
```
#### Interpretasi 
Kode di atas merupakan kode yang menerangkan tentang struktur data Prioroty Queue yang menggunakan heap. Heap sendiri digunakan untuk menampung elemen dengan prioritas yang berbeda, serta operasi-operasi seperti penghapusan serta penggantian prioritas lalu penghapusan elemen dapat dilakukan untuk menghemat waktu dengan yang lebih singkat.
Penjabaran kode yang ada dalam data :
- insert(int p) : fungsi ini digunakan untuk menambahkan elemen baru ke dalam prioritas heap yang dialankan. Elemen baru nantinya akan ditaruh ke posisi proritas lalu pada fungsi shiftUp akan digunakan untuk menjaga struktur heap.
- extractMax() : Digunakan untuk menghapus elemen dengan prioritas yang paling atas dari heap lalu nantunya akan mengembalikan nilai heap sendiri. Elemen yang dihapus tadi akan digantikan dengan elemen terakhir di heap serta fungsi sjiftDown akan digunakan untuk menjaga struktur heap.
- changePriority(int i, int p) : Berguna untuk mengubah proritas yang sudah disediakan oleh heap. Elemen yang diutamakan inilah yang akan digantikan dengan prioritas bary serta fungsi shiftUp serta shiftDown untuk menjaga strukturnya.
- remove(int i) : fungsi ini diguakan untuk menghapus elemen yang diberikan. Elemen yang dihapus akan menggantikan dengan elemen terakhir di heap serta fungsi shiftDown untuk memastikan struktyrnya.
Lalu kode ini akan menjalankan seluruh operasi dengan menggunakan fungsi main

#### Output:
![unguided 1](https://github.com/xyzall1/Struktur-Data-Assigment/assets/161272189/ca1a982e-6674-4813-886f-01ecd49327ae)

Kode di atas akan menampilkan sebuah output berupa heap nya akan diinput manual oleh user. Pertama kita akan disuguhkan pesan "Input the number of elements" di sini kita diperintah untuk memasukkan jumlah elemen, kemudian akan muncul pesan "Input element" yang nantinya user diperintah untuk memasukkan elemen sampai dnegan jumlan elemen yang dimasukkan pertama kali tadi. Selanjutnya akan ditampilkan node tadi setelah itu akan dicari maximum priority yaitu 45. Kemudian node akan di extract setelah itu kita diberikan perintah untuk mengubah nilai dengan memasukkan elemen dan kita diarahkan untuk input nilai prioritas terbaru yaitu 49. Kemudian prority queue akan berubah menjadi [49 20 31 13 7 7 13 12] lalu kita akan menghapus elemen ke 3 serta hasil akhirnya yaitu [ 49 12 31 20 7 7 11].

## Kesimpulan
1. Priority Queue merupakan struktur data khusus yang memungkinkan kita dapat menyimpan elemen-elemen dengan nilai prioritas tertentu. Konsep dasar Priority Queue mirip dengan antrean biasa, namun perbedaan adalah setiap elemen dalam Proirity Queue memilki nilai prioritas yang menentukan urutan elemen saat diambil. Elemen dengan nilai prioritas tertinggi diambil terlebih dahulu, bukan elemen yang paling lama berada dalam antrean.

2.  Heap yaitu pohon biner lengkap atau hampir lengkap yang memenuhi atau struktur data unik yang terutama digunakan saat mengelola kumpulan data.


3. Cara Kerja Priority Queue yaitu dnegan Priority Queue dapat diimplementasikan dengan menggunakan struktur data dasar seperti heap atau binary search tree yang memungkinkan kita untuk melakukan operasi penyisipan (insert) serta penghapusan (delete) dalam waktu logaritmik. Dengan struktur data ini, kita dapat dengan mudah mengakses elemen dengan nilai prioritas tertinggi tanpa harus memindahkan seluruh elemen lainnya.


4. Penggunaan dalam algoritma terbagi menjadi empat yaitu : algoritma dijkstra, algoritma A (A-Star), algoritma Huffman, lalu dengan penjadwalan tugas.

5. Jenis Heap sendiri ada dua yaitu Max Heap dan Min Heap.

6. Operasi Heap ada berupa, Heapify, Find-Max, Insertion, Delection, Extract.

7. Karakterisitk Heap seperti, Sistem menetapkan heap identifier unik untuk setiap heap dalam grup aktivasi, ukuran heaps dapat diperluas secara dinamis, serta ukuran maksimum yaitu dinatasi hingga (16 MB - 64 KB).

## Referensi
[1] K., Roby, 2018 "Artikel Struktur Data", Universitas Mitra Indonesia, Sistem Informasi

[2] Goodrich, Tamassia, Mount. Data Structure
and Algorithms in C++, Wiley, 2004.

[3] Munir, Rinaldi. Diktat Kuliah IF2251 Strategi
Algoritmik, 2005.

[4] Schildt, Herbert, The Complete Reference
Java, Mc.Graw Hill, 2005.

[5] Sedgewick, Robert. Algorithms in C, 1990. 

[6] Trivusi, "Struktur Data Heap: Pengertian, Karakteristik, dan operasinya", 2023. Diakses pada 20 Mei 2024 dari https://www.trivusi.web.id/2023/01/struktur-data-heap.html 
