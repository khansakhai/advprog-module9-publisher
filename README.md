# Module 9 Tutorial: Software Architecture

Advanced Programming (Even Semester 2024/2025) Tutorial Module 9

Khansa Khairunisa - 2306152462

## Reflection

>1. How much data your publisher program will send to the message broker in one run?

Program publisher akan mengirimkan **lima buah pesan** ke message broker (RabbitMQ) dalam satu kali dijalankan. Masing-masing pesan berisi informasi berupa `user_id` dan `user_name`, yang dikemas dalam bentuk struct `UserCreatedEventMessage`. Jadi total data yang dikirim adalah sebanyak 5 message ke queue bernama `user_created`.

>2. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?

URL `amqp://guest:guest@localhost:5672` adalah alamat koneksi ke RabbitMQ. Kata pertama guest adalah username, kata kedua guest adalah password, localhost berarti broker dijalankan di komputer lokal, dan 5672 adalah port default untuk protokol AMQP. Karena subscriber dan publisher menggunakan URL yang sama, artinya mereka berkomunikasi lewat broker RabbitMQ yang sama di mesin lokal, dengan kredensial yang sama.

- **Running RabbitMQ**

Berikut adalah tampilan saat RabbitMQ berhasil dijalankan.

![Running RabbitMQ](images/RabbitMQ_Running.png)

- **Sending and Processing Event**

Gambar berikut menunjukkan bahwa setelah program `publisher` dijalankan sebanyak dua kali, program `subscriber` berhasil menerima total 10 event yang dikirim. Hal ini membuktikan bahwa proses pengiriman dan penerimaan pesan melalui RabbitMQ berjalan dengan baik.

![Subscriber Sending Event](images/SendingEvent_Subscriber.png)
![Publisher Sending Event](images/SendingEvent_Publisher.png)

- **Monitoring chart based on publisher**

Grafik pada RabbitMQ menunjukkan lonjakan karena program `publisher` dijalankan beberapa kali dan mengirim pesan ke broker. Lonjakan tersebut mencerminkan aktivitas publish yang berhasil dan terpantau melalui dashboard.

![Monitoring chart based on publisher](images/Monitoring_Chart_Case.png)