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

<details>
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
<details open>
<summary><h2>Tugas Individu 9</h2></summary>

## Jelaskan mengapa kita perlu membuat model untuk melakukan pengambilan ataupun pengiriman data JSON? Apakah akan terjadi error jika kita tidak membuat model terlebih dahulu?
Menggunakan model untuk melakukan pengambilan ataupun pengiriman data JSON memastikan bahwa tidak terdapat error atau null fields. Setiap field diparsing sesuai dengan models masing-masing. Selain itu, models juga meningkatkan _readability_ kode agar mudah untuk dikmbangkan kedepannya.

## Jelaskan fungsi dari library http yang sudah kamu implementasikan pada tugas ini
http library adalah library Flutter yang digunakan untuk membuat HTTP requests pada flutter. Pada tugas ini, library penting sebab kita ingin mengintegrasikan django dan flutter sehingga harus berkomunikasi melalui HTTP requests.

## Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.
CookieRequest berfungsi untuk menyimpan cookie yang diterima dari server setelah proses otentikasi. Cookie kemudian dikirimkan kembali ke server pada requests selanjutnya agar server dapat mengidentifikasi pengguna. Maka dari itu, CookieRequest perlu unutk dibagikan ke semua komponen di aplikasi Flutter.

## Jelaskan mekanisme pengiriman data mulai dari input hingga dapat ditampilkan pada Flutter.
  1. Input Data
  Pengguna memberikan data melalui widget (misalnya, TextField, DropdownButton, dll.).

  2. Validasi Data
  Data yang diinput diverifikasi untuk memastikan format dan data sesuai.

  3. Pengiriman ke Backend
  Data dikirim ke server melalui HTTP requests.

  4. Proses di Backend
  Backend menerima, memproses, dan memberikan response.

  5. Penerimaan Response
  Flutter menerima respons dari server dan mengolahnya.

  6. Penyajian di UI
  Data dari response ditampilkan kepada pengguna melalui komponen UI dengan memperbarui state aplikasi.

## Jelaskan mekanisme autentikasi dari login, register, hingga logout. Mulai dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.
Proses login dimulai dengan memasukkan input kepada forms. Input yang dimasukkan diantara lain adalah email dan password. Setelah diinput, request dan dikirim kepada endpoint django yang bersangkutan. Kemudian, jika berhasil, cookie akan disimpan dalam CookieRequest untuk request-request kedepannya. Setelah login berhasil, menu utama flutter akan ditampilkan.
Proses register dimulai dengan memasukkan input kepada forms. Kemudian, data dari input dilanjutkan kk Django. Jika data valid, data tersebut akan disimpan dalam database backend untuk diakses berikutnya. Selain itu, django aja mengembalikan erspons sukses. Setelah register berhasil, pengguna akan diarahkan untuk login.
Proses logout dimulai dengan mengirimkan requets kepada Django. Kemudian, session dari cookie yang digunakan untuk login didelete. Flutter kemudian mengubah status sebagai logged out dan redirect pengguna kepada menu login. 

## Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial).

### Mengimplementasikan fitur registrasi akun pada proyek tugas Flutter.

Membuat register page dengan tampilan yang menarik. Namun, perlu diingat bahwa register page harus mengirimkan post request kepada endpoint views register pada urls.py django.
```dart
final response = await request.postJson(
  "http://127.0.0.1:8000/auth/register/",
  jsonEncode({
    "username": username,
    "password1": password1,
    "password2": password2,
  }));
 (context.mounted) {
if (response['status'] == 'success') {
  ScaffoldMessenger.of(context).showSnackBar(
    const SnackBar(
      content: Text('Successfully registered!'),
    ),
  );
  Navigator.pushReplacement(
    context,
    MaterialPageRoute(
        builder: (context) => const LoginPage()),
  );
} else {
  ScaffoldMessenger.of(context).showSnackBar(
    const SnackBar(
      content: Text('Failed to register!'),
    ),
  );
}
```

### Membuat halaman login pada proyek tugas Flutter.
Membuat login page semenarik mungkin. Namun ada beberapa key takeaways:
- menerima input
- mengirimkan request post kepada backend endpoint django untuk login

```dart
import 'package:chickendaddy_flutter/screens/menu.dart';
import 'package:chickendaddy_flutter/screens/register.dart';
import 'package:flutter/material.dart';
import 'package:pbp_django_auth/pbp_django_auth.dart';
import 'package:provider/provider.dart';

void main() {
  runApp(const LoginApp());
}

class LoginApp extends StatelessWidget {
  const LoginApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Login',
      theme: ThemeData(
        useMaterial3: true,
        colorScheme: ColorScheme.fromSwatch(
          primarySwatch: Colors.deepPurple,
        ).copyWith(secondary: Colors.deepPurple[400]),
      ),
      home: const LoginPage(),
    );
  }
}

class LoginPage extends StatefulWidget {
  const LoginPage({super.key});

  @override
  State<LoginPage> createState() => _LoginPageState();
}

class _LoginPageState extends State<LoginPage> {
  final TextEditingController _usernameController = TextEditingController();
  final TextEditingController _passwordController = TextEditingController();

  @override
  Widget build(BuildContext context) {
    final request = context.watch<CookieRequest>();

    return Scaffold(
      appBar: AppBar(
        title: const Text('Login'),
      ),
      body: Center(
        child: SingleChildScrollView(
          padding: const EdgeInsets.all(16.0),
          child: Card(
            elevation: 8,
            shape: RoundedRectangleBorder(
              borderRadius: BorderRadius.circular(12.0),
            ),
            child: Padding(
              padding: const EdgeInsets.all(20.0),
              child: Column(
                mainAxisSize: MainAxisSize.min,
                children: [
                  const Text(
                    'Login',
                    style: TextStyle(
                      fontSize: 24.0,
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                  const SizedBox(height: 30.0),
                  TextField(
                    controller: _usernameController,
                    decoration: const InputDecoration(
                      labelText: 'Username',
                      hintText: 'Enter your username',
                      border: OutlineInputBorder(
                        borderRadius: BorderRadius.all(Radius.circular(12.0)),
                      ),
                      contentPadding:
                          EdgeInsets.symmetric(horizontal: 12.0, vertical: 8.0),
                    ),
                  ),
                  const SizedBox(height: 12.0),
                  TextField(
                    controller: _passwordController,
                    decoration: const InputDecoration(
                      labelText: 'Password',
                      hintText: 'Enter your password',
                      border: OutlineInputBorder(
                        borderRadius: BorderRadius.all(Radius.circular(12.0)),
                      ),
                      contentPadding:
                          EdgeInsets.symmetric(horizontal: 12.0, vertical: 8.0),
                    ),
                    obscureText: true,
                  ),
                  const SizedBox(height: 24.0),
                  ElevatedButton(
                    onPressed: () async {
                      String username = _usernameController.text;
                      String password = _passwordController.text;

                      // Cek kredensial
                      // TODO: Ganti URL dan jangan lupa tambahkan trailing slash (/) di akhir URL!
                      // Untuk menyambungkan Android emulator dengan Django pada localhost,
                      // gunakan URL http://10.0.2.2/
                      final response = await request
                          .login("http://127.0.0.1:8000/auth/login/", {
                        'username': username,
                        'password': password,
                      });

                      if (request.loggedIn) {
                        String message = response['message'];
                        String uname = response['username'];
                        if (context.mounted) {
                          Navigator.pushReplacement(
                            context,
                            MaterialPageRoute(
                                builder: (context) => MyHomePage()),
                          );
                          ScaffoldMessenger.of(context)
                            ..hideCurrentSnackBar()
                            ..showSnackBar(
                              SnackBar(
                                  content:
                                      Text("$message Selamat datang, $uname.")),
                            );
                        }
                      } else {
                        if (context.mounted) {
                          showDialog(
                            context: context,
                            builder: (context) => AlertDialog(
                              title: const Text('Login Gagal'),
                              content: Text(response['message']),
                              actions: [
                                TextButton(
                                  child: const Text('OK'),
                                  onPressed: () {
                                    Navigator.pop(context);
                                  },
                                ),
                              ],
                            ),
                          );
                        }
                      }
                    },
                    style: ElevatedButton.styleFrom(
                      foregroundColor: Colors.white,
                      minimumSize: Size(double.infinity, 50),
                      backgroundColor: Theme.of(context).colorScheme.primary,
                      padding: const EdgeInsets.symmetric(vertical: 16.0),
                    ),
                    child: const Text('Login'),
                  ),
                  const SizedBox(height: 36.0),
                  GestureDetector(
                    onTap: () {
                      Navigator.push(
                        context,
                        MaterialPageRoute(
                            builder: (context) => const RegisterPage()),
                      );
                    },
                    child: Text(
                      'Don\'t have an account? Register',
                      style: TextStyle(
                        color: Theme.of(context).colorScheme.primary,
                        fontSize: 16.0,
                      ),
                    ),
                  ),
                ],
              ),
            ),
          ),
        ),
      ),
    );
  }
}
```

### Mengintegrasikan sistem autentikasi Django dengan proyek tugas Flutter.
- membuat masing-masing views untuk login, logout, register
- memberi masing-masing views endpoint pada urls.py
- memberi perubahan kode flutter yang bersangkutan untuk mengolah data dari backend menggunakan requests.

### Membuat model kustom sesuai dengan proyek aplikasi Django.
- Membuka endpoint 127.0.0.1:8000/json
- Generate dart file menggunaka Quicktype
- membuat file product_entry.dart dalam direktori lib/models.

### Membuat halaman yang berisi daftar semua item yang terdapat pada endpoint JSON di Django yang telah kamu deploy.  

Melakukan request kepada endpoint django, lalu iterate dari json tersebut untuk menampilkan data.
```dart
import 'package:flutter/material.dart';
import 'package:chickendaddy_flutter/models/product_entry.dart';
import 'package:chickendaddy_flutter/widgets/left_drawer.dart';
import 'package:pbp_django_auth/pbp_django_auth.dart';
import 'package:provider/provider.dart';
import 'package:chickendaddy_flutter/screens/product_detail_page.dart';

class ProductEntryPage extends StatefulWidget {
  const ProductEntryPage({super.key});

  @override
  State<ProductEntryPage> createState() => _ProductEntryPageState();
}

class _ProductEntryPageState extends State<ProductEntryPage> {
  Future<List<ProductEntry>> fetchProduct(CookieRequest request) async {
    final response = await request.get('http://127.0.0.1:8000/json/');
    var data = response;

    List<ProductEntry> listProduct = [];
    for (var d in data) {
      if (d != null) {
        listProduct.add(ProductEntry.fromJson(d));
      }
    }
    return listProduct;
  }

  @override
  Widget build(BuildContext context) {
    final request = context.watch<CookieRequest>();
    return Scaffold(
      appBar: AppBar(
        title: const Text('Product Entry List'),
      ),
      drawer: const LeftDrawer(),
      body: FutureBuilder(
        future: fetchProduct(request),
        builder: (context, AsyncSnapshot snapshot) {
          if (snapshot.data == null) {
            return const Center(child: CircularProgressIndicator());
          } else {
            if (!snapshot.hasData) {
              return const Column(
                children: [
                  Text(
                    'Belum ada data products pada chicken daddy.',
                    style: TextStyle(fontSize: 20, color: Color(0xff59A5D8)),
                  ),
                  SizedBox(height: 8),
                ],
              );
            } else {
              return ListView.builder(
                itemCount: snapshot.data!.length,
                itemBuilder: (_, index) => Container(
                  margin:
                      const EdgeInsets.symmetric(horizontal: 16, vertical: 12),
                  padding: const EdgeInsets.all(20.0),
                  child: Column(
                    mainAxisAlignment: MainAxisAlignment.start,
                    crossAxisAlignment: CrossAxisAlignment.start,
                    children: [
                      Text(
                        "${snapshot.data![index].fields.name}",
                        style: const TextStyle(
                          fontSize: 18.0,
                          fontWeight: FontWeight.bold,
                        ),
                      ),
                      const SizedBox(height: 10),
                      Text("${snapshot.data![index].fields.price}"),
                      const SizedBox(height: 10),
                      Text("${snapshot.data![index].fields.description}"),
                      const SizedBox(height: 10),
                      ElevatedButton(
                        onPressed: () {
                          Navigator.push(
                            context,
                            MaterialPageRoute(
                              builder: (context) => ProductDetailPage(
                                product: snapshot.data![index],
                              ),
                            ),
                          );
                        },
                        child: const Text('View Details'),
                      ),
                    ],
                  ),
                ),
              );
            }
          }
        },
      ),
    );
  }
}
```


### Membuat halaman detail untuk setiap item yang terdapat pada halaman daftar Item.

```dart
ElevatedButton(
  onPressed: () {
    Navigator.push(
      context,
      MaterialPageRoute(
        builder: (context) => ProductDetailPage(
          product: snapshot.data![index],
        ),
      ),
    );
  },
  child: const Text('View Details'),
)
```

### Melakukan filter pada halaman daftar item dengan hanya menampilkan item yang terasosiasi dengan pengguna yang login.
</details>