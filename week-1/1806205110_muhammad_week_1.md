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
