Ringkasan :
- Bab 10
*Antarmuka Sistem Operasi
Ini akan menjaga os.open membayangi fungsi buka bawaan yang beroperasi jauh berbeda.

*Argumen Baris Perintah

Skrip utilitas umum seringkali perlu memproses argumen baris perintah. Argumen ini disimpan dalam atribut argv modul sys sebagai daftar.
Modul argparse menyediakan mekanisme yang lebih canggih untuk memproses argumen baris perintah.

*Error Output Redirection dan Program Termination
Modul sys juga memiliki atribut untuk stdin, stdout, dan stderr.

*Pencocokan Pola Tali
Modul re menyediakan alat ekspresi reguler untuk pemrosesan string tingkat lanjut.

*Matematika
Proyek SciPy memiliki banyak modul lain untuk perhitungan numerik.

*Akses internet
Ada sejumlah modul untuk mengakses internet dan memproses protokol internet. (Perhatikan bahwa contoh kedua memerlukan server surat yang berjalan di localhost.)

*Tanggal dan Waktu

Modul datetime menyediakan kelas untuk memanipulasi tanggal dan waktu dengan cara sederhana dan kompleks. Modul ini juga mendukung objek yang sadar zona waktu.

*Kompresi data
Pengarsipan data umum dan format kompresi didukung langsung oleh modul termasuk: zlib, gzip, bz2, lzma, zipfile dan tarfile.

*Pengukuran Kinerja
Sebagai contoh, mungkin tergoda untuk menggunakan fitur packing dan unpacking tuple daripada pendekatan tradisional untuk bertukar argumen.

*Konstruksi Tes Kontrol Kualitas
Sesederhana memotong-dan-menempelkan panggilan biasa beserta hasilnya ke dalam dokumen.

*Termasuk Baterai

Python memiliki filosofi «termasuk baterai». Ini paling baik dilihat melalui kemampuan canggih dan tangguh dari paket-paketnya yang lebih besar. Terlepas dari nama modul, tidak diperlukan pengetahuan langsung atau penanganan XML.
Paket email adalah pustaka untuk mengelola pesan email, termasuk MIME dan dokumen pesan berbasis RFC 2822 lainnya. Modul csv mendukung pembacaan dan penulisan file secara langsung dalam format Comma-Separated Value, umumnya didukung oleh database dan spreadsheet. Pemrosesan XML didukung oleh paket xml.etree.ElementTree, xml.dom dan xml.sax. Bersama-sama, modul dan paket ini sangat menyederhanakan pertukaran data antara aplikasi Python dan alat lainnya.

- Bab 11
*Tur Singkat Pustaka Standar — Bagian II
Modul ini jarang muncul dalam skrip kecil.

*Pemformatan Keluaran
Modul pprint menawarkan kontrol yang lebih canggih atas pencetakan objek bawaan dan yang ditentukan pengguna dengan cara yang dapat dibaca oleh juru bahasa. Modul lokal mengakses database format data khusus budaya.

*Template Mengelilingi

Placeholder dengan tanda kurung memungkinkannya diikuti oleh lebih banyak huruf alfanumerik tanpa spasi. Metode pengganti memunculkan KeyError saat placeholder tidak disediakan dalam kamus atau argumen kata kunci.

*Bekerja dengan Tata Letak Rekaman Data Biner
Contoh berikut menunjukkan cara mengulang informasi header dalam file ZIP tanpa menggunakan modul zipfile.

*Thread multi-threading

dapat digunakan untuk meningkatkan daya tanggap aplikasi yang menerima input pengguna saat tugas lain berjalan di latar belakang. Tantangan utama dari aplikasi multi-utas adalah mengoordinasikan utas yang berbagi data atau sumber daya lainnya. Aplikasi yang menggunakan objek Queue untuk komunikasi dan koordinasi antar-thread lebih mudah dirancang, lebih mudah dibaca, dan lebih dapat diandalkan.

*Logging

Modul logging menawarkan fitur lengkap dan sistem logging yang fleksibel. Opsi keluaran lainnya termasuk merutekan pesan melalui email, datagram, soket, atau ke Server HTTP.

*Referensi Lemah

Modul weakref menyediakan alat untuk melacak objek tanpa membuat referensi. Ketika objek tidak lagi diperlukan, secara otomatis dihapus dari tabel ref lemah dan panggilan balik dipicu untuk objek ref lemah.

*Alat untuk Bekerja dengan Daftar

Banyak kebutuhan struktur data dapat dipenuhi dengan tipe daftar bawaan. Modul array menyediakan objek array yang seperti daftar yang hanya menyimpan data homogen dan menyimpannya dengan lebih kompak.
Modul heapq menyediakan fungsi untuk mengimplementasikan tumpukan berdasarkan daftar reguler.

*Desimal Floating Point Arithmetic

Hasil Desimal menjaga trailing nol, secara otomatis menyimpulkan signifikansi empat tempat dari multiplicands dengan dua tempat signifikansi. Desimal mereproduksi matematika seperti yang dilakukan dengan tangan dan menghindari masalah yang dapat muncul ketika floating point biner tidak dapat secara tepat mewakili jumlah desimal.
