# Process
adalah sebuah program yang sedang berjalan atau *active*. Biasanya program
terdiri dari banyak *process*

Contoh:
- *Cronjob*
- *Broadcast Receiver*
- *Process* yang menunjukkan *time*

## PID
Sebuah nomor unik yang diberikan ke setiap *process* yang berjalan di sistem
Unix sebagai id dari *process* tersebut

### Maximum PID Number
Pada sistem Unix 32bit terdapat batasan banyaknya process yang dapat berjalan
di *system* tersebut atau bisa dikatakan *maximum* nilai dari PID yaitu 
tersimpan di dalam *file* **/proc/sys/kernel/pid_max** atau dapat menggunakan
bantuan
command
```shell
sysctl kernel.pid_max
```

![pid_max_png](/images/pid_max.png)

Pada sistem 64bit, nilai ini bisa diperbesar lagi sampai 2<sup>22</sup> atau
sekitar 4 juta dengan cara write **4194304** ke file **/proc/sys/kernel/pid_max**

### When a process has a PID exceeding the maximum limit (pid_max)
Dari sebuah *file* [**pid.c**](https://github.com/torvalds/linux/blob/master/kernel/pid.c) 
yang bertugas untuk mengontrol pid yang diberikan
ke suatu *process* dengan cara menambahkan pid terakhir dengan 1, nah tapi
kalau nilainya melebihi nilai maksimal maka akan diubah menjadi bernilai 300
yaitu sebuah *variable* konstanta yang sudah di *define* di 
[sini](https://github.com/torvalds/linux/blob/c85fb28b6f999db9928b841f63f1beeb3074eeca/kernel/pid.c#L63).

Lalu mengapa tidak dikembalikan ke 0? karena PID - PID yang cukup kecil yaitu
dalam rentang 0 sampai 300 adalah PID yang dikhususkan untuk kernel, maka ketika
sebuah process melebihi nilai maksimal (pid_max) akan di-cycle PID nya menjadi
300 bukan 0.

## PS
Salah satu command untuk membantu user dalam manage process dan thread di suatu
sistem.

### Options
Terdapat beberapa option yang dapat membantu user dalam manage process dan
thread di sistemnya

```shell
ps aux
```
Sebuah option **aux** atau menggunakan BSD syntax biasa dipakai ketika ingin
melihat semua process dari sistem tersebut. Ini akan membantu user ketika ingin
membunuh suatu process misal ada process di background yang ingin dibunuhnya
maka cukup kirimkan sinyal kematian pada pid yang bersangkutan.

![ps-aux-png](/images/ps-aux.png)

```shell
ps axjf
```
Option axjf adalah option yang akan mencetak keluaran dari seluruh process dalam
bentuk tree yang mana dapat memudahkan user untuk melacak langsung parent
process dari process yang dia lihat. Misal ingin membunuh suatu zombie process
yang mana kita ingin melihat parent yang paling tepat untuk dibunuh maka option
ini akan sangat membantu dalam membunuh parent process untuk membunuh semua
child process nya.

![ps-axjf](/images/ps-axjf.png)

```shell
ps -U
```
Option -U adalah untuk filter process yang berjalan di suatu sistem yaitu
process - process yang bersangkutan dengan user tersebut. Tentunya hal ini akan
sangat membantu user misal sysadmin yang bertugas untuk menjaga server nya, maka
dia dapat melihat apa yang sedang dilakukan suatu user, apakah ada yang
mencurigakan dan sebagainya, dan sysadmin cukup kill teletype dari user tersebut
untuk menghindari hal - hal yang tidak diinginkan.

![ps-u](/images/ps-u.png)
