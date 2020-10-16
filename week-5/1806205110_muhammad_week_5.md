# Memory
Terdapat dua tipe memory yaitu **physical** dan **virtual** dengan physical
memory berarti adalah RAM dan virtual memory adalah tempat penyimpanan yang
bersifat secondary misalnya ssd atau hdd.

Dikarenakan physical memory atau RAM itu sangat mahal dan juga aplikasi jaman
sekarang semakin besar resource yang dibutuhkan dan juga banyak sekali
background process yang berjalan yang juga pastinya membutuhkan resource, maka
diperlukannya penggunaan physical memory untuk penyimpanan cadangan. Jadi kernel
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
