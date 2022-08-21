# Subscription Type
Ada beberapa tipe _subscription_

### 1. Open Subscription
Tipe subscription terbuka, artinya tanpa tanggal _checkout_ yang pasti. Invoice akan ditagihkan dan dibayar setiap bulannya sampai tenant menentukan tanggal untuk _checkout_.

### 2. Closed Subscription
Tipe subscription tertutup, artinya tenant sudah memastikan kapan dia akan _checkout_ (end date).

Ada beberapa bentuk pembayaran untuk Closed Subscription, yaitu _Upfront_ dan _Monthly Commitment_.

Pembayaran _Upfront_ artinya tenant membayar sepenuhnya biaya sewa diawal.

Pembayaran _Monthly Commitment_ artinya tenant membayar tagihannya secara bulanan, namun dengan komitmen untuk _stay_ selama x bulan. Tanggal _checkout_ tidak terikat dengan nilai _Monthly Commitment_ ini.


# Order
### 1. New Order
Order yang tidak berkaitan dengan tenant dan atau order sebelum atau sesudahnya.

> [!Additional Info]-
> - Gap antar order di building dan room yang sama minimal 2 hari

### 2. Extend Order
Order dengan tenant, room, dan building yang sama seperti sebelum atau sesudahnya. Order harus saling menempel satu sama lain.

> [!Additional Info]-
> - Date Gap : 1 hari (check in date h+1)
> - room sama
> - tenant sama  
> - extend dengan perhitungan short stay hanya mungkin jika order sebelum atau setelahnya adalah short stay  
> - jika order sebelumnya monthly maka tidak bisa short stay

Ada dua type Extend Order

##### 1. Before upcoming order
Artinya tenant melakukan extend di tanggal sebelum order yang sudah ia miliki.

- Extend before hanya untuk closed subscription upfront 
- harus sudah confirm checkout
- checkout tenant h-1 dari checkin date sebelumnya (resched early check-in)
	
##### 2. After ongoing order
Artinya tenant melakukan extend di tanggal sesudah order yang sedang berjalan.

- h+1 checkout

### 3. Transfer Room
Order dengan tenant yang sama, dengan beda room. Disediakan untuk memenuhi kasus tenant ganti kamar.

Untuk kasus berbeda building, tidak akan kita _cover_ dulu di Transfer Room. Bisa menggunakan New Order jika ingin pindah berbeda building.

> [!Additional Info]-
> - Date Gap : 1 hari (h+1 dari checkout date)
> - no deposit
> - tenant sama
> - room sama
> - stay periode sama
> - checkin date = transfer date
> - checkout date = auto ambil dari checkout order sebelumnya

Ada tiga jenis Transfer Room yaitu

- Upgrade
- Same Room Variant
- Downgrade


# Tenant Type
### 1. Legacy Tenant
Penghuni lama sebelum rukita ambil alih buildingnya.

> [!Additional Info]-
> - Join Date (TBC) ?
> - Last paid to tenant  
> - Landlord Price (manual)
> - Tidak bisa menggunakan monthly commitment  
> - Last Payment to Landlord (date)  
> - First Stay in Unit (informational)   
> - Check in Date (>= live/soft live date)  
> - Tanpa Deposit  
> - Status: Waiting --> Deposit Payment Received --> Ongoing  
> - Jika ingin convert ke rukita tenant, maka harus buat order baru  
> - Jika tenant tidak akan lanjut ke rukita dan checkout di masa setelah live dengan rukita, maka c/o date akan = last payment to landlord dan sistem hanya akan generate invoice ke landlord = close sub upfront

### 2. Rukita Tenant
Penghuni building Rukita.

> [!Additional Info]-
> - deposit = manual free text number   
> - first payment bisa upfront, prorate, first full month   
> - bisa split payment   
> - sales bisa memilih apakah bisa split payment jika check in date lebih dari 7 hari   
> - pembayaran pertama 24 jam setelah order dibuat atau check in time = 08:00 am   
> - dan semua pembayaran harus dilunasi h-2   
> - flag for close sub short stay (current hidden)   
> - short stay di hitung dari stay period (Check-in Check-in date)

### 3. Rukita Staff - Paying
_TBD_

### 4. Rukita Staff - Free of Charge
_TBD_

# Discount, Promo and Voucher
Ada tiga jenis pengurangan pembayaran yaitu Discount, Promo dan Voucher.

Discount dan Promo memiliki _behavior_ yang mirip sedangkan voucher cukup berbeda dibanding yang lainnya.

> [!Additional Info]-
>  - Budget Allocation
>  - Budget Spent
>    - Budget Spent masih bisa melebihi Budget Allocation
>    - Penambahan Budget Allocation akan dilakukan saat order create
>    - Jika Budget Spent > Budget Allocation, promo/diskon akan hilang atau tidak bisa digunakan.
>    - Penambahan Budget Spent ditambahkan ketika order create.

	
# AddOns
- Pembayaran mengikuti subscription type
- Untuk Close Subscription, harus ada End Date dan tidak boleh lebih dari Checkout Date
- Tidak dapat dipotong oleh Discount, Promo atau Voucher

# Tenant Invoice
Bukti pemesanan room yang perlu dibayar oleh Tenant. Diantaranya terdapat informasi:
- Tenant Data
- Stay Information (Building, Room, Add-ons, Check-in date)
- Payment Status (Deposit & 1st Month Rent)

# The Big Plan
> [!Plan]-
> ![[SOP.png]]

- Status Mixing (Ongoing)
- Order Creation
- Discount, Promo and Voucher
- Add-ons
- Cancellation (Low Priority)
- Early Checkout
- Refund (Low Priority)
- Price Update
- Online Booking (Main Goals: Rukita)
- First Invoice (Main Goals: Product & Tech)
- Internal Dashboard

**N1**: _New Order_ Legacy Tenant Open Subscription
**N2**: _New Order_ Legacy Tenant Close Subscription (Upfront)
**N3**: _New Order_ Rukita Tenant Open Subscription
**N4**: _New Order_ Rukita Tenant Close Subscription (Upfront)
**N5**: _New Order_ Rukita Tenant Close Subscription (Monthly Commitment)

**E1**: _Extend Order_ Before Upcoming Order
**E2**: _Extend Order_ After Upcoming Order

**T1**: _Transfer Order_ Upgrade
**T2**: _Transfer Order_ Same Room Variant
**T3**: _Transfer Order_ Downgrade

