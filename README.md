# davinstore

## Tautan Aplikasi
https://davinstore.adaptable.app/main/

## Tugas 02
1. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).

 - [x] Membuat sebuah proyek Django baru.

- Membuat direktori lokal dan repo baru di Github -> Menginisiasi git dengan `git init` -> meng-connect repo lokal dan repo gthub.s
- Mengaktfkan `Virtual Environment` dengan `env\Scripts\activate.bat` -> memulai project `django-admin startproject davinstore` .` 
- Menambahkan `.gitignore`dan `requirements.txt` -> melakukan `add`, `commit`, dan `push` untuk push semua changes ke github

 - [x]  Membuat aplikasi dengan nama `main` pada proyek tersebut.

- Membuat aplikasi main dengan `python manage.py startapp main` di `INSTALLED APPS` pada `settings.py`


 - [x] Melakukan routing pada proyek agar dapat menjalankan aplikasi main.

- Mendefinisikan URL aplikasi main di main.urls -> Mendaftarkan URL aplikasi main yang telah dibuat pada URL project. Keduanya dilakukan dengan menambahkan path di urlpatterns. URL menjadi gerbang request dari internet dan penghubung menuju aplikasi yang di request


 - [x] Membuat model pada aplikasi `main` dengan nama `Item` dan memiliki atribut wajib sebagai berikut.
    + `name` sebagai nama *item* dengan tipe `CharField`.
    + `amount` sebagai jumlah *item* dengan tipe `IntegerField`.
    + `description` sebagai deskripsi *item* dengan tipe `TextField`.

- Membuat class yang berisi atribut sesuai dengan ketentuan soal. Hal ini berguna untuk mendefinisikan struktur database. Berikut code nya
```
from django.db import models

class Item(models.Model):
    name = models.CharField(max_length=255)
    amount = models.IntegerField()
    description = models.TextField()
```

- Mengmigrasikan class yang telah dibuat ke database dengan `python manage.py makemigrations` dan `python manage.py migrate`. Nantinya pada admin, database otomatis terbuat dengan atribut-atribut yang telah dibuat dalam class Item.

 - [x] Membuat sebuah fungsi pada `views.py` untuk dikembalikan ke dalam sebuah *template* HTML yang menampilkan nama aplikasi serta nama dan kelas kamu.

- Membuat function show main dengan parameter request -> Menambahkan context sebagai data yang akan di tampilkan pada HTML -> Menambahkan return render dengan parameter request dan file html. Render ini bertujuan untuk mengrender response html pada browser.

- Membuat file html yang berisi:

```
<h1>{{app_name}}</h1>

<h5>Nama: </h5>
<p>{{name}}</p> 
<h5>Kelas: </h5>
<p>{{class}} </p>
```


 - [x] Membuat sebuah routing pada urls.py aplikasi main untuk memetakan fungsi yang telah dibuat pada views.py.

- Sudah dijelaskan di checklist sebelumnya. Mendaftarkan url yang sudah didefine pada main.urls ke dalam urlpatterns agar nantinya jika client request path aplikasi maka urls project akan mengarahkan menuju urls aplikasi

 - [x] Melakukan deployment ke Adaptable terhadap aplikasi yang sudah dibuat sehingga nantinya dapat diakses oleh teman-temanmu melalui Internet.

- Melakukan push semua progres project ke dalam repo github -> melakukan login adaptable.io dengan github -> memilih repo ini.
- Mengatur segala ketentuan sebagai berikut: Template Deployment yang dipakai adalah `Python App Template` dan database `PostgreSQL`. `Start Command` -> menjalankan perintah `python manage.py migrate && gunicorn davinstore.wsgi`.

Terakhir, aplikasi yang saya buat memiliki *domain* bernama `https://davinstore.adaptable.app/main`.


2. Buatlah bagan yang berisi request client ke web aplikasi berbasis Django beserta responnya dan jelaskan pada bagan tersebut kaitan antara urls.py, views.py, models.py, dan berkas html.

![bagan](https://github-production-user-asset-6210df.s3.amazonaws.com/124948495/267528405-df8edcfa-abc2-4f17-8b7c-599fb4f16620.png)

- Client request HTTP melalui browser dan dilanjutkan ke file `urls.py`.Selanjutnya, path akan mengarahkan ke path yang telah terdaftar di urls.py aplikasi. Kemudian,mengakses file `views.py` sesuai dengan parameter function yang tercantum pada path. Setelah itu `views.py` akan mengambil data dari `models.py` dan memberikan data tersebut kepada code `main.htmml` dan merendernya. Kemudian `main.html` akan merender hasil ke browser.

3. Jelaskan mengapa kita menggunakan virtual environment? Apakah kita tetap dapat membuat aplikasi web berbasis Django tanpa menggunakan virtual environment?

- Virtual environment digunakan untuk membuat lingkungan terisolasi agar dapat mengelola dependensi dan modul Python yang dibutuhkan untuk setiap proyek secara terpisah. Dengan cara ini, kita dapat mencegah konflik dan interaksi antara modul atau konfigurasi proyek yang berbeda. Pendekatan ini memungkinkan untuk menghindari instalasi paket atau modul secara global, terutama jika paket atau modul tersebut hanya diperlukan oleh satu proyek khusus.

- Virtual environment dibentuk dengan  `python -m venv env` dan diaktifkan dengan  `env\Scripts\activate.bat`.

4. Jelaskan apakah itu MVC, MVT, MVVM dan perbedaan dari ketiganya.

- MVC (Model-View-Controller), MVT (Model-View-Template), dan MVVM (Model-View-ViewModel) adalah pola arsitektur perangkat lunak yang digunakan dalam pengembangan aplikasi. Mereka semua memiliki prinsip dasar yang serupa, yaitu membagi komponen aplikasi menjadi bagian yang berbeda untuk memudahkan pemahaman, perawatan, dan pengujian. Namun, ada perbedaan penting dalam cara masing-masing pola ini diimplementasikan.

- MVC (Model-View-Controller):

    -  Model: Menyimpan data dan logika aplikasi.
    - View: Bertanggung jawab atas antarmuka pengguna atau tampilan grafis.
    - Controller: Mengelola interaksi antara Model dan View serta mengontrol alur aplikasi.
Perbedaan utama:

- MVC adalah pola arsitektur yang sering digunakan dalam pengembangan perangkat lunak tradisional, seperti aplikasi desktop.
Controller berperan sebagai inti dari MVC, menghubungkan Model dan View serta mengendalikan alur aplikasi.
MVT (Model-View-Template):

    - Model: Menyimpan data dan logika aplikasi.
    - View: Menangani tampilan pengguna, tetapi dalam konteks kerangka kerja Django, sebagian besar logika tampilan dikendalikan oleh Template.
    - Template: Bertanggung jawab untuk merender tampilan dan menggabungkan data dari Model.
Perbedaan utama:

- MVT adalah variasi dari MVC yang diterapkan secara khusus dalam kerangka kerja Django untuk pengembangan web.
Template memiliki peran yang lebih besar dalam menangani tampilan dibandingkan dengan View.

- MVVM (Model-View-ViewModel):

    - Model: Berisi data dan logika aplikasi.
    - View: Merupakan tampilan grafis yang dilihat oleh pengguna.
    - ViewModel: Bertugas mengelola data yang akan ditampilkan di View dan bertindak sebagai penghubung antara Model dan View.
Perbedaan utama:

- MVVM adalah pola arsitektur yang sering digunakan dalam pengembangan aplikasi berbasis objek, seperti aplikasi desktop dan mobile.
- ViewModel berperan sebagai inti dari MVVM, menghubungkan Model dan View dengan cara yang lebih terstruktur dan terkendali dibandingkan dengan Controller dalam MVC.
<<<<<<< HEAD
=======

## Tugas 3
Apa perbedaan antara form POST dan form GET dalam Django?
Dalam Django, seperti dalam banyak kerangka kerja web lainnya, ada dua metode HTTP yang umum digunakan untuk mengirim data dari formulir HTML ke server: POST dan GET. Berikut adalah perbedaan antara keduanya:

Metode POST (HTTP POST):
- Penggunaan Utama: Formulir yang dikirim dengan metode POST biasanya digunakan untuk mengirim data yang sensitif atau data yang akan mengubah status server, seperti mengirim data pendaftaran pengguna atau menambahkan entri ke dalam basis data.
- Data Terkirim: Data formulir dikirim dalam badan permintaan HTTP, yang tidak terlihat di URL. Oleh karena itu, data tidak terlihat di bilah alamat browser.
- Batasan Data: Tidak ada batasan praktis pada ukuran data yang dapat dikirimkan dengan metode POST.
- Keamanan: Lebih aman daripada metode GET karena data tidak terlihat di URL. Ini membuatnya lebih cocok untuk mengirim data sensitif.
- Pencarian: Data yang dikirimkan dengan metode POST tidak bisa di-bookmark atau disebarkan dengan mudah, karena data tidak terlihat di URL.

Metode GET (HTTP GET):
- Penggunaan Utama: Formulir yang dikirim dengan metode GET biasanya digunakan untuk permintaan pencarian atau akses ke data yang tidak memengaruhi status server. Misalnya, pencarian produk di toko online atau filter daftar posting blog.
- Data Terkirim: Data formulir dikirim sebagai parameter query string di URL, yang terlihat di bilah alamat browser.
- Batasan Data: Terdapat batasan pada ukuran data yang dapat dikirimkan dengan metode GET, tergantung pada server dan browser, dan data yang terlalu besar mungkin tidak dapat dikirim dengan metode ini.
- Keamanan: Kurang aman dibandingkan metode POST karena data terlihat di URL. Data yang dikirim dengan metode GET dapat dengan mudah diakses dan disebarkan.
- Pencarian: Data yang dikirim dengan metode GET dapat dengan mudah di-bookmark atau disebarkan melalui tautan.

Apa perbedaan utama antara XML, JSON, dan HTML dalam konteks pengiriman data?

XML (eXtensible Markup Language), JSON (JavaScript Object Notation), dan HTML (Hypertext Markup Language) adalah tiga format yang berbeda yang digunakan untuk mengirim dan menyusun data dalam konteks web dan komunikasi data. Berikut adalah perbedaan utama antara ketiganya dalam konteks pengiriman data:

XML (eXtensible Markup Language):
- Struktur: XML adalah bahasa markup yang digunakan untuk mendefinisikan aturan khusus dan hierarki struktur data. Ini memungkinkan penggunaan tag yang dapat disesuaikan untuk mendefinisikan elemen-elemen data.
- Legibilitas: XML cenderung lebih berat secara sintaksis dan memiliki lebih banyak karakter khusus (seperti < dan >) dibandingkan dengan JSON dan HTML. Hal ini membuatnya kurang mudah dibaca oleh manusia.
- Tujuan: XML umumnya digunakan untuk pertukaran data yang memiliki struktur kompleks, seperti dokumen berbasis teks, konfigurasi, atau data terstruktur lainnya. Itu adalah pilihan umum dalam SOAP (Simple Object Access Protocol) untuk layanan web.
- Pemrosesan: Memerlukan analisis berbasis pohon, yang membuatnya lebih lambat daripada JSON dan HTML dalam beberapa kasus.

JSON (JavaScript Object Notation):
- Struktur: JSON adalah format data yang ringan dan mudah dibaca, yang berbasis pada sintaksis objek JavaScript. Data diwakili sebagai pasangan "kunci-nilai" yang dapat bersarang dalam struktur hirarkis.
- Legibilitas: JSON lebih mudah dibaca oleh manusia dibandingkan dengan XML karena memiliki sintaksis yang lebih sederhana dan kurang karakter khusus.
- Tujuan: JSON sangat populer untuk pertukaran data dalam pengembangan web dan penggunaan umumnya mencakup API web, konfigurasi, dan penyimpanan data.
- Pemrosesan: JSON lebih cepat dan lebih mudah diproses oleh browser dan banyak bahasa pemrograman karena memiliki sintaksis yang mirip dengan objek.

HTML (Hypertext Markup Language):
- Struktur: HTML adalah bahasa markup yang digunakan untuk membuat konten web dan menentukan tampilan dan perilaku elemen-elemen di dalamnya. Ini memiliki tag dan atribut yang ditujukan untuk mengatur tampilan web.
- Legibilitas: HTML dirancang khusus untuk menampilkan konten web kepada pengguna dan memiliki sintaksis yang lebih mudah dibaca oleh manusia dibandingkan dengan XML atau JSON.
- Tujuan: HTML digunakan untuk membuat halaman web, menampilkan informasi kepada pengguna, dan mengatur tampilan dan interaksi dalam konteks web.
- Pemrosesan: HTML diterjemahkan oleh browser untuk menampilkan halaman web kepada pengguna, dan tidak digunakan secara luas untuk pertukaran data terstruktur.

Ketiganya memiliki kegunaan dan konteks yang berbeda, dan pemilihan format tergantung pada kebutuhan aplikasi dan bagaimana data akan digunakan. JSON biasanya menjadi pilihan yang lebih umum untuk pertukaran data di web karena kesederhanaan dan keterbacaannya, sementara XML digunakan lebih umum dalam beberapa lingkup yang memerlukan struktur data yang kompleks. HTML, sementara itu, digunakan untuk membuat halaman web yang dapat diakses oleh pengguna.

Mengapa JSON sering digunakan dalam pertukaran data antara aplikasi web modern?

- Keterbacaan oleh Manusia: JSON memiliki sintaksis yang sederhana dan mudah dibaca oleh manusia. Ini membuatnya mudah dipahami oleh pengembang dan mempermudah debugging. Struktur data JSON berbasis pasangan "kunci-nilai" yang mirip dengan objek dalam banyak bahasa pemrograman, sehingga mudah diinterpretasikan.
- Ringan: JSON adalah format data yang ringan dengan overhead yang minimal. Ini membuatnya efisien dalam hal pengiriman data melalui jaringan, mengurangi beban pada server dan menghemat bandwidth.
- Struktur Hierarkis: JSON mendukung struktur data hierarkis dan bersarang, yang memungkinkan Anda untuk mewakili data yang kompleks dengan cara yang mudah dimengerti dan diorganisir. Anda dapat dengan mudah menambahkan objek dalam objek atau daftar dalam objek.
- Dukungan Cross-Platform: JSON dapat digunakan di berbagai platform dan bahasa pemrograman. Sebagian besar bahasa pemrograman modern memiliki dukungan bawaan atau pustaka untuk mengurai dan membuat JSON, menjadikannya format data yang sangat interoperabel.
- Kompatibilitas dengan JavaScript: JSON dirancang berdasarkan sintaksis objek JavaScript, sehingga dapat digunakan langsung di dalam kode JavaScript tanpa perlu transformasi atau parsing tambahan. Ini membuatnya sangat sesuai untuk komunikasi antara server dan aplikasi web yang berjalan di browser.
- Dukungan Browser: Banyak browser modern memiliki fungsi JSON.parse() dan JSON.stringify() yang memungkinkan pengolahan data JSON dengan mudah. Ini mempermudah interaksi dengan API web dan pengiriman data dari server ke browser.
Paket Data: JSON mendukung berbagai jenis data, termasuk teks, angka, string, daftar, objek, dan nilai-nilai boolean. Ini memungkinkan Anda untuk mengirimkan data yang beragam dan memodelkan struktur data dengan sangat baik.
- Pembaruan Mudah: Karena sifat fleksibel JSON, Anda dapat dengan mudah menambah atau menghapus bidang dalam objek JSON tanpa memengaruhi kestabilan aplikasi yang ada. Ini berguna dalam pengembangan evolusioner dan pemeliharaan aplikasi.
- Keamanan: JSON, jika diimplementasikan dengan benar, tidak memiliki celah keamanan yang signifikan. Ini memungkinkan pertukaran data yang relatif aman antara aplikasi web modern.

Karena keunggulan-keunggulan ini, JSON telah menjadi format data yang dominan dalam pertukaran data antara aplikasi web modern, terutama dalam konteks penggunaan API (Application Programming Interface). JSON memberikan keseimbangan yang baik antara keterbacaan manusia dan efisiensi komputer, sehingga sangat cocok untuk berbagai kasus penggunaan dalam pengembangan web dan layanan web.

Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).

Membuat input form untuk menambahkan objek model pada app sebelumnya.
- Membuat folder templates pada root folder dan buatlah sebuah berkas HTML baru bernama base.html -> Modifikasi settings.py agar dapat menggunakan base.html sebagai template -> Membuat forms.py untuk membuat struktur form yang dapat menerima data produk baru -> Membuat fungsi create_product pada views.py untuk menambahkan product dan menyimpannya pada database -> Membuat create_product.html untuk form input yang tampil pada browser -> Menambahkan code untuk memperlihatkan data produk.

Tambahkan 5 fungsi views untuk melihat objek yang sudah ditambahkan dalam format HTML, XML, JSON, XML by ID, dan JSON by ID.

- Lima fungsi untuk menampilkan XML dan JSON memiliki konsep yang sama, yaitu mengambil semua objek dan kemudian objek tersebut di-serialize menjadi format XML dan JSON menggunakan serializer
- Untuk fungsi menampilkan XML dan JSON yang difilter dengan id, cukup ditambahkan parameter id sehingga fungsi hanya memberikan object yang sudah difilter berdasarkan id

Membuat routing URL untuk masing-masing views yang telah ditambahkan pada poin 2.

- Menambahkan path untuk setiap fungsi baru.
```
    path('create-product', create_product
    name='create_product'),
    path('xml/', show_xml, name='show_xml'),
    path('json/', show_json, name='show_json'), 
    path('xml/<int:id>/', show_xml_by_id, name='show_xml_by_id'),
    path('json/<int:id>/', show_json_by_id, name='show_json_by_id'), 
```

#Notes: #Notes: Saya hanya menjelaskan bagaimana implementasi saya dan maksud dari implementasi saya. Untuk detail code dapat dilihat pada setiap file yang sesuai 


## Tugas 4
Apa itu Django UserCreationForm, dan jelaskan apa kelebihan dan kekurangannya?
- Django UserCreationForm adalah salah satu formulir bawaan (built-in form) yang disediakan oleh Django untuk mempermudah proses pembuatan akun pengguna (user account) dalam aplikasi web yang menggunakan Django. Form ini digunakan untuk mengumpulkan data yang diperlukan untuk membuat akun pengguna, seperti nama pengguna (username), kata sandi (password), dan lainnya. Kelebihan dan kekurangan dari UserCreationForm adalah sebagai berikut:
- Kelebihan:
    - Mudah Digunakan: UserCreationForm sudah terintegrasi dengan Django Authentication System, sehingga mudah digunakan tanpa perlu menulis kode dari awal.
    - Validasi Otomatis: Form ini menyertakan validasi otomatis untuk memastikan bahwa data yang dimasukkan pengguna sesuai dengan persyaratan yang ditentukan, seperti kompleksitas kata sandi.
    - Kustomisasi: Anda dapat menyesuaikan UserCreationForm sesuai dengan kebutuhan aplikasi Anda dengan mengganti atau menambahkan bidang-bidang kustom atau validasi tambahan.
- Kekurangan:
    - Tampilan Terbatas: Form ini hanya menyediakan pola dasar untuk tampilan form, dan Anda mungkin perlu menyesuaikannya lebih lanjut untuk mencocokkan desain aplikasi Anda.
    - Fleksibilitas Terbatas: Jika Anda memerlukan lebih banyak bidang atau logika yang kompleks dalam formulir pendaftaran, Anda mungkin perlu membuat formulir khusus sendiri daripada mengandalkan UserCreationForm.

Apa perbedaan antara autentikasi dan otorisasi dalam konteks Django, dan mengapa keduanya penting?

- Autentikasi adalah proses verifikasi identitas pengguna, yaitu memeriksa apakah pengguna adalah orang yang mereka klaim. Dalam Django, autentikasi umumnya dilakukan dengan memeriksa nama pengguna (username) dan kata sandi (password) pengguna.
- Otorisasi adalah proses yang memutuskan apa yang diizinkan oleh pengguna yang sudah terotentikasi untuk lakukan atau akses dalam sistem. Ini melibatkan pengaturan izin dan peran (roles) yang menentukan akses ke bagian-bagian tertentu dari aplikasi. Django memiliki sistem otorisasi bawaan yang memungkinkan Anda mengontrol akses ke tampilan dan sumber daya tertentu berdasarkan peran pengguna.

Apa itu cookies dalam konteks aplikasi web, dan bagaimana Django menggunakan cookies untuk mengelola data sesi pengguna?
- Cookies dalam konteks aplikasi web adalah file data yang disimpan di sisi klien (di browser pengguna) dan digunakan untuk menyimpan informasi tertentu yang dapat diakses oleh server. Django menggunakan cookies untuk mengelola data sesi pengguna, seperti ID sesi atau token autentikasi, yang digunakan untuk mengidentifikasi dan mengatur keadaan sesi pengguna selama kunjungan mereka ke situs web.

Apakah penggunaan cookies aman secara default dalam pengembangan web, atau apakah ada risiko potensial yang harus diwaspadai?

Penggunaan cookies tidak selalu aman secara default dalam pengembangan web. Beberapa risiko potensial yang harus diwaspadai adalah:
- Peretasan Cookie: Cookie dapat disadap jika tidak dienkripsi dengan benar atau jika terdapat celah keamanan dalam aplikasi web.
- Man in the Middle (MITM) Attacks: Peretas dapat mencoba mencuri atau memodifikasi cookies selama transfer data antara klien dan server.
- Kebocoran Data Pribadi: Data sensitif yang disimpan dalam cookies dapat bocor jika tidak dienkripsi dengan benar atau jika pengaturan cookie tidak benar.

Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).

Mengimplementasikan fungsi registrasi, login, dan logout untuk memungkinkan pengguna untuk mengakses aplikasi sebelumnya dengan lancar.

- Membuat function register -> Menambahkan UserCreationForm sebagai template form -> Membuat validasi dan jika valid maka data dari input form disimpan dalam database -> Membuat register.html untuk menampilkan form dan message
- Membuat function login -> Menambahkan function authenticate untuk melakukan autentikasi dan login jika autentikasi berhasil -> Memasukkan input username dan password pada function authenticate -> Membuat login.html untuk menampilkan form dan message
- Membuat function logout -> Menambahkan function logout untuk melakukan logout user.

- Kemudian ketiga fungsi tersebut didaftarkan path nya pada urls.py pada main.

Membuat dua akun pengguna dengan masing-masing tiga dummy data menggunakan model yang telah dibuat pada aplikasi sebelumnya untuk setiap akun di lokal.

- Melakukan registrasi dua akun, yaitu davin dan ruizhi -> Login user davin -> Menambahkan item dengan button add new product sebanyak 3 item -> Logout

- Melakukan langkah yang sama untuk user ruizhi

Menghubungkan model Item dengan User

- Modifikasi models.py dengan menambahkan column user dengan ForeignKey untuk menghubungkan satu produk dengan satu user melalui sebuah relationship -> Modifikasi fungsi create_product pada views.py agar item tidak langsung disimpan ke dalam database (commit dahulu kemudian push) -> Modifikasi fungsi show_main dengan mengubah variable products yang awalnya semua item yang disimpan dalam database (include item user lain), kini item disimpan dalam variable product adalah item-item milik user (difilter berdasarkan user yang saat ini login)

- Melakukan migrasi karena terdapat penambahan column user pada models.py. Setiap perubahan model harus dilakukan migrasi ke dalam database

Menampilkan detail informasi pengguna yang sedang logged in seperti username dan menerapkan cookies seperti last login pada halaman utama aplikasi.

- Menambahkan fungsi set.cookie pada fungsi login user untuk untuk membuat _cookie last_login dan menambahkannya ke dalam response -> Menambahkan context last_login yang berisi request cookies last_login agar dapat dirender pada main.html -> Menambahkan code untuk mendapatkan data last_login pada main.html 

- Menambahkan fungsi delete.cookie pada fungsi logout untuk mereset cookie ketika logout. Agar nantinya saat user login kembali data yang didapatkan adalah data terbaru.

#Notes: Saya hanya menjelaskan bagaimana implementasi saya dan maksud dari implementasi saya. Untuk detail code dapat dilihat pada setiap file yang sesuai 




>>>>>>> 0673063 (submit tugas 4)
