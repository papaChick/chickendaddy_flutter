<h1>Tugas Individu</h1>
<details>
  <summary><h2>Tugas Individu 7</h2></summary>

## Jelaskan apa yang dimaksud dengan stateless widget dan stateful widget, dan jelaskan perbedaan dari keduanya.

- __Stateless widget__ adalah widget yang tidak berubah-ubah sehingga ideal untuk menunjukkan konten yang bersifat _static_. __Stateless widget__ tidak memiliki _state_. Contoh dari widget yang _stateless_ adalah teks dan icons.

- __Stateful widget__ adalah widget yang dapat berubah dan dapat menyimpan state. __Stateful widget__ bersifat dinamis dan dapat memperbarui penampilannya sebagai _response_ dari trigger-trigger tertentu, termasuk input pengguna. Contoh dari widget yang _stateful_ adalah checkbox, radio button, dan slider.

## Sebutkan widget apa saja yang kamu gunakan pada proyek ini dan jelaskan fungsinya.

1. __MaterialApp:__
Widget root yang menyediakan fungsi-fungsi dasar aplikasi Material Design

2. __Scaffold:__
Menyediakan struktur dasar halaman seperti AppBar, body, drawer, dll

3. __AppBar:__
Bar bagian atas aplikasi untuk menampilkan judul dan menu

4. __Text:__
Menampilkan teks dengan berbagai opsi styling

5. __Column:__
Menyusun widget-widget secara vertikal

6. __Row:__
Menyusun widget-widget secara horizontal

7. __Container:__
Widget serbaguna untuk dekorasi, padding, dan constraints

8. __Center:__
Menempatkan widget child di tengah

9. __Padding:__
Memberikan ruang kosong di sekitar widget

10. __SizedBox:__
Membuat kotak dengan ukuran tertentu, sering digunakan untuk spacing

11. __GridView:__
Menampilkan widget dalam layout grid

12. __Card:__
Menampilkan konten dalam bentuk kartu dengan elevasi

13. __Material:__
Widget dasar Material Design untuk efek visual

14. __InkWell:__
Area yang responsif terhadap sentuhan dengan efek ripple

15. __Icon:__
Menampilkan ikon dari set ikon Material Design

16. __SnackBar:__
Menampilkan pesan singkat di bagian bawah layar

## Apa fungsi dari setState()? Jelaskan variabel apa saja yang dapat terdampak dengan fungsi tersebut.
`setState()` mengabari framework bahwa _internal state_ dari objek tertentu berubah sedemikian rupa yang dapat berdampak pada _User Interface_, yang menyebabkan framework menjadwalkan sebuah _build_ untuk objek _state_ tersebut. Variavel-variable yang terdampak oleh `setState()` antara lain adalah variabel _instance_, _widget property_, dan _collections_.

## Jelaskan perbedaan antara const dengan final.
`const` digunakan untuk membuat variabel yang bersifat tidak dapat diganti dan hanya dapat diinisialisasi saat pembuatan variabel (sudah ditentukan sejak kompilasi). Sedangkan, `final` digunakan untuk membuat variabel yang bersifat tidak dapat diganti, namun dapat diinisialisasi sekali setelah pembuatan variabel (dapat ditentukan saat runtime).

## Jelaskan bagaimana cara kamu mengimplementasikan checklist-checklist di atas.

- __Buat project flutter__
  ```
  flutter create <APP_NAME>
  cd <APP_NAME>
  ```
  
- __Membuat file /lib/menu.dart__
- __Membuat MyHomePage, ItemHomePage, ItemCard, dan InfoCard__
  - ItemHomePage dibuat sedemikian rupa agar bisa construct warna
    ```dart
    class ItemHomepage {
      final String name;
      final IconData icon;
      final Color backgroundColor;
  
      ItemHomepage(this.name, this.icon, this.backgroundColor);
    }
    ```
  - juga untuk `ItemCard`
    ```dart
      class ItemCard extends StatelessWidget {
      // Menampilkan kartu dengan ikon dan nama.

      final ItemHomepage item;

      const ItemCard(this.item, {super.key});

      @override
      Widget build(BuildContext context) {
          return Material(
          // Menentukan warna latar belakang dari tema aplikasi.
          color: item.backgroundColor,
      ...
    ```
- __Membuat tombol__
  ``` dart
  class MyHomePage extends StatelessWidget {
  final String npm = '2306152323';
  final String name = 'Christian Raphael Heryanto';
  final String className = 'PBP D';
  final List<ItemHomepage> items = [
    ItemHomepage("Lihat Mood", Icons.mood, Colors.yellow),
    ItemHomepage("Tambah Mood", Icons.add, Colors.blue),
    ItemHomepage("Logout", Icons.logout, Colors.red),
  ];
  ...
  }
  ```

  Menggunakan ontap pada `ItemCard` untuk menunjukkan snackbar
   ```dart
   onTap: () {
          // Menampilkan pesan SnackBar saat kartu ditekan.
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(SnackBar(
                content: Text("Kamu telah menekan tombol ${item.name}!")));
        },
    ```

- __Menghubungkan MyHomepage kedalam `main.dart`__
  ```dart
  import 'package:chickendaddy_flutter/menu.dart';
  ```

</details>

<details open>
  <summary><h2>Tugas Individu 8</h2></summary>

## Apa kegunaan `const` di Flutter? Jelaskan apa keuntungan ketika menggunakan `const` pada kode Flutter. Kapan sebaiknya kita menggunakan `const`, dan kapan sebaiknya tidak digunakan?
`const` pada Flutter digunakan untuk membuat sebuah _object_ atau nilai dalam Flutter menjadi sebuah _constant_ (tidak dapat diubah). Keuntungan dari menggunakan `const` adalah sebagai berikut:
- Optimisasi dengan membuat _pre-allocated memory_
- Menambah _readability_ dan _maintainability_
`const` sebaiknya digunakan untuk widget yang bersifat _static_ (tidak berubah selama runtime). Sedangkan, `const` sebaiknya tidak digunakan untuk widget yang bersifat _dinamis_ (berubah-ubah selama runtime).

## Jelaskan dan bandingkan penggunaan Column dan Row pada Flutter. Berikan contoh implementasi dari masing-masing layout widget ini!
Column: digunakan untuk menyusun elemen atau widget secara vertikal
Row: digunakan untuk menyusun elemen atau widget secara horizontal

Contoh Implementasinya adalah sebagai berikut:
- Column
  ```dart
  Column(
    children: [
      Text('Item 1'),
      Text('Item 2'),
      ElevatedButton(onPressed: () {}, child: Text('Button'))
    ],
  )
  ```
- Row
  ```dart
  Row(
    mainAxisAlignment: MainAxisAlignment.spaceEvenly,
    children: [
      Icon(Icons.star),
      Icon(Icons.favorite),
      Icon(Icons.settings),
    ],
  )
  ```

## Sebutkan apa saja elemen input yang kamu gunakan pada halaman form yang kamu buat pada tugas kali ini. Apakah terdapat elemen input Flutter lain yang tidak kamu gunakan pada tugas ini? Jelaskan!

Terdapat banyak sekali widget input untuk forms pada Flutter. Pada tugas ini, saya hanya menggunakan `TextFormField()`. Tentu masih banyak elemen input Flutter yang tidak saya gunakan sebab Flutter memiliki banyak sekali widget input (dapat dilihat pada documentation Flutter official). Penggunaan `TextFormField()` digunakan untuk menerima input dalam bentuk text. Pada tugas ini, kita cukup menerima input berupa Text yang kemudian salah satunya dapat di casting sebagi interger. 


## Bagaimana cara kamu mengatur tema (theme) dalam aplikasi Flutter agar aplikasi yang dibuat konsisten? Apakah kamu mengimplementasikan tema pada aplikasi yang kamu buat?
Tema dapat diatur melalui berkas `lib/main.dart`. Iya, saya mengimplementasikannya pada aplikasi ini.
```dart
theme: ThemeData(
      // This is the theme of your application.
      //
      // TRY THIS: Try running your application with "flutter run". You'll see
      // the application has a purple toolbar. Then, without quitting the app,
      // try changing the seedColor in the colorScheme below to Colors.green
      // and then invoke "hot reload" (save your changes or press the "hot
      // reload" button in a Flutter-supported IDE, or press "r" if you used
      // the command line to start the app).
      //
      // Notice that the counter didn't reset back to zero; the application
      // state is not lost during the reload. To reset the state, use hot
      // restart instead.
      //
      // This works for code too, not just values: Most code changes can be
      // tested with just a hot reload.
      colorScheme: ColorScheme.fromSwatch(
        primarySwatch: Colors.deepPurple,
      ).copyWith(secondary: Colors.deepPurple[400]),
      useMaterial3: true,
    ),
    home: MyHomePage(),
```

## Bagaimana cara kamu menangani navigasi dalam aplikasi dengan banyak halaman pada Flutter?
Untuk navigasi dalam flutter dapat menggunakan `Navigator` dan metode `push` & `pop`.
Implementasi dapat dilakukan sebagai berikut
```dart
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => SecondPage()),
);
```
```dart
ElevatedButton(
  onPressed: () {
    Navigator.pop(context);
  },
  child: Text('Kembali'),
)
```

</details>