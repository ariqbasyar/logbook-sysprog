# Stat System Call

## [Inode](https://en.wikipedia.org/wiki/Inode)
Inode table adalah struktur data pada traditional Unix-style file system seperti
ext3 dan ext4 yang bertugas untuk menyimpan properti dan alokasi block dari
sebuah file atau direktori.

## [Stat structure](https://en.wikipedia.org/wiki/Stat_(system_call)#stat_structure)
Adalah sebuah struktur data yang memiliki atribut untuk menyimpan data yang berkaitan
dengan sebuah file misal id dari device yang menyimpan file tersebut, nomor inode,
file type, mode dan masih banyak yang lainnya. Hal ini bisa di lihat di manual
page dari [stat](https://man7.org/linux/man-pages/man2/stat.2.html).

## File descriptor
Adalah sebuah pointer ketika kita membuka file menggunakan system call open(),
file descriptor ini berfungsi sebagai pointer yang dapat digunakan untuk
membaca isi sebuah file, menuliskan buffer ke sebuah file atau menutup file
descriptor itu agar bisa digunakan oleh process lain.

## stat(), fstat(), lstat()
Apa perbedaannya?
### [stat()](https://man7.org/linux/man-pages/man2/stat.2.html)
Melihat status dari sebuah file atau direktori dan apabila menemui sebuah
symbolic link maka stat ini akan mengikuti symlink tersebut dan akan
mengembalikan status dari sebuah file yang dituju di symlink tersebut.
### [fstat()](https://man7.org/linux/man-pages/man2/fstat.2.html)
Melihat status sebuah file atau direktori yang dimana hanya bisa dilihat
menggunakan *file descriptor fd*
### [lstat()](https://man7.org/linux/man-pages/man2/lstat.2.html) 
Melihat status dari sebuah file atau direktori dan apabila menemui sebuah
symbolic link maka lstat ini tidak akan mengikuti link tersebut melainkan hanya
akan memberikan deskripsi dari link tersebut.

## Seberapa penting menutup sebuah file descriptor?
Contohnya adalah ketika membuka sebuah file menggunakan system call open() dan
ingin menuliskan sesuatu dari sebuah buffer ke file tersebut, sebelum di close
sebenarnya tidak benar - benar di tulis ke sana melainkan ke tempat yang
bersifat temporary. Nah kalau tidak menggunakan close() ketika menggunakan
fungsi open() maka data dari buffer tidak akan dituliskan ke file.

## File holes
Sebuah holes di dalam sebuah file itu dilambangkan menjadi angka 0, holes ini
terbuat ketika offset data yang ditulis ke sebuah file melebihi kapasitas file
itu sendiri yang menyebabkan data dari offset yang telah ditulis sampai file
size aslinya akan ditulis dengan angka 0. 

![File holes image](/images/file_holes.png)