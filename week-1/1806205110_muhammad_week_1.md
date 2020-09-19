# Apa itu Pemrograman Sistem?
Pemrograman sistem biasanya adalah pemrograman yang dapat berinteraksi langsung dengan hardware. Desain dan penulisan kodenya khusus untuk dipakai oleh suatu sistem misal sebuah OS atau sistem lainnya. Pemrograman sistem ini meliputi operating system, I/O, firmware dan masih banyak lagi yang tidak terhubung langsung dengan user. Pemrograman sistem ini sangat berhubungan langsung dengan hardware, jadi para programmer harus memikirkan juga kira - kira hardware apa software yang dibuatnya bisa berjalan. 

# Apa perbedaan dari Scripting dan Programming language?
| Scripting language | Programming langauage |
| -------------------| --------------------- |
| Membutuhkan bahasa pemrograman<br>lain untuk diinterrpetasikan | dapat diinterpretasikan<br>langsung ke bahasa mesin |
| Biasa untuk automasi | Software Engineering |
| lebih sedikit kode | lebih banyak kode |
| dapat langsung dieksekusi | harus dicompile terlebih<br>dahulu |

# Apa perbedaan kernal dengan sistem operasi?
| Kernel | Sistem operasi |
| -------| -------------- |
| Menghubungkan sistem operasi dengan hardware | menghubungkan user dengan |
| bagian penting dari sistem operasi | operating system adalah sistem program |
| mengatur process yang berjalan | lebih sering berinteraksi dengan<br>user |

# Apa perbedaan process yang berjalan di user mode dan kernel mode?
| kernel mode | user mode |
| ----------- | --------- |
| error pada kode berakibat fatal untuk komputer | error masih dapat ditolerir |
| memiliki akses langsung ke memori | tidak memiliki akses langsung ke memori<br>(membutuhkan perizinan dari sistem APIs) |
kode yang sehari - hari kita eksekusi adalah pada user mode.

# Apa perbedaan program dengan process?
| Program | Process |
| ------- | ------- |
| terdiri dari kumpulan instruksi | adalah program yang berjalan(running) |
| bersifat pasif, berbentuk executeable | bersifat running, berbentuk process |
| tersimpan di disk | tersimpan di memori |

# Process memory terbagi menjadi 4 segmen, apa saja?
* Text section
Terdiri dari kode yang sudah dicompile dibaca dari disk ketika dijalankan
* Data section
Bertugas mengatur variable global, variable konstanta dan dependensi lainnya<br>sebelum program main dijalankan
* Heap
Digunakan untuk alokasi memori yang dinamis
* Stack
Berfungsi untuk variable local dari suatu process yang besarnya dialokasikan ketika program dijalankan

# Apa keunikan dari folder `/proc` pada linux ?
## Informasi detail dari CPU
file `/proc/cpuinfo` menyediakan informasi detail dari cpu yang tertanam pada suatu sistem.
`cat /proc/cpuinfo`
![Hasil cat file /proc/cpuinfo](/images/cpuinfo.png)

## Informasi memori atau RAM
file `/proc/meminfo` memiliki infomasi tentang memori dari memori total, free, cache, swap dan lain - lain. Saya ingin mencoba melihat memori untuk usage, cache dan swap nya menggunakan
`grep -E 'Mem|Cache|Swap' /proc/meminfo`

![Hasil grep meminfo](/images/meminfo.png)

## Informasi tentang berapa lama system tersebut menyala?
Informasi tentang lamanya sebuah system menyala, kita dapat mengetahui dari file `/proc/uptime`
`cat /proc/uptime`
![Hasil cat uptime](/images/uptime.png)

Di sana terdapat angka 5737205.97 yaitu me representasikan lama waktu sebuah sistem up dalam detik, jadi kalau di convert ke hari maka sistem/komputer saya sudah up selama 66.403 hari atau 66 hari 9 jam 40 menit

Nilai kedua adalah lama waktu yang dihabiskan setiap core dalam hitungan detik, nah karena logical processor hanya 1, maka waktu uptime system sama dengan lamanya processor saya bekerja

## Informasi tentang versi kernel yang sedang dipakai
Dapat diketahui di file `/proc/version`
`cat /proc/version`
![Hasil cat uptime](/images/kernel-version.png)

## Informasi tentang kernel modules yang sekarang sedang berjalan
Dapat diketahui di file `/proc/modules`
![Hasil cat uptime](/images/kernel-modules.png)
Sebenarnya output nya sangat panjang, mungkin ini sudah cukup mewakili.

## Informasi partisi
File `/proc/partitions` memberikan informasi yaitu  table yang berisi nomor major dan minor terhadap device untuk partisi, nomor - nomor itu bisa di mapping ke isi file `/proc/devices`.  Nah major number berfungsi untuk mapping di /proc/devices yaitu untuk melihat di device mana partisi itu berada. Nah kalau minor number itu adalah unique number untuk mengidentifikasi tiap - tiap device yang sama. Table ini sangat berhubungan dengan bagaimana kita membuat partisi untuk linux ini.

![Hasil cat /proc/partitions](/images/partitions.png)


# Apa perbedaan relative path dan absolute path?
Perbedaannya adalah, kalau relative path, maka relative terhadap dimana command tersebut dijalankan atau dimana user berada(dapat dilihat dengan command `pwd`) sedangkan absolute path, tidak melihat dimana command itu dijalankan, sebagai contoh:

Ketika saya di folder home (~/), saya dapat mengakses ssh key saya yaitu misal .ssh/id_rsa tetapi beda kalau saya pindah folder misal sekarang di ~/Documents maka saya tidak bisa mengakses .ssh/id_rsa lagi karena tidak ada file .ssh/id_rsa di ~/Documents.
Nah kalau absolute path, saya dapat mengakses rsa key saya yaitu dengan memberikan absolute path nya dan biasanya absolute path menggunakan root(/) atau home(~/) maka saya dapat mengakses rsa key saya dengan memberikan path ~/.ssh/id_rsa atau /home/username/.ssh/id_rsa.

# Filesystem Hierarchy Standard
Itulah nama standard yang mendefine struktur dari folder pada distribusi linux. Struktur ini merancang bahwa semua folder berada pada folder root (/) walau berada pada disk yang berbeda, struktur nya tetap sama. Contoh folder - folder yang default ada pada root adalah (/), (/boot), (/dev), (/proc), dan lain - lain bisa di lihat di sini https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard