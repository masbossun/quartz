Phase 1 new order creattion 

Total: 1 Sprint

Objective:

- cleansing model save
	- save model
	- save admin
	- save form
	- signa()
	- cron()
	- graphql
	- REST
- Prepare new schema
	- define new structure model order
	- after save method
	- model or method related to order
- Prepare schema "migration"
	- Define diferent existing vs new schema
	- how to migrate?

Cleansing

Saat ini order setelah save bertanggung jawab kepada banyak hal, yang paling kelihatan adalah, saat order dibuat setidaknya akan terjadi 3 hal ini secara otomatis
- Membuat model invoice
- Mengubah model room/room variant status
- Mengubah tenant model jika memiliki referall
- dan lainnya yang perlu dicek

Selain mengecek cleansing yang kepada model-model lain yang berubah akibat order tapi harus listing juga fungsi-fungsi yang berdampak kepada order itu sendiri, seperti
- cron mengubah status order
- cront yang generate invoice
- dan lainnya yang perlu dicek

Tujuan utama cleansing ini adalah membersihkan model order kepada tangung jawab selain pada dirinya sendiri, sehingga ketika user membuat order, order hanya akan berdampak kepada model, dia tidak lagi akan
- Membuat model invoice
- Tidak langsung mengubah room/room variant
- Tidak langsung mengubah tenant model jika ada referal
- dan lainnya yang masih perlu dicek

Untuk kondisi yang kedua (listing fungsi di luar order yang memengaruhi order ) hany aperlu dicatat tanpa dibuang, bagaimanapun dalam pengerjaan ini kondisi order yang sudah dibuat sebelumnya masih bisa berjalan dengan baik.

(Untuk bagian ini ekspektasi waktu yang akan dihabiskan minimal 1 hari kerja maksimal 2 hari kerja)

Prepare new schema

Dalam fase ini engineer baru memulai untuk mengaudit field/kolom mana saja yang dipertahankan, "dibuang", atau ditambah. Konteks dibuang di sini lebih menyerupai menyembunyikan, di sini tujuannya untuk memastikan dahulu data lama tidak berubah dan amsih tersimpan di database, walau secara tampilan di web (entah django atau ND) tidak dimunculkan field terkait.

Untuk yang ditambahkan ini yang akan dikerjakan, mulai spesifik field-field baru dengan kebutuhan SOP baru.

Sedangkan yang dipertahankan ada dua kemungkinan:
- dipertahankan apa adanya
- dipertahankan dengan perubahan

Untuk yang dipertahankan dengan perubahan, contohnya adalah mengubah nilai kolom harga dari positive integer menjadi positive float dengan beberapa angka di belakang koma.

Untuk efek setelah order juga mulai dimapping di sini, dikarenakan ini nantinya akan berfokus di ND, rekomendasi adalah dibikin class OrderManagement tersendiri yang nantinya bisa dipanggil di beragam tempat, seperti
- Endpoint CRUD di ND
- Handling di after save admin.py

Untuk poin ketiga yang model lainnya tapi related ke order pada phase ini masih dicatat terlebih dahulu

*Untuk bagian Class OrderManagement() belum melakukan apapun, tapi sudah discafolding*

(Estimasi pengerjaan 3 hari kerja)

Prepare migration

Ketika Order sudah "bersih", struktur baru sudah terbentuk maka step yang perlu dilakukan adalah:
- Menampilkan bagian yang berbeda, dengan pertanyaan
	- apakah field lama ada yang inline dengan field yang baru
	- apakah datanya bisa langsung dipindahkan?
	- apakah datanya harus ditransform terlebih dahulu?

Setelah diketahui jawaban-jawabanya tinggal bagaiaman cara kita migrasinya dan juga mitigasinya
( estimasi 1 sampai 2 hari kerja )

Hasil akhir phase 1 dari Order creation ini

- Order sementara akan bertanggung jawab dengan dirinya sendiri
- Sudah berhasil mapping fungsi after/before save berpengaruh kemana saja
- Sudah disiapkan script untuk migrasi sewaktu-waktu dibutuhkan