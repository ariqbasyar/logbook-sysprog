# Process
adalah sebuah program yang sedang berjalan atau *active*. Biasanya program terdiri
dari banyak *process*

Contoh:
- *Cronjob*
- *Broadcast Receiver*
- *Process* yang menunjukkan *time*

## PID
Sebuah nomor unik yang diberikan ke setiap *process* yang berjalan di sistem
Unix sebagai id dari *process* tersebut

### Maximum PID Number
Pada sistem Unix 32bit terdapat batasan banyaknya process yang dapat berjalan
di *system* tersebut atau bisa dikatakan *maximum* nilai dari PID yaitu tersimpan
di dalam *file* **/proc/sys/kernel/pid_max** atau dapat menggunakan bantuan
command
```shell
sysctl kernel.pid_max
```

![pid_max_png](/images/pid_max.png)

Pada sistem 64bit, nilai ini bisa diperbesar lagi sampai 2<sup>22</sup> atau
sekitar 4 juta dengan cara write **4194304** ke file **/proc/sys/kernel/pid_max**
