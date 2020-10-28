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

    atau ZSH. Yaitu shell yang terbilang sangat powerful. ketika suatu shell
    tidak bisa melakukan sesuatu, maka ZSH kemungkinan besar dapat melakukannya.
    ZSH ini juga memiliki komunitas yang cukup luas, para komunitas juga
    mengembangkan versi fancy dari ZSH yaitu
    [ohmyzsh/oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh), disana plugin yang
    diberikan jauh lebih banyak dibanding `oh-my-bash` tadi, ini membuktikan
    bahwa komunitas nya juga lebih besar dibanding bash. Kerugian memakai shell
    ini adalah tidak semua system memakai ZSH jadi untuk migrasi akan lebih
    susah dibanding memakai BASH atau SH.

## Shell Variable

Seperti pada variable pada bahasa pemrograman, shell variable juga bisa dibuat
misalnya `foo=bar` maka variable `foo` bernilai string `"bar"`, juga dapat
dipanggil dengan menggunakan $ misal `echo $foo` maka outputnya adalah `bar`,
juga dapat di delete dengan cara `foo=` atau menggunakan `unset foo`.

## Lifespan of Shell Variable

Variable pada shell memiliki waktu terbatas sebelum variable itu hilang. Lamanya
waktu suatu variable adalah sampai shell dimana dia dibuat itu mati.

## Special variables
* \$1, \$2, \$3 ...

    Adalah variable yang memiliki reference ke positional argumen ketika suatu
    program dijalankan, misal terdapat script simple `coba.sh`:
    ```bash
    #!/bin/bash
    echo -e $2;
    echo -e $3;
    echo -e $1;
    ```
    maka ketika dijalankan `./coba.sh arg1 arg2 arg3` akan menghasilkan output:
    ```
    arg2
    arg3
    arg1
    ```

* \$*

    Variable yang menyimpan secara lengkap string dari seluruh positional
    argumen pada suatu program mencakup dari argumen pertama atau `$1` sampai
    argumen ke N. Misal terdapat script simple `coba.sh`:
    ```bash
    #!/bin/bash
    echo $*;
    ```
    maka ketika dijalankan `./coba.sh arg1 arg2 arg3` akan menghasilkan output
    ```
    arg2 arg3 arg1
    ```

* \$@

    Variable yang menyimpan secara lengkap array of string dari seluruh
    posiitonal argument pada suatu program mencakup dari argumen pertama atau
    `$1` sampai argumen ke N. Misal terdapat script simple `coba.sh`:
    ```bash
    #!/bin/bash
    echo $*;
    ```
    maka ketika dijalankan `./coba.sh arg1 arg2 arg3` akan menghasilkan output
    ```
    arg2 arg3 arg1
    ```
    Secara representasi String nya, ini sama dengan \$*,
    tetapi akan berguna pada for loop.

* \$#

    Variable yang menyimpan banyaknya positional argumen atau parameter dalam
    desimal dari variable positional argumen ke 1 `$1` sampai ke N. Misal
    terdapat script simple `coba.sh`:
    ```bash
    #!/bin/bash
    echo $#;
    ```
    maka ketika dijalankan `./coba.sh arg1 arg2 arg3` akan menghasilkan output
    ```
    3
    ```

* \$-

    Atau variable *hypen*, yaitu variable yang menyimpan option pada shell yang
    sekrang sedang dipakai contoh output dari:
    ```bash
    echo $-
    ```
    adalah
    ```
    himBH
    ```
    dimana:
    - h adalah `hashall`
    - i adalah `interactive`
    - m adalah `monitor`
    - B adalah `Braceexpand`
    - H adlaah `histexpand`

* \$\$

    Adalah variable yang menyimpan PID yang menjalankan shell tersebut. Contoh,
    terdapat file script `coba.sh`:
    ```bash
    #!/bin/bash
    echo $$;
    ```
    Ketika dijalankan `./coba.sh` maka contoh outputnya akan:
    ```
    11429
    ```

* \$_
* \$IFS
* \$?
* \$!
* \$0
