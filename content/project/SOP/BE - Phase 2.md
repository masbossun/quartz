Di phase 2 ini saat dimulai diharapkan sudah selesai dengan phase satu yang meliputi
- Order bertanggung jawab pada dirinya sendiri
- Mapping fungsi before/after save

Pada saat ini pengerjaan SOP baru dimulai, jadi mulai diperhatikan skenario-skenario yang akan dicover. Sesuai rekomendasi saya yang sebaiknya dibuat misal `class OrderManagement()` Maka object inilah yang akan jadi pintu masuk kepada segala skenarion order. Pada phase 2 ini yang akan difokuskan kepada skema closed subscription, kenapa dipilih skema yang ini dulu:
- Order hanya sekali buat sehingga kita bisa ignore beberapa hal terkait update yang akan berefek kepada perubahan skema pembayaran invoice
- Closed subscription akan mengcover baik yang upfront dan juga monthly commitment
- Order ini juga akan mulai meliputi untuk legacy maupun rukita tenant
Pada pembuatn closed subscription masih berfokus hanya kepada order belum kepada tambahan seperti diskon dan lainnya

(estimasi pengerjaan 2-3 hari kerja)

Ketika Closed Subscription sudah dikerjakan, maka saat mengejakan open subscription bisa reuse closed subscription yang monthly commitment, bedanya open tidak memiliki checkout date yang pasti sehingga order akan recurring selama order masih berjalan

Saat proses creation validasi dan lainnya seharusnya sama.

(estimasi pengerjaan 1 hari kerja)

## Shortstay:

Definisi shortstay adalah order yang memiliki periode tinggal kurang dari 30 hari, setiap periode dibagi ke dalam tier
	- tier satu 1-6 hari: penghitungan prorate +100%
	- tier dua  7-13 hari: penghitungan prorate +70%
	- tier tiga 14-20 hari: penghitungan prorate +50%
	- tier empat 21 hari: penghitungan prorate +25%
	- tier 5 lebih dari 21 hari: penghitungan prorate + 0%

Rumus: (100% + tier_percent ) X daily rate X total days
contoh: Daily rate: 100.000,
```
tier 1: (100%+100%) X 100.000 X 6
tier 2: (100%+70%) X 100.000 X 13
...
```
(estimase 1-2 hari kerja )
## Extend

Before

Untuk before extend sudah dipastikan extend berupa closed, contoh:

"Aries" memiliki fix order Tanggal 1 Januari efektif check in. Maka, "Aries" bisa extend lebih awal (early checkin) dengan kondisi:
- jika room yang dipilih tidak ada order bisa dipilih kapan saja namun dengan checkout H-1 dari efektif checkin
- jika room memiliki order sebelumnya, checkin H+1 dari checkout order dengan aturan checkout yang sama
After

Extend after bisa dilakukan setelah checkout terkonfirmasi:
	 - Extend walau kurang dari 21 hari tidak akan terhitung sebagai shortstay
	 - Extend tidak bisa pindah
	 - Checkoutnya depend kepada order selanjutnya

T

