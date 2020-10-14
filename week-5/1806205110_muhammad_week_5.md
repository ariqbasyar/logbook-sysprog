# Memory
## Locality of reference
jadi sebenarnya pada pertanyaan di pretest adalah perbedaan temporal dan spatial
locality yang mana setelah saya cari tau ternyata ada 4 tipe (dengan sumber
yang saya gunakan adalah dari
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
