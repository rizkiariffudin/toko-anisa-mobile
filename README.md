# toko_anisa

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

# Tugas 7: Elemen Dasar Flutter
## Apa perbedaan utama antara stateless dan stateful widget dalam konteks pengembangan aplikasi Flutter?

### Stateless Widget
- **Stateless Widget** adalah jenis widget di Flutter yang tidak memiliki keadaan internal (state). Artinya, setelah sebuah Stateless Widget dibuat dan dirender, ia tidak dapat diubah. Konten Stateless Widget hanya dapat didefinisikan pada saat pembuatan dan tidak dapat diubah selama widget berada di layar.
- Stateless Widget biasanya digunakan untuk tampilan yang tidak perlu mempertahankan data atau keadaan internal yang berubah. Contoh-contoh dari Stateless Widget adalah teks, gambar, ikon, tombol yang tidak memiliki perubahan dalam konten atau tampilan.
- Stateless Widget lebih efisien dalam hal kinerja karena mereka tidak memerlukan manajemen keadaan yang kompleks.

### Stateful Widget
- **Stateful Widget**, sebaliknya, adalah jenis widget yang memiliki keadaan internal (state) yang dapat berubah selama widget berada di layar. Ini berarti widget dapat diperbarui atau direbuild untuk mencerminkan perubahan keadaan.
- Stateful Widget umumnya digunakan untuk komponen yang harus mempertahankan data atau keadaan yang berubah, seperti formulir, daftar yang dapat digulir, atau aplikasi yang melibatkan interaksi pengguna yang kompleks.
- Stateful Widget memungkinkan pengembang untuk memperbarui tampilan berdasarkan perubahan data atau interaksi pengguna tanpa harus merender seluruh tampilan ulang. Ini dapat meningkatkan efisiensi dan responsifitas aplikasi.

Perbedaan utama antara keduanya adalah bahwa Stateless Widget tidak memiliki keadaan internal yang dapat berubah, sementara Stateful Widget memiliki keadaan yang dapat berubah dan diperbarui selama waktu. Pemilihan antara Stateless dan Stateful Widget tergantung pada kebutuhan aplikasi dan apakah komponen memerlukan pembaruan berdasarkan perubahan keadaan atau data.

Pengembang Flutter sering kali menggunakan kombinasi Stateless dan Stateful Widget untuk membangun aplikasi yang efisien dan responsif.

## Sebutkan seluruh widget yang kamu gunakan untuk menyelesaikan tugas ini dan jelaskan fungsinya masing-masing.

### MyHomePage
- `MyHomePage` adalah tampilan utama dalam aplikasi yang menggunakan `Scaffold` sebagai kerangka dasarnya. `Scaffold` menyediakan elemen-elemen UI dasar, termasuk `AppBar` di bagian atas halaman yang menampilkan judul aplikasi. Untuk mengatasi konten yang lebih besar dari layar, digunakan `SingleChildScrollView` yang memungkinkan halaman untuk discroll jika kontennya melebihi layar. `Padding` digunakan untuk menambahkan jarak di sekitar elemen-elemen anak, dan elemen-elemen anak diatur secara vertikal menggunakan `Column`.

### ShopCard
- `ShopCard` adalah widget yang menggambarkan kartu toko dalam aplikasi. Ini menggunakan `Material` untuk menerapkan efek desain Material dan memberikan latar belakang dengan warna yang sesuai dengan item toko. Untuk membuat area responsif terhadap sentuhan, seperti ketika di-klik, digunakan `InkWell`. Saat di-tap, widget ini menampilkan Snackbar. `Container` mengelilingi ikon dan teks pada kartu toko, memberikan padding, dan mengatur latar belakang warna. Terdapat juga widget `Icon` yang menampilkan ikon dengan warna putih dan ukuran tertentu, serta widget `Text` yang menampilkan nama item toko dari `ShopItem`.

### MyApp
- `MyApp` adalah widget yang mengatur konfigurasi dasar aplikasi. Ini menggunakan `MaterialApp` untuk mengatur judul aplikasi, tema keseluruhan aplikasi, dan halaman awal. Konfigurasi `title` digunakan untuk memberikan judul aplikasi, `theme` mengatur tema aplikasi dengan warna sesuai dengan tema Material Design 3.0, dan `home` mengatur `MyHomePage()` sebagai halaman utama aplikasi.

## Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial)
### Langkah 1: Membuat Proyek Flutter
- Buka _command prompt_ dan navigasikan ke direktori tujuan proyek Flutter.
- Gunakan perintah berikut untuk membuat proyek Flutter dengan nama "toko_anisa" dan pindah ke direktori proyek tersebut:
  ```bash
  flutter create toko_anisa
  cd toko_anisa
  ```
### Langkah 2: Menambahkan File `menu.dart`
- Buka folder `lib` dalam proyek `toko_anisa` dan buat file baru dengan nama "menu.dart".
### Langkah 3: Menyusun Kode
- Pertama, impor paket flutter/material.dart di bagian atas file menu.dart.
- Pindahkan kelas MyHomePage dan _MyHomePageState dari file main.dart ke dalam file menu.dart.
### Langkah 4: Mengimpor Fungsi dari `menu.dart`
- Di dalam file `main.dart`, tambahkan pernyataan untuk mengimpor fungsi yang diperlukan dari file `menu.dart` untuk menghindari kesalahan saat mengakses kelas dan fungsi dari file tersebut.
```dart
import 'package:toko_anisa/menu.dart';
```
### Langkah 5: Membuat Tombol-Tombol Sederhana
- Di dalam file `main.dart`, ubah konfigurasi MyHomePage dengan mengganti baris `MyHomePage(title: 'Flutter Demo Home Page')` menjadi `home: MyHomePage()`.
### Langkah 6: Mengubah `MyHomePage` menjadi _Stateless_
- Di dalam file `menu.dart`, ubah kelas `MyHomePage` dari stateful menjadi stateless dan sesuaikan kontennya.
```dart
class MyHomePage extends StatelessWidget {
  MyHomePage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      ...
    );
  }
}
```
- Jangan lupa untuk menghapus fungsi State yang ada di bawah widget stateless ini.
### Langkah 7: Mendefinisikan Atribut Tombol
- Di dalam kelas `MyHomePage`, tambahkan definisi atribut untuk tombol (ShopItem).
```dart
  class MyHomePage extends StatelessWidget {
  MyHomePage({Key? key}) : super(key: key);
  final List<ShopItem> items = [
    ShopItem("Lihat Item", Icons.checklist, Colors.amberAccent),
    ShopItem("Tambah Item", Icons.add_shopping_cart, Colors.deepOrangeAccent),
    ShopItem("Logout", Icons.logout, Colors.lightBlueAccent),
  ];
  ```
### Langkah 8: Mengubah Fungsi `Widget build`
- Di dalam kelas `MyHomePage`, ubah fungsi `Widget build` sesuai dengan konten yang diberikan.
```dart
-   @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text(
          'Toko Anisa',
        ),
      ),
      body: SingleChildScrollView(
        // Widget wrapper yang dapat discroll
        child: Padding(
          padding: const EdgeInsets.all(10.0), // Set padding dari halaman
          child: Column(
            // Widget untuk menampilkan children secara vertikal
            children: <Widget>[
              const Padding(
                padding: EdgeInsets.only(top: 10.0, bottom: 10.0),
                // Widget Text untuk menampilkan tulisan dengan alignment center dan style yang sesuai
                child: Text(
                  'Toko Anisa', // Text yang menandakan toko
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    fontSize: 30,
                    fontWeight: FontWeight.bold,
                  ),
                ),
              ),
              // Grid layout
              GridView.count(
                // Container pada card kita.
                primary: true,
                padding: const EdgeInsets.all(20),
                crossAxisSpacing: 10,
                mainAxisSpacing: 10,
                crossAxisCount: 3,
                shrinkWrap: true,
                children: items.map((ShopItem item) {
                  // Iterasi untuk setiap item
                  return ShopCard(item);
                }).toList(),
              ),
            ],
          ),
        ),
      ),
    );
  }
  ```
### Langkah 9: Menambahkan Fungsi `ShopCard`
- Tambahkan fungsi `ShopCard` untuk mendefinisikan tampilan tombol/card yang telah ditambahkan.
  Dengan langkah-langkah ini, Anda telah membuat aplikasi Flutter yang menampilkan tiga tombol dengan ikon dan teks, serta menampilkan _Snackbar_ ketika tombol ditekan.
```dart
- class ShopCard extends StatelessWidget {
  final ShopItem item;

  const ShopCard(this.item, {super.key}); // Constructor

  @override
  Widget build(BuildContext context) {
    return Material(
      color: item.color,
      child: InkWell(
        // Area responsive terhadap sentuhan
        onTap: () {
          // Memunculkan SnackBar ketika diklik
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(SnackBar(
                content: Text("Kamu telah menekan tombol ${item.name}!")));
        },
        child: Container(
          // Container untuk menyimpan Icon dan Text
          padding: const EdgeInsets.all(8),
          child: Center(
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Icon(
                  item.icon,
                  color: Colors.white,
                  size: 30.0,
                ),
                const Padding(padding: EdgeInsets.all(3)),
                Text(
                  item.name,
                  textAlign: TextAlign.center,
                  style: const TextStyle(color: Colors.white),
                ),
              ],
            ),
          ),
        ),
      ),
    );
  }
}
```

# Tugas 8: Flutter Navigation, Layouts, Forms, and Input Elements
## Jelaskan perbedaan antara `Navigator.push()` dan `Navigator.pushReplacement()`, disertai dengan contoh mengenai penggunaan kedua metode tersebut yang tepat!

### `Navigator.push()`
Metode `Navigator.push()` digunakan untuk menempatkan halaman baru di atas tumpukan navigasi. Ini menambahkan halaman baru ke tumpukan dan memungkinkan pengguna untuk kembali ke halaman sebelumnya dengan tombol kembali sistem atau perintah kembali yang sesuai.

**Contoh penggunaan:**
```dart
// Navigasi ke halaman kedua
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => SecondPage()),
);
```

### `Navigator.pushReplacement()`
Metode `Navigator.pushReplacement()` digunakan untuk menggantikan halaman saat ini dengan halaman baru. Ini menghapus halaman saat ini dari tumpukan dan menempatkan halaman baru di atasnya. Pengguna tidak dapat kembali ke halaman sebelumnya setelah menggunakan `pushReplacement()`.

**Contoh penggunaan:**
```dart
// Navigasi ke halaman kedua dan menggantikan halaman saat ini
Navigator.pushReplacement(
context,
MaterialPageRoute(builder: (context) => SecondPage()),
);
```
### **Perbedaan Utama:**
- `Navigator.push()` menambahkan halaman baru ke tumpukan, memungkinkan pengguna untuk kembali ke halaman sebelumnya.
- `Navigator.pushReplacement()` menggantikan halaman saat ini dengan halaman baru, menghapus halaman saat ini dari tumpukan.

### ***Contoh Penggunaan Bersamaan:**
Misalkan kita memiliki tiga halaman: `HomePage`, `SecondPage`, dan `ThirdPage`. Ketika pengguna menavigasi dari `HomePage` ke `SecondPage`, dan dari `SecondPage` ke `ThirdPage`, menggunakan `pushReplacement()` setelah `push()` pada saat yang sama, berikut contohnya:
```dart
// Navigasi dari HomePage ke SecondPage
Navigator.push(
context,
MaterialPageRoute(builder: (context) => SecondPage()),
);

// Navigasi dari SecondPage ke ThirdPage dan menggantikan SecondPage
Navigator.pushReplacement(
context,
MaterialPageRoute(builder: (context) => ThirdPage()),
);
```

## Jelaskan masing-masing layout widget pada Flutter dan konteks penggunaannya masing-masing!

### 1. **Container**
- **Deskripsi:** `Container` adalah widget dasar yang dapat mengandung widget lain dan memberikan kontrol terhadap propertinya seperti padding, margin, dan dekorasi.
- **Contoh Penggunaan:** Digunakan untuk mengelilingi widget lain dan mengatur propertinya seperti padding atau margin.

### 2. **Row dan Column**
- **Deskripsi:** `Row` dan `Column` adalah widget linier yang mengatur anak-anaknya secara horizontal (`Row`) atau vertikal (`Column`).
- **Contoh Penggunaan:** `Row` digunakan untuk menyusun widget secara horizontal, misalnya, untuk menempatkan beberapa ikon berdampingan. `Column` digunakan untuk menyusun widget secara vertikal, seperti menyusun teks dan gambar secara bertingkat.

### 3. **ListView**
- **Deskripsi:** `ListView` adalah widget scrollable yang mengatur anak-anaknya dalam daftar linier.
- **Contoh Penggunaan:** Digunakan untuk menampilkan daftar item yang dapat di-scroll, seperti daftar kontak atau pesan.

### 4. **Stack**
- **Deskripsi:** `Stack` adalah widget yang menempatkan anak-anaknya di atas satu sama lain.
- **Contoh Penggunaan:** Digunakan ketika Anda ingin menumpuk widget, misalnya, menempatkan teks di atas gambar.

### 5. **Expanded dan Flexible**
- **Deskripsi:** `Expanded` dan `Flexible` digunakan untuk memberikan fleksibilitas dalam tata letak.
- **Contoh Penggunaan:** `Expanded` digunakan untuk mengisi ruang yang tersisa dalam widget induk, sedangkan `Flexible` memberikan kontrol lebih besar terhadap proporsi ruang yang diambil oleh anak-anak dalam widget flex.

### 6. **GridView**
- **Deskripsi:** `GridView` adalah widget scrollable yang mengatur anak-anaknya dalam grid.
- **Contoh Penggunaan:** Digunakan untuk menampilkan item dalam grid, seperti galeri gambar atau aplikasi e-commerce dengan tampilan produk.

### 7. **Card**
- **Deskripsi:** `Card` adalah widget yang mengatur kontennya dalam bentuk kartu dengan sudut terbulat.
- **Contoh Penggunaan:** Digunakan untuk menampilkan informasi dalam format kartu, seperti kartu kontak atau kartu artikel.

### 8. **Wrap**
- **Deskripsi:** `Wrap` adalah widget yang mengatur anak-anaknya dalam baris dan kolom yang membungkus widget ketika tidak cukup ruang.
- **Contoh Penggunaan:** Digunakan ketika Anda ingin anak-anaknya berada dalam baris atau kolom, dan bungkus widget ketika mencapai batas lebar.

### 9. **SizedBox**
- **Deskripsi:** `SizedBox` memberikan dimensi tetap pada widget-nya.
- **Contoh Penggunaan:** Digunakan untuk memberikan ruang putih atau menentukan dimensi tetap pada suatu widget.

### 10. **AspectRatio**
- **Deskripsi:** `AspectRatio` mengatur lebar dan tinggi widget untuk mencapai rasio aspek tertentu.
- **Contoh Penggunaan:** Digunakan ketika Anda ingin mempertahankan rasio aspek tertentu pada suatu widget, misalnya, gambar.

### 11. **ConstrainedBox**
- **Deskripsi:** `ConstrainedBox` memberikan batasan ukuran maksimum dan minimum pada widget-nya.
- **Contoh Penggunaan:** Digunakan ketika Anda ingin membatasi ukuran widget, seperti memastikan suatu widget tidak lebih besar atau lebih kecil dari nilai tertentu.

### 12. **Positioned**
- **Deskripsi:** `Positioned` mengatur posisi anak-anaknya dalam suatu stack.
- **Contoh Penggunaan:** Digunakan untuk mengatur posisi relatif dari widget dalam suatu stack.

### 13. **Align**
- **Deskripsi:** `Align` mengatur posisi anak-anaknya relatif terhadap ukuran widget induk.
- **Contoh Penggunaan:** Digunakan untuk mengatur posisi anak-anak secara tepat dalam widget induk.

### 14. **IntrinsicHeight dan IntrinsicWidth**
- **Deskripsi:** `IntrinsicHeight` dan `IntrinsicWidth` memaksa anak-anaknya untuk memiliki tinggi atau lebar intrinsik.
- **Contoh Penggunaan:** Digunakan untuk memastikan widget memiliki tinggi atau lebar yang cukup untuk menampung kontennya.

### 15. **FlutterLogo**
- **Deskripsi:** `FlutterLogo` menampilkan logo Flutter yang dapat diatur ukurannya.
- **Contoh Penggunaan:** Digunakan untuk menampilkan logo Flutter dalam aplikasi.

Dalam pengembangan Flutter, penggunaan layout widget ini tergantung pada kebutuhan desain dan fungsionalitas spesifik dari aplikasi yang sedang dibangun.

## Sebutkan apa saja elemen input pada form yang kamu pakai pada tugas kali ini dan jelaskan mengapa kamu menggunakan elemen input tersebut!
- `TextFormField`: Saya menggunakan `TextFormField` dengan _input validation_ untuk menerima input teks seperti nama item, jumlah, dan deskripsi. Khusus untuk jumlah, saya lakukan validasi dengan percobaan parse menjadi `int`. TextFormField Cocok digunakan untuk data teks singkat.

## Bagaimana penerapan clean architecture pada aplikasi Flutter?
Clean Architecture adalah suatu pendekatan pengembangan perangkat lunak yang bertujuan untuk memisahkan konsep bisnis inti dari detail teknis implementasinya. Penerapan Clean Architecture pada aplikasi Flutter melibatkan struktur proyek yang terorganisir dengan baik dan pemisahan yang jelas antara lapisan-lapisan yang berbeda. Berikut adalah langkah-langkah umum untuk menerapkan Clean Architecture pada aplikasi Flutter:

### 1. Pemisahan Lapisan (Layer Separation):

#### Presentasi (Presentation Layer):
- Berisi widget-widget UI, tata letak, dan logika presentasi.
- Tidak boleh mengandung logika bisnis atau detail implementasi teknis.
- Mungkin menggunakan BLoC, Provider, atau arsitektur manajemen state lainnya.

#### Domain Layer:
- Berisi bisnis inti dan aturan domain.
- Tidak boleh tergantung pada detail implementasi teknis atau framework.
- Menggunakan objek entitas, nilai-nilai objek, aturan bisnis, dan interaksi antar entitas.

#### Data Layer:
- Berisi logika akses data dan implementasi teknis seperti API panggilan, basis data, atau penyimpanan lokal.
- Terisolasi dari detail presentasi dan domain.
- Mungkin menggunakan Repository Pattern untuk mengakses data.

### 2. Penggunaan Dependency Injection:
- Gunakan teknik dependency injection (DI) untuk memberikan dependensi ke kelas-kelas yang membutuhkannya.
- Ini membantu memastikan bahwa kelas tidak bertanggung jawab atas penciptaan atau manajemen dependensinya sendiri.

### 3. Repository Pattern:
- Implementasikan Repository Pattern untuk mengabstraksi dan mengisolasi logika akses data.
- Memungkinkan perubahan sumber data tanpa mempengaruhi lapisan bisnis.

### 4. Use Case atau Interactor:
- Gunakan Use Case atau Interactor untuk mengimplementasikan logika bisnis tingkat tinggi.
- Merepresentasikan operasi atau fitur yang dapat dilakukan dalam aplikasi.

### 5. Model-View-Presenter (MVP) atau Model-View-ViewModel (MVVM):
- Pilih pola desain yang sesuai untuk mengelola logika presentasi.
- MVP dan MVVM adalah dua opsi yang umum digunakan dalam aplikasi Flutter.

### 6. Unit Testing:
- Pastikan bahwa setiap lapisan dapat diuji secara terpisah dengan menggunakan unit test.
- Uji bisnis dan logika presentasi tanpa perlu mengakses infrastruktur atau sumber data nyata.

### 7. Konfigurasi Proyek:
- Konfigurasikan proyek Flutter dengan memisahkan file-file konfigurasi dan variabel lingkungan.
- Ini membantu dalam memisahkan konfigurasi dari logika aplikasi dan mempermudah manajemen konfigurasi untuk berbagai lingkungan (pengembangan, produksi, dll.).

### 8. Publikasi dan Pembaruan Dependensi:
- Publikasikan lapisan Domain sebagai paket publik.
- Hindari memiliki ketergantungan langsung antara lapisan Presentasi dan Data dengan menggunakan lapisan Domain sebagai interface.

### 9. Manajemen State:
- Pilih dan implementasikan solusi manajemen state yang sesuai seperti BLoC, Provider, atau Riverpod.
- Pastikan bahwa logika manajemen state terisolasi dari logika presentasi dan bisnis.

Dengan mengikuti prinsip-prinsip Clean Architecture, aplikasi Flutter dapat menjadi lebih mudah dipahami, dikembangkan, dan diuji. Penerapan ini memungkinkan perubahan dalam logika presentasi atau detail teknis tanpa memengaruhi bisnis inti dan sebaliknya.

##  Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial)
### *Refactoring* Sebelum Memulai Tugas 8

Sebelum memulai tugas 8, dilakukan *refactoring* pada kode program `menu.dart` dan `main.dart` yang telah dibuat pada tugas 7. Dua *folder* baru, yaitu `widgets` dan `screens`, dibuat di dalam direktori `lib`. *Folder* ini akan digunakan untuk menyimpan *widget* dan *screen* yang akan dibuat selanjutnya. Kode program `menu.dart` dipindahkan ke direktori `lib/screens`. Selanjutnya, `MenuItem` dan `MenuCard` dipisahkan ke dalam *widget* baru bernama `shop_card.dart`, yang ditempatkan di direktori `lib/widgets`.

### Membuat Halaman Form Tambah Item Baru

Setelah *refactoring* selesai, dilakukan pembuatan halaman form untuk menambah item baru berdasarkan model yang telah dibuat di Django. Dibuat *screen* baru bernama `shoplist_form.dart` di dalam direktori `lib/screens`. 
Lalu, file `shoplist_form.dart` diisi dengan kode yang sesuai.

### Mengarahkan pengguna ke halaman form tambah item baru
Setelah halaman form tambah item baru dibuat, kita akan mengarahkan pengguna ke halaman tersebut ketika tombol `Tambah Item` pada halaman utama ditekan. Untuk mengarahkan pengguna ke halaman form tambah item baru, kita perlu mengubah kode program `shop_card.dart` dan `menu.dart` sehingga menggunakan `Navigator.push()`.

### Memunculkan data sesuai isi dari formulir yang diisi dalam sebuah `pop-up` setelah menekan tombol `Save` pada halaman formulir tambah item baru
Untuk memunculkan data setelah menekan tombol `Save` pada halaman formulir tambah item baru, kita perlu menambahkan `onPressed: ()` pada `shoplist_form.dart` yang akan memunculkan data sesuai isi dari formulir yang diisi dalam sebuah `pop-up`.

### Membuat sebuah drawer pada aplikasi
Untuk membuat sebuah drawer pada aplikasi, kita perlu membuat sebuah *widget* bernama `left_drawer.dart` pada direktori `lib/widgets`. Kode program `left_drawer.dart` adalah sebagai berikut:
```dart
import 'package:flutter/material.dart';
import 'package:toko_anisa/screens/menu.dart';
import 'package:toko_anisa/screens/shoplist_form.dart';
import 'package:toko_anisa/screens/show_item.dart';

class LeftDrawer extends StatelessWidget {
  const LeftDrawer({super.key});

  @override
  Widget build(BuildContext context) {
    return Drawer(
      child: ListView(
        children: [
          const DrawerHeader(
            decoration: BoxDecoration(
              color: Colors.indigo,
            ),
            child: Column(
              children: [
                Text(
                  'Toko Anisa',
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    fontSize: 30,
                    fontWeight: FontWeight.bold,
                    color: Colors.white,
                  ),
                ),
                Padding(padding: EdgeInsets.all(10)),
                Text(
                  "Create and manage your items from here!",
                  // Menambahkan gaya teks dengan center alignment, font ukuran 15, warna putih, dan weight biasa
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    fontSize: 15,
                    color: Colors.white,
                    fontWeight: FontWeight.normal,
                  ),
                ),
              ],
            ),
          ),
          // Routing
          ListTile(
            leading: const Icon(Icons.home_outlined),
            title: const Text('Beranda'),
            // Bagian redirection ke MyHomePage
            onTap: () {
              Navigator.pushReplacement(
                  context,
                  MaterialPageRoute(
                    builder: (context) => MyHomePage(),
                  ));
            },
          ),
          ListTile(
            leading: const Icon(Icons.checklist),
            title: const Text('Lihat Item'),
            // Bagian redirection ke ShopFormPage
            onTap: () {
              Navigator.pushReplacement(
                  context,
                  MaterialPageRoute(
                    builder: (context) => const ItemsPage(),
                  ));
            },
          ),
          ListTile(
            leading: const Icon(Icons.add_shopping_cart),
            title: const Text('Tambah Item'),
            // Bagian redirection ke ShopFormPage
            onTap: () {
              /*
              Routing ke ShopFormPage di sini, setelah halaman ShopFormPage sudah dibuat.
              */
              Navigator.pushReplacement(
                  context,
                  MaterialPageRoute(
                      builder: (context) => const ItemFormPage()));
            },
          ),
        ],
      ),
    );
  }
}
```
Setelah itu, kita perlu memanggil *widget* `LeftDrawer` pada setiap *screen* yang akan kita buat selanjutnya. Kita akan memanggil *widget* `LeftDrawer` pada `menu.dart`, `shoplist_form.dart`, dan `show_item.dart`.