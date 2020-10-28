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
* Korn Shell
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
