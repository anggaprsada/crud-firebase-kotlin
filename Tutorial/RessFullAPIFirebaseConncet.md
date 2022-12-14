# Connect ke Firebase
Aplikasi yang kita buat harus kita koneksikan ke firebase dengan cara sebagai berikut:

## Menambahkan Firebase mengunakan Firebase Concole
Penambahan Firebase ke aplikasi memerlukan tindakan baik di [Firebase console](https://console.firebase.google.com/u/0/) maupun di project Android yang terbuka (misalnya, Anda mendownload file konfigurasi Firebase dari console, lalu memindahkannya ke project Android).
*Buat Project Firebase</br>
Agar dapat menambahkan Firebase ke aplikasi Android, Anda perlu membuat project Firebase untuk dihubungkan ke aplikasi Android.
* Daftarkan aplikasi ke Firebase</br>
  + Buka [Firebase console](https://console.firebase.google.com/u/0/).
  + Di bagian tengah halaman ringkasan project, klik ikon Android (plat_android) atau Add app untuk meluncurkan alur kerja penyiapan.
  + Masukkan nama paket aplikasi Anda di kolom Android package name.<br/>
     Pastikan untuk memasukkan nama paket yang benar-benar digunakan aplikasi Anda. Nilai nama paket peka huruf besar/kecil dan tidak dapat diubah untuk aplikasi Android Firebase ini setelah didaftarkan ke project Firebase Anda.
  + Klik Register app.<b/>
* Tambahkan file konfigurasi Firebase<br/>
  + Tambahkan file konfigurasi Andoid ke aplikasi
    - Klik Download google-services.json untuk mendapatkan file konfigurasi Android Firebase Anda (google-services.json).
    - Pindahkan file konfigurasi ke direktori modul (level aplikasi) aplikasi Anda.
    - ![resources/logo-artivisi.png](https://www.gstatic.com/mobilesdk/160426_mobilesdk/images/android_studio_project_panel@2x.png)
  + Untuk mengaktifkan produk Firebase di aplikasi, tambahkan [plugin google-services](https://developers.google.com/android/guides/google-services-plugin) ke file Gradle.
* Tambahkan Firebase SDK ke aplikasi
  + Dalam file Gradle level root (level project), <code translate="no" dir="ltr">build.gradle</code>, tambahkan aturan untuk menyertakan plugin Gradle Layanan Google. Pastikan Anda juga memiliki repositori Maven Google.
  ```kotlin
  buildscript {
    repositories {
        google()
    }
    dependencies {
        classpath 'com.google.gms:google-services:4.3.13'
    }
  }
  ```
  + Dalam file Gradle modul (level aplikasi), biasanya <code translate="no" dir="ltr">app/build.gradle</code>, terapkan plugin Gradle Layanan Google:
  ```kotlin
  apply plugin: 'com.google.gms.google-services'
  plugins {
    //...
    id 'com.google.gms.google-services'
  }

  android 
  ```
* Tambahkan Firebase SDK ke aplikasi
  + Dengan Firebase Android BoM, deklarasikan dependensi untuk produk Firebase yang ingin digunakan di aplikasi. Deklarasikan dalam file Gradle modul (level aplikasi), biasanya <code translate="no" dir="ltr">app/build.gradle</code>.
  ```kotlin
  dependencies {
  //...
  //untuk koneksi ke authentication
  implementation 'com.google.firebase:firebase-auth:21.0.7'
  //untuk koneksi ke realtime database
  implementation 'com.google.firebase:firebase-database:20.0.5'
  implementation 'com.google.firebase:firebase-database-ktx:20.0.5'
  ```
  + Sinkronkan aplikasi Anda untuk memastikan bahwa semua dependensi memiliki versi yang diperlukan.
