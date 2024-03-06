# Tutorial Pemrograman Lanjut

> #### Fathan Naufal Adhitama (2206825965)
**Contents:**
1. **[Tutorial 1](#tutorial-1)**
2. **[Tutorial 2](#tutorial-2)**
3. **[Tutorial 3](#tutorial-3)**
4. **[Tutorial 4](#tutorial-4)**


## Tutorial 1
***
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

***

## Tutorial 2
***
### Reflection

1. **List the code quality issue(s) that you fixed during 
the exercise and explain your strategy on fixing them.**

    Setelah dilakukan *code scanning* oleh PMD, terdeteksi beberapa
   _code quality issues_ yang terdapat pada kode yang saya tulis. Di antaranya
    adalah sebagai berikut: <br><br>
   - **_Unused Import_** : 
   <br>Adanya _imports_ yang tidak perlu karena tidak digunakan.
   **Strategi** untuk masalah tersebut adalah dengan menghapus semua _imports_ yang tidak digunakan.
   <br><br>
   - **_Unnecessary Modifiers_**:
     <br>Penggunaan modifier **public** yang sebenarnya tidak perlu
      karena secara default, method-method dalam interface sudah memiliki modifier
   `public abstract` tanpa perlu ditulis kembali. **Strategi** untuk masalah tersebut adalah dengan menghapus 
   semua modifier public yang tidak perlu.<br><br>

2. Look at your CI/CD workflows (GitHub)/pipelines (GitLab). 
Do you think the current implementation has met the definition
of Continuous Integration and Continuous Deployment? 
Explain the reasons (minimum 3 sentences)!
Implementasi yang saat ini saya terapkan pada kode saya telah sesuai 
dengan prinsip **CI/CD**. **_Continuous Integration_** diaplikasikan
dengan _workflows_ yang dijalankan setiap adanya push, pull dan merge di
setiap branch karena adanya file-file seperti `ci.yml`, `scorecard.yml`, dan `pmd_action.yml`.
Sedangkan **_Continuous Deployment_** diaplikasikan dengan penggunaan Koyeb sebagai _platform_
untuk deployment aplikasi ini. Koyeb akan secara otomatis melakukan re-deploy setiap
adanya perubahan pada branch `master`.
***

## Tutorial 3
***
### Reflection
1. Explain what principles you apply to your project!
   - **Single Responsibility Principle (SRP)**: Saya memisahkan fungsi-fungsi 
   yang memiliki tugas berbeda atau lebih detil ke _class_ sendiri 
   sehingga setiap kelas hanya fokus pada 1 tugas saja. Contoh:
     - `CarController` terpisah dengan `ProductController`
     - `ProductFinder` terpisah dengan `ProductRepository`
   - **Interface Segregation Principle (ISP)**: Setiap _class_ mengimplementasikan
   Interface-interface yang relevan dengan fungsi kelas tersebut. Contoh:
     - `CarRepository` mengimplementasikan `CarRepoInterface`
     - `ProductRepository` mengimplementasikan `ProductRepoInterface`
     - `ProductServiceImpl` mengimplementasikan `ProductService`
     - `CarServiceImpl` mengimplementasikan `CarService`
   - **Dependency Inversions Principle (DIP)**: _Class_ harus bergantung pada 
   _Interface/Abstract Class_, bukan _Concrete Class_. Contoh:
     - `carService` pada `CarController` seharusnya menggunakan Interface `CarService`,
     bukan `CarServiceImpl`
   - **Open-Closed Principle (OCP)** : Sebuah _class_ harus bersifat _open_ terhadap extension,
   tetapi _closed_ terhadap _modification_. Contoh:
     - Tidak secara langsung melakukan modifikasi terhadap objek Car 
     pada method `update` di class `CarRepository`.
   - **Liskov Substitution Principle (LSP)** : Suatu subclass seharusnya dapat menggantikan
   superclass-nya tanpa memengaruhi efektivitas program. Contoh:
     - class `CarController` seharusnya tidak menjadi subclass dari `ProductController`
     karena keduanya memiliki fungsi dan sifat yang berbeda.

2. Explain the advantages of applying SOLID principles to your project with examples.
   - Dengan menerapkan prinsip-prinsip SOLID, kode akan menjadi lebih teratur, mudah dimodifikasi, 
   dan dapat di-_maintain_ dengan baik. Dengan begitu, _developer_ dapat mengurangi risiko rapuhnya
   perangkat lunak, mempermudah untuk melakukan perubahan yang dibutuhkan di masa depan.
   - Contoh:
     - Dengan memisahkan kelas `ProductFinder` dari `ProductRepository`, developer akan lebih
     mudah untuk mengubah kode yang spesifik terhadap fitur _finder_. Sehingga, ketika melakukan debugging
     ataupun menambah fungsionalitas lain, developer dapat lebih fokus pada 1 kelas saja.
     - Dengan menggunakan Interface `CarService` daripada Concrete Class `CarServiceImpl`,
     developer tidak perlu lagi mengubah controller jika membuat implementasi baru

3. Explain the disadvantages of not applying SOLID principles to your project with examples.
   - Berkebalikan dengan penjelasan pada nomor 2, apabila kita tidak menggunakan prinsip SOLID
   pada kode kita, kode akan menjadi lebih sulit untuk di-_maintain_ ke depannya karena rendahnya
   _readability_ dari kode tersebut. Akibatnya, kode akan menjadi lebih rentan pada perubahan
   dan akan sulit untuk melakukan _testing_.
   - Contoh: 
     - Apabila tidak menerapkan SRP pada kelas `ProductRepository`, ke depannya akan sulit dilakukan
     perubahan terhadap fungsi tertentu, terutama apabila method yang diterapkan sudah semakin banyak dan kompleks.
     Tentu akan lebih mudah apabila kelas-kelas dipisahkan sesuai fungsinya.
     - Apabila tidak menerapkan DIP, ketergantungan antarkelas akan testing lebih sulit
     dan sulit melakukan perubahan karena akan banyak bagian yang perlu diperhatikan untuk diganti.

***

## Tutorial 4
***
### Reflection
1. Menurut Percival (2017) berikut adalah pertanyaan-pertanyaan reflektif yang dapat kita gunakan
untuk mengevaluasi tiga objektif utama pada _tests_ kita:
   1. Correctness
      - Do I have enough functional tests to reassure myself that my application
        really works, from the point of view of the user? 
      <br>>> Menurut saya, functional test yang telah dibuat pada program ini sudah cukup untuk
      memastikan bahwa _code_ yang dibuat dapat berfungsi dengan baik sesuai ekspektasi awal.
      - Am I testing all the edge cases thoroughly?
      <br>>> Tests yang telah dibuat sudah mencakup kasus-kasus yang disebutkan dalam soal. Namun,
      masih terdapat kemungkinan _edge cases_ lain yang belum di-_cover_.
      - Do I have tests that check whether all my components fit together
        properly?
        <br>>> Untuk memastikan apakah semua program dapat berjalan dengan baik secara keseluruhan,
        dapat dilihat melalui _functional tests_ yang telah dibuat. Namun, untuk melakukan hal tersebut
        dengan lebih pasti, dapat dibuat juga _Integration Test_
   2. Maintainability
      - Are my tests giving me the confidence to refactor my code, fearlessly
        and frequently?
        <br>>> Iya, dengan memiliki tests yang dapat mengecek benar atau tidaknya kode saya, saya merasa lebih nyaman untuk melakukan perubahan dan perbaikan pada kode tanpa harus takut untuk merusak program yang sebelumnya berjalan dengan baik
      - Are my tests helping me to drive out a good design? If I have a lot of
        integration tests but less unit tests, do I need to make more unit tests to
        get better feedback on my code design?
        <br>>> Menurut saya, test-test yang ada dapat membantu saya untuk memikirkan desain yang lebih baik dalam program saya dengan memikirkan
        kemungkinan-kemungkinan yang terjadi pada program saya dari perspektif _user_. Integration test dan unit test memiliki tujuan yang berbeda, sehingga
        menjaga keseimbangan antara keduanya akan lebih baik agar tujuan dari masing-masing test dapat terpenuhi.
   3. Productive _workflow_
        - Are my feedback cycles as fast as I would like them? When do I get
          warned about bugs, and is there any practical way to make that happen
          sooner?
          <br>>> Dengan tests yang ada, saya bisa mendapatkan _feedback_ sesegera mungkin setelah saya melakukan perubahan pada kode.
            Apabila terdapat bug, saya akan mendapat _warning_ dan dapat melihat dimana kode yang harus diperbaiki.
            Salah satu cara yang dapat dilakukan untuk mendapat feedback dengan lebih cepat adalah dengan membuat lebih banyak functional tests
        - Is there some way that I could write faster integration tests that would
          get me feedback quicker?
          <br>>> Untuk menulis integration tests yang dapat memberi feedback dengan lebih cepat, kita dapat mengoptimalkan 
            setup dan teardown dari testing, lebih fokus untuk menguji skenario yang kritis dan gunakan stubbing tools untuk menggantikan
            komponen eksternal yang dapat memperlambat testing.
        - Can I run a subset of the full test suite when I need to?
          <br>>> Ya, kita dapat memberi tanda pada tes-tes tertentu menjadi "penting" dan mengatur test suite untuk hanya menjalankan tes tersebut.
        - Am I spending too much time waiting for tests to run, and thus less time
          in a productive flow state?
          <br>>> Tidak, karena saat ini tests yang ada tidak membutuhkan waktu lama untuk memberikan feedback
            sehingga tidak akan menghambat produktivitas.
2. You have created unit tests in Tutorial. Now reflect whether your tests have successfully followed F.I.R.S.T. principle or not. If not, explain things that you need to do the next time you create more tests.
   - Fast
     - Testing yang telah dibuat tidak membutuhkan waktu lama untuk memberikan feedback
       sehingga tidak akan menghambat produktivitas.
   - Isolated/Independent
     - Setiap test case tidak akan memengaruhi hasil dari test case lain
   - Repeatable
     - Hasil tests akan selalu konsisten ketika tests dijalankan berulang kali.
   - Self-validating
     - Semua tests sudah menerapkan prinsip self-validating dengan menggunakan assertion yang benar dan strict terhadap hasil pass maupun fail.
   - Thorough/Timely
     - Tests yang ada telah mencakup keseluruhan skenario happy dan unhappy paths sesuai yang dijelaskan pada modul.