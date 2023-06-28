Ringkasan :
- Bab 12
*Pendahuluan

Aplikasi kadang-kadang memerlukan versi perpustakaan tertentu, karena aplikasi mungkin memerlukan bug tertentu yang telah diperbaiki atau aplikasi mungkin ditulis menggunakan versi lama antarmuka perpustakaan. Ini berarti tidak mungkin satu instalasi Python memenuhi persyaratan setiap aplikasi. Jika aplikasi A membutuhkan versi 1.0 dari modul tertentu tetapi aplikasi B membutuhkan versi 2.0, maka persyaratan tersebut bertentangan dan menginstal versi 1.0 atau 2.0 akan membuat satu aplikasi tidak dapat dijalankan. Jika aplikasi B memerlukan pustaka yang ditingkatkan ke versi 3.0, ini tidak akan memengaruhi lingkungan aplikasi A.

*Membuat Lingkungan Virtual

Modul yang digunakan untuk membuat dan mengelola lingkungan virtual disebut venv. File definisi variabel lingkungan Env yang didukung oleh beberapa perkakas. Setelah Anda membuat lingkungan virtual, Anda dapat mengaktifkannya. Mengaktifkan lingkungan virtual akan mengubah prompt shell Anda untuk menunjukkan lingkungan virtual apa yang Anda gunakan, dan memodifikasi lingkungan sehingga menjalankan python akan memberi Anda versi dan pemasangan Python tertentu.

*Mengelola Paket dengan pip

Anda dapat menginstal, memutakhirkan, dan menghapus paket menggunakan program bernama pip. Secara default pip akan menginstal paket dari Python Package Index. Jika Anda menjalankan kembali perintah ini, pip akan melihat bahwa versi yang diminta telah diinstal dan tidak melakukan apa pun.
python -m pip uninstall diikuti oleh satu atau lebih nama paket akan menghapus paket dari lingkungan virtual.
pip memiliki lebih banyak opsi. Konsultasikan panduan Memasang Modul Python untuk dokumentasi lengkap untuk pip.