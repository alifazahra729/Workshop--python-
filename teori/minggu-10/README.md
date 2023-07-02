Ringkasan :
- PEP 249
*Pengantar

API ini telah didefinisikan untuk mendorong kesamaan antara modul Python yang digunakan untuk mengakses database. Dengan melakukan ini, kami berharap dapat mencapai konsistensi yang mengarah ke modul yang lebih mudah dipahami, kode yang umumnya lebih portabel di seluruh basis data, dan jangkauan konektivitas basis data yang lebih luas dari Python. Dokumen ini menjelaskan Spesifikasi Python Database API 2.0 dan satu set ekstensi opsional umum.

Konstruktor

Dibutuhkan sejumlah parameter yang bergantung pada basis data.
Berbagi dalam konteks di atas berarti bahwa dua utas dapat menggunakan sumber daya tanpa membungkusnya menggunakan semafor mutex untuk menerapkan penguncian sumber daya.

InterfaceError
Ini harus menjadi subclass dari Error.

IntegrityError
Ini harus menjadi subclass dari DatabaseError.

Pengecualian InternalError
dimunculkan ketika database mengalami kesalahan internal, mis.

Pengecualian NotSupportedError
dimunculkan jika metode atau database API digunakan yang tidak didukung oleh database, mis.

Objek Koneksi

Objek koneksi harus merespons metode berikut. Metode koneksi. Tutup koneksi sekarang daripada kapanpun. Komit setiap transaksi yang tertunda ke database.

Perhatikan bahwa jika database mendukung fitur auto-commit, fitur ini harus dinonaktifkan terlebih dahulu. Metode antarmuka mungkin disediakan untuk mengaktifkannya kembali. Metode ini opsional karena tidak semua database menyediakan dukungan transaksi. Jika database memang menyediakan transaksi, metode ini menyebabkan database memutar kembali ke awal transaksi yang tertunda.

Kembalikan Objek Kursor baru menggunakan koneksi. Jika database tidak menyediakan konsep kursor langsung, modul harus meniru kursor menggunakan cara lain sejauh yang dibutuhkan oleh spesifikasi ini.

Urutan parameter harus berisi satu entri untuk setiap argumen yang diharapkan oleh prosedur. Parameter input dibiarkan tidak tersentuh, parameter output dan input/output diganti dengan nilai yang mungkin baru. Prosedur juga dapat memberikan hasil yang ditetapkan sebagai output. Tutup kursor sekarang.

Parameter dapat diberikan sebagai urutan atau pemetaan dan akan terikat pada variabel dalam operasi. Variabel ditentukan dalam notasi khusus basis data . Referensi ke operasi akan dipertahankan oleh kursor. Jika objek operasi yang sama diteruskan lagi, maka kursor dapat mengoptimalkan perilakunya.

Ini paling efektif untuk algoritme di mana operasi yang sama digunakan, tetapi parameter yang berbeda terikat padanya . Untuk efisiensi maksimum saat menggunakan kembali suatu operasi, yang terbaik adalah menggunakan . Metode Setinputsizes untuk menentukan jenis dan ukuran parameter sebelumnya. Persiapkan operasi basis data dan kemudian jalankan terhadap semua urutan parameter atau pemetaan yang ditemukan di urutan seq_of_parameters.

Modul bebas untuk mengimplementasikan metode ini menggunakan beberapa panggilan ke . Jalankan metode atau dengan menggunakan operasi array agar database memproses urutan secara keseluruhan dalam satu panggilan. Penggunaan metode ini untuk operasi yang menghasilkan satu atau lebih rangkaian hasil merupakan perilaku yang tidak terdefinisi, dan penerapannya diizinkan untuk memunculkan pengecualian saat mendeteksi bahwa rangkaian hasil telah dibuat oleh pemanggilan operasi. Ambil kumpulan baris berikutnya dari hasil kueri, mengembalikan urutan dari urutan .

Jumlah baris untuk diambil per panggilan ditentukan oleh parameter. Jika tidak diberikan, ukuran array kursor menentukan jumlah baris yang akan diambil. Metode harus mencoba mengambil baris sebanyak yang ditunjukkan oleh parameter ukuran. Jika parameter ukuran digunakan, maka yang terbaik adalah mempertahankan nilai yang sama dari satu .

Ambil semua baris hasil kueri, kembalikan sebagai urutan dari urutan . Metode ini akan membuat kursor melompat ke set berikutnya yang tersedia, membuang baris yang tersisa dari set saat ini. Jika tidak ada set lagi, metode mengembalikan Tidak ada. Ambil banyak.

Setel ukuran penyangga kolom untuk pengambilan kolom besar . Kolom ditentukan sebagai indeks ke dalam urutan hasil. Tidak menentukan kolom akan menetapkan ukuran default untuk semua kolom besar di kursor.

Banyak database perlu memiliki input dalam format tertentu untuk mengikat parameter input operasi. Misalnya, jika input ditujukan untuk kolom DATE, maka input tersebut harus terikat ke database dalam format string tertentu. Ketika modul database melihat objek string Python, ia tidak tahu apakah harus diikat sebagai kolom CHAR sederhana, sebagai item BINARY mentah, atau sebagai TANGGAL.

Tipe ROWID

Objek tipe ini digunakan untuk mendeskripsikan kolom «ID Baris» dalam database.

*Petunjuk Implementasi untuk Penulis Modul

- Objek tanggal/waktu dapat diimplementasikan sebagai objek modul datetime Python atau menggunakan paket mxDateTime . Keduanya menyediakan semua konstruktor dan metode yang diperlukan di tingkat Python dan C. - Jenis objek yang disukai untuk objek Biner adalah tipe buffer yang tersedia dalam Python standar mulai dari versi 1.5.2. Silakan lihat dokumentasi Python untuk detailnya.

C dalam distribusi sumber Python.

*Ekstensi DB API opsional

Selama masa pakai DB API 2.0, pembuat modul sering memperluas implementasinya melebihi apa yang diperlukan oleh spesifikasi DB API ini. Untuk meningkatkan kompatibilitas dan menyediakan jalur pemutakhiran yang bersih ke kemungkinan versi spesifikasi yang akan datang, bagian ini menentukan kumpulan ekstensi umum untuk spesifikasi inti DB API 2.0. Seperti semua fitur opsional DB API, pembuat modul database bebas untuk tidak mengimplementasikan atribut dan metode tambahan ini atau untuk memunculkan NotSupportedError jika ketersediaan hanya dapat diperiksa saat run-time. Telah diusulkan untuk menggunakan ekstensi ini secara opsional terlihat oleh programmer dengan mengeluarkan peringatan Python melalui kerangka peringatan Python.

Indeks dapat dilihat sebagai indeks kursor secara berurutan. "Koneksi. Kesalahan, Koneksi. Semua kelas pengecualian yang ditentukan oleh standar DB API harus diekspos pada objek Connection sebagai atribut.

Atribut ini menyederhanakan penanganan kesalahan di lingkungan multikoneksi. » «Jika mode relatif , nilai diambil sebagai offset ke posisi saat ini di set hasil, jika disetel ke absolut, nilai menyatakan posisi target absolut. Dalam hal ini, posisi kursor tidak ditentukan .

*Catatan

Metode ini mungkin memunculkan NotSupportedError untuk menandakan bahwa operasi tertentu tidak didukung oleh database.

«Ini adalah objek daftar Python tempat antarmuka menambahkan tupel untuk semua pesan yang diterima antarmuka dari database yang mendasari kursor ini. Daftar ini dihapus oleh semua panggilan metode kursor standar kecuali untuk . Ambil* panggilan secara otomatis untuk menghindari penggunaan memori yang berlebihan dan juga dapat dihapus dengan menjalankan kursor del. Pesan .

Semua pesan kesalahan dan peringatan yang dihasilkan oleh database ditempatkan ke dalam daftar ini, sehingga memeriksa daftar memungkinkan pengguna untuk memverifikasi pengoperasian yang benar dari pemanggilan metode. » Koneksi. Sama seperti Kursor. Pesan kecuali bahwa pesan dalam daftar berorientasi koneksi.

Daftar ini dihapus secara otomatis oleh semua panggilan metode koneksi standar untuk menghindari penggunaan memori yang berlebihan dan juga dapat dihapus dengan menjalankan koneksi del. «Versi sebelumnya tidak memiliki pengecualian StopIteration sehingga metode tersebut harus memunculkan IndexError sebagai gantinya. » « Jika operasi tidak menetapkan rowid atau jika database tidak mendukung rowid, atribut ini harus disetel ke Tidak ada.

Atribut ke query dan atur mode autocommit koneksi. Kembalikan True jika koneksi beroperasi dalam mode autocommit. Kembalikan Salah jika koneksi beroperasi dalam mode komit manual.

Menyetel atribut ke True atau False menyesuaikan mode koneksi yang sesuai. Mengubah pengaturan dari True ke False akan membuat database keluar dari mode autocommit dan memulai transaksi baru. Mengubah dari False ke True memiliki semantik yang bergantung pada basis data sehubungan dengan bagaimana transaksi yang tertunda ditangani. «.

Setiap sumber daya dalam transaksi global harus diberi kualifikasi cabang yang berbeda.

*Berbagai komponen harus memenuhi kriteria

ID Transaksi berikut dibuat dengan . Mengembalikan objek ID transaksi yang cocok untuk diteruskan ke . Tpc_* metode koneksi ini. Metode Koneksi TPC.

Memulai transaksi TPC dengan ID transaksi yang diberikan xid. Metode ini harus dipanggil di luar transaksi i. Kembalikan. Selain itu, merupakan kesalahan untuk memanggil .

Kembalikan dalam transaksi TPC. Melakukan tahap pertama transaksi yang dimulai dengan . Tpc_commit melakukan transaksi TPC yang sebelumnya disiapkan dengan . Manajer transaksi dapat memilih untuk melakukan ini jika hanya satu sumber daya yang berpartisipasi dalam transaksi global.

Saat dipanggil dengan ID transaksi xid, database melakukan transaksi yang diberikan. Jika ID transaksi yang tidak valid diberikan, ProgrammingError akan dimunculkan. Tpc_rollback mengembalikan transaksi TPC. Saat dipanggil dengan ID transaksi xid, ini mengembalikan transaksi yang diberikan.

Jika ID transaksi yang tidak valid diberikan, ProgrammingError dimunculkan. tpc_rollback. Jika database tidak mendukung pemulihan transaksi, mungkin mengembalikan daftar kosong atau memunculkan NotSupportedError.

*Pertanyaan yang Sering Diajukan

Database SIG sering melihat pertanyaan berulang tentang spesifikasi DB API.

*Menjawab

Sebagian besar dari mereka menggunakan pendekatan menggunakan nama kolom yang didefinisikan dalam atribut kursor. Perhatikan bahwa alasan untuk tidak memperluas spesifikasi DB API juga mendukung nilai kembalian kamus untuk . - Beberapa database tidak mendukung nama kolom peka huruf besar kecil atau mengonversinya secara otomatis ke semua huruf kecil atau semua karakter huruf besar. - Kolom dalam rangkaian hasil yang dihasilkan oleh kueri tidak dipetakan ke nama kolom tabel dan database biasanya menghasilkan nama untuk kolom ini dengan cara yang sangat spesifik basis data.

Akibatnya, mengakses kolom melalui kunci kamus bervariasi antara database dan membuat penulisan kode portabel menjadi tidak mungkin. Python Database API 2.0 memperkenalkan beberapa perubahan besar dibandingkan dengan versi 1.0. Karena beberapa perubahan ini akan menyebabkan skrip berbasis DB API 1.0 rusak, nomor versi utama disesuaikan untuk mencerminkan perubahan ini. Set yang dihasilkan harus mencakup semua tipe data dasar yang biasa ditemukan di database SQL modern.

- Konstanta dan metode baru. Nextset ditambahkan untuk menyediakan binding database yang lebih baik. Modul bebas mengembalikan nilai pengembalian gaya lama, tetapi ini tidak lagi diamanatkan oleh spesifikasi dan harus dianggap bergantung pada antarmuka basis data. - Pengecualian berbasis kelas dimasukkan ke dalam spesifikasi.

Pelaksana modul bebas memperluas tata letak pengecualian yang ditentukan dalam spesifikasi ini dengan mensubklasifikasikan kelas pengecualian yang ditentukan.

Jika database tidak mendukung fungsionalitas yang diperlukan oleh metode, antarmuka harus melontarkan pengecualian jika metode tersebut digunakan. Pendekatan yang lebih disukai adalah tidak mengimplementasikan metode dan dengan demikian membuat Python menghasilkan AttributeError jika metode tersebut diminta. Ini memungkinkan pemrogram untuk memeriksa kemampuan basis data menggunakan fungsi hasattr standar. Untuk beberapa antarmuka yang terkonfigurasi secara dinamis, mungkin tidak tepat untuk mengharuskan tersedianya metode secara dinamis.

Antarmuka ini kemudian harus memunculkan NotSupportedError untuk menunjukkan ketidakmampuan untuk melakukan roll back saat metode dipanggil. Antarmuka basis data dapat memilih untuk mendukung kursor bernama dengan mengizinkan argumen string ke metode. Modul akan menggunakan metode __getitem__ dari objek parameter untuk memetakan posisi atau nama ke nilai parameter. Istilah terikat mengacu pada proses pengikatan nilai input ke buffer eksekusi database.

Ambil * metode. metode __iter__. Istilah jumlah baris yang terpengaruh umumnya mengacu pada jumlah baris yang dihapus, diperbarui, atau disisipkan oleh pernyataan terakhir yang dijalankan pada kursor database. Perubahan seharusnya tidak memengaruhi modul yang ada atau penggunaan modul tersebut, karena semua kelas pengecualian kesalahan DB-API masih di-root pada kelas Kesalahan atau Peringatan.

Pada saat penulisan DB-API 2.0 pada tahun 1999, kerangka peringatan dengan Python belum ada. Banyak modul database yang mengimplementasikan atribut autocommit akan secara otomatis melakukan transaksi yang tertunda dan kemudian masuk ke mode autocommit. Dalam revisi DB-API mendatang, kami akan memperkenalkan metode baru. Setautocommit, yang memungkinkan pengaturan mode autocommit, dan make .

Komit otomatis atribut hanya-baca. Selain itu, kami sedang mempertimbangkan untuk menambahkan autocommit parameter kata kunci standar baru ke konstruktor Connection. Penulis modul didorong untuk menambahkan perubahan ini sebagai persiapan untuk perubahan ini.

*Ucapan Terima Kasih

Banyak terima kasih kepada Andrew Kuchling yang mengonversi Python Database API Specification 2.0 dari format HTML asli ke dalam format PEP pada tahun 2001.
