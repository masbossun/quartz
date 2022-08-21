# Booking Order Detail or Review (UI)

Storypoints:: 55


### Create Booking Detail Screen (UI)
Storypoints:: 1

- Create component screen container
- Assign to MainStack

### Booking Steps Panel (UI)
Storypoints:: 2

- Develop Booking Steps Panel

### Booking Steps Detail Bottomsheet (UI)
Storypoints:: 2

- Develop Booking Steps Detail Bottomsheet

### Booking Status Panel (UI)
Storypoints:: 3

- Render information based on statuses (Order, Invoice, Payment)
- Have button to check the booking status on certain condition

### Check-in Guidelines Panel (UI)
Storypoints:: 1

- Create panel for Check-in Guidelines

### Check-in Guidelines Bottomsheet (UI)
Storypoints:: 2

- Create bottomsheet for Check-in Guidelines

### Invoice Info
Storypoints:: 2

- Create panel for Invoice Information
- Have button to open the PDF Viewer (Downloadable) on certain condition

### Downloadable Invoice PDF (UI)
Storypoints:: 3

- Use https://rukita.atlassian.net/wiki/spaces/RN/pages/2055602261/About+PDF+Viewer
- Create PDFViewer Screen
- Accepts params
	- URL
	- Title (for toolbar title)

### Building Info Panel (UI)
Storypoints:: 2

- Create panel for Building Info (1)

### Create Bottomsheet for Building Info (UI)
Storypoints:: 3

- Create bottomsheet for Building Info


### Check-in Check-out Info Panel (UI)
Storypoints:: 5

- Create panel to show Checkin-out information
- Have check-in time field and can be edited by timepicker

### Tenant Personal Info Panel (UI)
Storypoints:: 1

- Create panel to show tenant personal information

### Tenant Personal Info Detail Bottomsheet (UI)
Storypoints:: 5

- Create bottomsheet to show Tenant Personal Info Detail


### Input Voucher Panel (UI)
Storypoints:: 3

- Create panel to show voucher
- Have state
	- Applied Voucher
	- Unapplied Voucher
- Have button to navigate to Select Voucher (Existing Screen)

### Revamp Voucher Screen (UI)
Storypoints:: 3

- Handle Voucher Sections
	- "Pilih Voucher"
	- "Voucher belum bisa dipakai"
- Add new state for Voucher Card - "Voucher Kadaluarsa"

### Input Referral Panel (UI)
Storypoints:: 2

- Create panel to show referral code
- Have state
	- Applied Referral Code
	- Unapplied Referral Code
- Have button to open [[#Input Referral Bottomsheet UI]]

### Input Referral Bottomsheet (UI)
Storypoints:: 3

- Create bottomsheet to input Referral Code

### Price Detail Panel (UI)
Storypoints:: 3

- Create panel to show Price details/breakdown
- Some field might have modal for detailed information

### Price Detail Bottomsheet (UI)
Storypoints:: 5

- Create bottomsheet for Price Detail/Breakdown

### Payment Method Selection Panel (UI)
Storypoints:: 2

- Create panel to select Payment Method.
- Not selectable if payment method already locked.
- If no payment method locked, on Press navigate to existing payment method selection screen.

### Policies Panel (UI)
Storypoints:: 1

- Crate panel to show policies menu
- Each policies menu have their own detailed modal/bottomsheet

### Policies Bottomsheet (UI)
Storypoints:: 3

- Create Bottomsheet for "Kebijakan Pembatalan"
- Create Bottomsheet for "Kebijakan Pengembalian Dana"
- Create Bottomsheet for "Kebijakan Split Invoice"

### Help/FAQ Panel (UI)
Storypoints:: 1

- Create panel/section to show "Help" information
- Have button/link to FAQ

### Footer Component (UI)
Storypoints:: 3

- Have CTA Button (label and function can be changed based on current booking status)
- Have Grandtotal Information