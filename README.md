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
