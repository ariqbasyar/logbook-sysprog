# System Call

## Definition
System call adalah sebuah cara bagaimana sebuah application program dapat
berinteraksi hardware, dengan system call memberikan sebuah
API agar dapat berinteraksi dengan hardware pada kernel space.

## Why?
Mengapa kita membutuhkan system call? Agar program kita dapat melakukan task
seperti pada program yang low level contohnya I/O atau berinteraksi dengan
devices, networking, bahkan kita jadi bisa membuat file system sendiri dengan
bantuan API dari system call.

## Example
contoh system call yang sering digunakan:
- [open](https://man7.org/linux/man-pages/man2/open.2.html), untuk membuka
suatu file dengan spesifikasi sebuah pathname
- [read](https://man7.org/linux/man-pages/man2/read.2.html), untuk membaca
suatu file dalam bytes ke sebuah buffer
- [write](https://man7.org/linux/man-pages/man2/write.2.html), untuk menulis
ke suatu file dalam bytes dari suatu buffer
- [close](https://man7.org/linux/man-pages/man2/close.2.html), untuk menutup
sebuah file descriptor agar tidak dipakai lagi dan bisa dipakai untuk
penggunaan yang lain
- [wait](https://man7.org/linux/man-pages/man2/wait.2.html), untuk mengunggu
perubahan state dari child dari suatu pemanggilan process
- [fork](https://man7.org/linux/man-pages/man2/fork.2.html), untuk membuat
[child process](https://en.wikipedia.org/wiki/Child_process) dengan cara
menduplikasi pemanggilan process dari program tersebut
- [exit](https://man7.org/linux/man-pages/man2/exit.2.html), untuk mengakhiri
pemanggilan process secara langsung
- [kill](https://man7.org/linux/man-pages/man2/kill.2.html), untuk mengirim
sinyal 'kematian' ke sebuah process atau process group

# Wrapper function for system call
## The problem
Penggunaan system call tidak bisa semulus yang kita kira, masalah utama
yang perlu diatasi adalah performa. Ya! performa suatu program akan berkurang
karena program harus berpindah dari user mode ke kernel mode untuk bisa
mengeksekusi system call yang dimana perpindahan ini dapat berakibat pada
berkurangnya performa dari suatu program.

## Solution
Bahasa pemrograman high level sekarang sudah memiliki library yang bertugas
untuk menjadi wrapper atau jembatan ketika ingin mengakses system call yang
dimana wrapper function tersebut sudah di utilize agar bisa memanggil system
call dengan programm atau process parent nya tetap berada pada user mode. 
Program cukup menggunakan library untuk pemanggilan system call dan wrapper
function akan meneruskan ke trap handler yang selanjutnya siap melakukan
eksekusi system call di register atau stack pada kernel memory.
