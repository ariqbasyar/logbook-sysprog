# Memory
Terdapat dua tipe memory yaitu **physical** dan **virtual** dengan physical
memory berarti adalah RAM dan virtual memory adalah tempat penyimpanan yang
bersifat secondary misalnya ssd atau hdd.

Dikarenakan physical memory atau RAM itu sangat mahal dan juga aplikasi jaman
sekarang semakin besar resource yang dibutuhkan dan juga banyak sekali
background process yang berjalan yang juga pastinya membutuhkan resource, maka
diperlukannya penggunaan virtual memory untuk penyimpanan cadangan. Jadi kernel
akan menyimpan beberapa data di physical memory sebagai caching dengan algoritma
dinamakan locality of reference.

## Locality of reference
Dengan adanya cara ini jadi tidak semua data yang dibutuhkan suatu aplikasi
atau process akan disimpan ke RAM. dan sebenarnya pada pertanyaan di pretest
adalah perbedaan temporal dan spatial locality yang mana setelah saya cari tau
ternyata ada 4 tipe (dengan sumber yang saya gunakan adalah dari
[Wikipedia](https://en.wikipedia.org/wiki/Locality_of_reference#Types_of_locality))
oke sekarang saya akan menjelaskannya dengan sepemahaman saya:

* Temporal locality

    Jika sebuah address diakses maka ada kemungkinan address tersebut akan
    diakses kembali. Contoh penerapan ini adalah pada variable, ketika sebuah
    variable diakses maka ada kemungkinan kalau variable tersebut akan diakses
    kembali.

* Spatial locality

    Jika suatu address diakses maka ada kemungkinan suatu wilayah dari address
    tersebut juga akan diakses. Contohnya dalam mengakses sebuah index dari
    suatu list maka ada kemungkinan index yang lainnya kana diakses juga.

* Branch locality

    Suatu prediksi pada branching agar ketika branching itu terjadi maka
    data yang ingin diakses sudah siap.

* Equidistant locality

    Suatu prediksi pada pengaksesan address yang memiliki pattern yang linear
    maka dapat diprediksi address selanjutnya.

Setelah membahas bagaimana penyimpanan ke physical memory, sekarang saya juga
harus melihat keuntungan dan kerugian dari penggunaan virtual memory ini.

## Advantage and disadvantage using **virtual memory**
* Advantages
    - Setiap process terisolasi dari process lainnya dalam hal memory atau
    dengan kata lain suatu process tidak bisa mengotak atik memory milik process
    lain.
    - Tidak perlu memiliki RAM yang besar karena kernel dapat mengatur agar
    menggunakan virtual memory di storage seperti ssd atau hdd.
    - Cara untuk dua atau lebih process yang ingin saling sharing memory akan
    lebih baik karena memiliki prinsip isolated jadi cukup berikan privilege
    suatu process untuk mengakses virtual memory process lain.

* Disadvantages
    - Semakin besarnya ketergantungan process ke virtual memory maka akan
    semakin lambat juga process tersebut
    - Selain lambat di process itu, juga akan lambat jika kita berganti aplikasi
    misal dari google chrome ke vscode.
    - Secondary storage jadi tidak bisa dipakai 100% karena sebagian harus
    menjadi tempat untuk virtual memory

## Memory leaks
Suatu failure ketika ingin melakukan alokasi memori, biasanya penyebabnya
adalah:
* Tidak melakukan dealokasi memory pada akhir program.
* Alokasi memory melebihi batas heap.
* Thread mati secara tiba - tiba tanpa cleanup.

## setjmp && longjmp
wih ternyata seru juga percobaan menggunakan setjmp dan longjmp
* int setjmp(jmp_buf env);

    adalah sebuah fungsi dimana fungsi itu akan menyimpan address sekarang ke
    sebuah buffer yang nantinya akan digunakan untuk "loncat" kembali
    menggunakan longjmp. Fungsi ini memiliki reutrn sebuah int dimana bila
    pertama kali dipanggil akan return 0 dan return value selanjutnya akan
    di set oleh value dari fungsi longjmp.

* void longjmp(jmp_buf env, int val);

    adalah sebuah fungsi yang berfungsi untuk melakukan 'loncat' ke dimana
    address dari env berada (address ini di set ketika setjmp(env) dipanggil).
    Fungsi ini memiliki parameter int val yaitu parameter yang akan menggantikan
    nilai return value dari setjmp(env) ketika fungsi longjmp ini dipanggil.
    Ada kasus dimana kalau longjmp mendapat parameter 0 maka dia akan
    memberikan nilai 1.

## abusing longjmp
longjmp ini tidak bisa asal pakai, ada beberapa kondisi dia tidak dapat lagi
digunakan, salah satu contohnya adalah ketika fungsi yang mengatur address env
atau pemanggilan setjmp(env) ini sudah melakukan return maka longjmp tidak boleh
melakukan "loncatan" ke sana, ketika state suatu fungsi sudah returned atau
address di stack tidak lagi menyimpan return address dari fungsi tersebut maka
ketika ada longjmp yang loncat ke fungsi tersebut akan berakibat return address
nya tidak lagi valid, dapat menyebabkan *segmentation fault*.
