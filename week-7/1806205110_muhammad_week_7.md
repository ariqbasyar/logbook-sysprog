# Scripting

Scripting adalah dimana melakukan programming yang bahasa nya masih perlu
diinterpretasi oleh bahasa programming lain. Biasanya scripting dilakukan untuk
mempermudah suatu urusan manusia, seperti scheduler, atau scripting di web
seperti javascript dan lainnya.

## Types of Shell
* Bourne Shell

    Biasa dikenal dengan sh, adalah shell yang sangat sering dijumpai di unix
    system keuntungan dari memakai shell ini adalah pada simple nya, shell ini
    sangat simple dari mulai prompt nya yang hanya `$ `. Keuntungan lainnya
    adalah pada shell ini ada di berbagai unix system jadi sangat mudah
    beradaptasi ke server lain.

    Kerugian nya adalah pada kompatibilitas dengan command lain. Shell ini
    kurang *compatible* dengan command lain bahkan seperti command `source` pun
    tidak bisa digunakan di sh.

* Bourne-Again Shell

    Atau biasa disebut bash, merupakan lanjutan dari korn shell dan memiliki
    kemiripan dengan sh atau Bourne Shell. Untuk migrasi dari sesama keluarga
    Bourne cukup mudah karena memiliki fitur - fitur atau command yang mirip.
    Keuntungan nya adalah shell ini menjadi default di banyak system, jadi
    penggunaan nya pun sudah sangat meluas dan dokumentasi nya pun cukup banyak
    dari komunitasnya. Saya memakai shell ini dengan memasang framework
    [ohmybash/oh-my-bash](https://github.com/ohmybash/oh-my-bash) yaitu sebuah
    fancy bash dibuat oleh community dengan memberikan fitur seperti theme,
    plugins dan lainnya.

* TENEX C Shell

    atau biasa disebut TCSH, adalah next generation dari C Shell dimana shell
    ini support seluruh syntax dan built in dari C Shell dan menambahkan
    powerful comamnd line editing yaitu filename dan user ID checking, auto
    completions pada hostnames, variable names, aliases dan lainnya. kerugian
    memakai shell ini adalah tidak semua distro atau linux system sudah
    terinstall shell ini, dan katanya untuk memakai shell ini akan lebih baik
    kalau sebelumnya sudah memakai C Shell agar lebih mudah memahami syntax dan
    sebagainya.

* Korn Shell

    atau KSH. Shell ini tidak membutuhkan waktu banyak untuk menguasainya,
    tetapi shell ini dibuat dengan desain yang butuk dan dokumen yang juga buruk
    atau sedikit. KSH dapat membuat correction dari typing error menjadi lebih
    simple dan terdapat reuse command dari history jadi kita tidak perlu
    mengetik kode yang sama berulang ulang. Tetapi syntax nya ternyata cukup
    complex dan complicated seperti C Shell.

* Z Shell 
## Shell Variables
## Lifespan of Shell Variable
## Special variables
* \$1, \$2, \$3 ...
* \$*
* \$@
* \$#
* \$-
* \$\$
* \$_
* \$IFS
* \$?
* \$!
* \$0
