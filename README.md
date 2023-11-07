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
