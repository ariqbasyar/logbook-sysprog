# Make, Stdio, and Buffering

## Make
Digunakan untuk membantu konfigurasi dan kompilasi terhadap suatu source code
jika developer memiliki kustomisasi kompilasi sendiri. **Makefile** merupakan
file yang akan dibaca oleh command `make` dimana disaa terdapat konfigurasi dari
kompilasi suatu runtutan file. Beberap option dapat diberikan seperti variable
untuk target group of dependencies, target tersebut diikuti oleh command sesuai
dengan tepat dibawahnya. Contoh:

```makefile
main.o: main.c defs.h
    cc -c main.c
```

Disana, `main.o` adalah target command dimana didefinisikan menggunakan
**main.c** dan memiliki dependensi ke **defs.h**. Terdapat beberapa konfigurasi
kompleks lagi seperti:

```makefile
FILES = Makefile defs.h main.c routines.c
OBJS = main.o routines.o
LIBES = -lm
CFLAGS = -g
LP = /fac/matthews/bin/p2c
INSTALL_DIR = /fac/matthews/bin

prog: main.o routines.o
    $(CC) $(CFLAGS) $(OBJS) $(LIBS) -o
prog

$(OBJS): defs.h

cleanup:
    -rm *.o
    -du

install: prog
    mv prog $(INSTALL_DIR)

print: $(FILES)
    pr $? > /tmp/manto
    $(LP) /tmp/manton
    touch print
    -rm /tmp/manton
```

Beberapa option sudah disediakan disana, user dapat langsung melakukan
`make clean` dengan didefinisikan `rm *.o` yaitu menghapus seluruh file dengan
extension ".o". Lalu ada `make install` dimana akan menjalankan command `prog`
dan melakukan kompilasi, jalannya command ini juga bergantung apakah source code
yang bersangkutan ada perubahan dan jika tidak ada maka tidak akan dilakukan
kompilasi ulang.
