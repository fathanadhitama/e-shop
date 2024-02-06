# Modul 1 : Coding Standards

> #### Fathan Naufal Adhitama (2206825965)

### Reflection 1

Setelah mempelajari lebih lanjut tentang ***coding standards*** 
dalam kelas sebelumnya, saya mencoba 
mengimplementasikannya dalam proyek ini. Di antaranya adalah:
- Saya selalu memberi nama variabel dan 
fungsi sejelas mungkin untuk membuat kode saya
lebih mudah dibaca dan lebih mudah dikelola. 
- Menggunakan function dengan efektif, yaitu dengan menulis
function dengan singkat dan tiap function hanya berfungsi untuk
melakukan satu hal sesuai dengan prinsip ***"Do One Thing"***
- Hanya menuliskan comments pada kebutuhan yang tepat dengan
menuliskan kode yang jelas sehingga tidak perlu ditambah comments
untuk menjelaskan kode tersebut.

Namun, setelah meninjau ulang kode yang saya tulis 
sekali lagi, saya menemukan bahwa saya belum 
menerapkan konsep ***secure coding*** yang cukup 
untuk melindungi program dari kejadian yang tidak 
diinginkan. Saya hanya memvalidasi data input 
untuk mencegah *runtime error* dalam program. Menurut
saya hanya menerapkan hal tersebut saja belum cukup 
aman karena berbagai serangan masih dapat mengancam 
program ini. Kesalahan-kesalahan tersebut dapat 
diperbaiki dengan menerapkan validasi data input
yang lebih spesifik dan menambahkan fitur keamanan
seperti ***Authentication & Authorization*** agar hal-hal seperti karakter
berbahaya dan upaya serangan injeksi dapat ditangani
dengan baik.

### Reflection 2
1. Jumlah unit test yang sebaiknya dibuat dalam
satu class dapat bervariasi tergantung 
kompleksitas class tersebut. Idealnya, setiap
fungsi atau metode dalam class sebaiknya 
memiliki setidaknya satu unit test yang
mencakup berbagai skenario. 
Untuk memastikan bahwa unit test sudah cukup
untuk memverifikasi program, penting untuk 
memperhatikan *coverage* dari unit test tersebut.
***Code coverage*** mengukur seberapa banyak bagian
dari source code yang telah diuji. Akan tetapi,
100% Code coverage juga tidak menjamin bahwa tidak ada 
*bug* atau *error* dalam kode. Code coverage
hanya mengukur sejauh mana kode telah 
dijalankan oleh unit test, bukan kualitas atau
validitas logika bisnisnya. 
Jadi, *code coverage* adalah hal yang penting,
tetapi sama halnya dengan pentingnya merancang
unit test yang cermat dan menyeluruh, mencakup berbagai 
kondisi yang mungkin terjadi dalam aplikasi.

2. Ketika kita membuat ***functional test suite*** lain yang
menggunakan *setup procedures* dan *instance variables* yang
sama dengan functional test suite sebelumnya, mungkin saja dapat
menimbulkan masalah pada **code cleanliness**. Salah satu contohnya
adalah menuliskan kode yang sama sehingga terdapat kode yang bersifat
*redundant* dan tidak efektif. Salah satu cara untuk meng-*improve*
masalah tersebut adalah dengan membuat *base class* yang berisi
*setup procedures* dan *instance variables* yang sama sehingga dapat
digunakan di beberapa test suite tanpa menyebabkan *code duplication*
