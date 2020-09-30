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