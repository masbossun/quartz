# Mobile App SOP Development
Our plan to develop SOP + Online Booking

# Tasks

[Online Booking Requirements](https://rukita.atlassian.net/wiki/spaces/RN/pages/2047508543/Online+booking)

## Enable search “room availability function” at all search/location/collection pages
#### Not Depends To BE
- New: [[Implement Calendar Filters on Building List (UI)]] (3)
- New: [[Create new modal - Select Checkin-out Modal (UI)]] (5)
- Revamp: [[Availability Badge Visibility on Building Card (UI)]] (1)
- Revamp: [[Availability Badge Visibility on Mapview Building Card (UI)]] (1)

#### Dependent to BE
- New: [[Search Buildings Based on Calendar Filter (Query)]] (3)
	- [[Mobile App SOP Development#Filter Buildings Availability]]

## Enable search “room availability function” at building pages
#### Not Depends To BE
- New: [[Implement Calendar Filters Building Detail (UI)]] (3)
	- [[Mobile App SOP Development#Filter Rooms Availability]]
- New: [[Add new parameter Checkin-out date on Building Detail]] (1)
- Revamp: [[Revamp Building Room Card (UI)]] (3)
- New: [[Building Detail Rooms Sorting (UI)]] (3)

## Remove current availability labeling 
- See [[Mobile App SOP Development#Enable search “room availability function” at building pages]]
- See [[Mobile App SOP Development#Enable search “room availability function” at all search location collection pages]]

## Enable user to select the available room

#### Not Depends To BE
- New: [[Building Detail - Select Room For Booking (UI)]] (2)

## Booking Prerequisites logic
#### Not Depends To BE
- New: [[Check pre-requisite rule before booking]] (5)
	- Check login condition
	- Check tenant personal info (Via API or Check manually)
	- Handle resume user journey after login/signup
- New: [[Tenant Personal Info Form (UI)]] (5)

#### Dependent to BE
- New: [[Tenant Personal Info Form (Query + Mutation)]] (5)

## Develop (review)detail order page
#### Not Depends To BE
- New: [[Booking Order Detail or Review (UI)]] (55)

#### Dependent to BE
- Reuse: [[Perform Check Referral (Mutation)]] (2)
	- Use existing referral check mutation
- Reuse: [[Get Vouchers (Query)]] (2)
	- Navigate to Vouchers Screen and Query the Vouchers
- New: [[Order Booking for Review (Query)]] (5)
	- [[Mobile App SOP Development#Params Screen for Review State]]
	- [[Mobile App SOP Development#Invoice Calculation]]
- New: [[Perform Booking (Mutation)]] (5)
	- [[Mobile App SOP Development#Create Booking Order]]

## Recheck room availability 
#### Dependent to BE
- [ ] New: [[Perform check room availability (Mutation)]] (3)
	- Will show modal and prevent to go to next flow
	
## Recheck room price
#### Dependent to BE
- New: [[Perform check room price changes (Mutation)]] (3)
	- Will show snackbar
	- Might prevent to to to next flow

## Develop detail order page
- See [[#Develop review detail order page]]

#### Dependent to BE
- New: [[Order Booking for Detail (Query)]] (5)
	- [[Mobile App SOP Development#Params Screen for Detail State]]

## Enable user to select the payment method
#### Dependent to BE
- New: [[Perform Select Payment VA (Mutation)]] (3)
	- [[Mobile App SOP Development#Select Payment VA]]

## Enable user to pay his order using midtrans with given timeline
- _TBD_

## Enable user to change their payment method
#### Dependent to BE
- New: [[Cancel Payment VA (Mutation)]] (3)
	- [[Mobile App SOP Development#Change Cancel Payment VA]]

## Show user payment status and the action needed from user at each stage

- _TBD_

## Develop function to enable user to get their latest payment status

- See [[Mobile App SOP Development#Develop review detail order page]]

#### Dependent to BE
- New: [[Get Latest Booking Status (API)]] (2)

## Enable user to see and download the invoice PDF
- See [[Mobile App SOP Development#Develop review detail order page]]

## Add more informations at EDIT profile
#### Not Depends To BE
- Revamp: [[Tenant Personal Info at Profile (UI)]] (3)

#### Dependent to BE
- Revamp: [[Get and Update Tenant Personal Info at Profile (Query + Mutation)]] (3)
- ~~Verify Phone Number with OTP (15)~~

## Develop new page “my booking”
#### Not Depends To BE
- New: [[My Booking List (UI)]] (7)

## Change “tagihan” page to “Tagihan sewa”
#### Not Depends To BE
- Revamp: [[Change Tagihan Menu Label]] (1)

## “Riwayat pesanan kost” change it to “Waiting list”
#### Not Depends To BE
- Revamp: [[Change Booking History Menu Label]] (1)
	- Decide to change the menu label
	
## remove “ajukan sewa” button from wishlist
#### Not Depends To BE
- Revamp: [[Remove Card Buttons on Wishlist Card]] (1)


---

[Discount Revamp](https://rukita.atlassian.net/wiki/spaces/RN/pages/2045050891/EPIC-1ST+INVOICE+Show+and+Remove+Discount)

## Show and Remove Discount
#### Dependent to BE
- New: [[Handle new Building List API using REST]] (30)


---

Task not listed on requirements

## Current Recurring Invoice Revamp
#### Dependent to BE
- Revamp: [[Remapping Invoice Detail Statuses]] (5)
	- [?] Need to make sure UI Invoice Detail with new SOP Statuses Mapping
	- The different is only on Expired x Failed payment status
- Revamp: [[Remapping Invoice AddOn Detail Statuses]] (5)
	- [?] Need to make sure UI Invoice Detail with new SOP Statuses Mapping
	- The different is only on Expired x Failed payment status


## Current Voucher Detail Revamp
#### Not Depends To BE
- Revamp: [[Fix use voucher from Voucher Detail behavior]] (3)
	- If using one button, On user use voucher, will either go to Invoice List or My Booking List
	- If using two buttons, On user use voucher, will either choose to go to Invoice List or My Booking List
	- Decide to go to current Recurring Invoice List

## Handling New Notification
#### Dependent to BE
- New: [[Handle notification (Online Booking, First Invoice)]] (2)
- New: [[Handle New Booking Dot Indicator]] (2)


# Additional Info

#### About Check-in Check-out Selection:
- Frontend and Backend will have their own way to work with check-in and check-out date.
- Frontend just need to send the check-in and check-out date to backend, regardless how frontend draw the UI to user.
- Frontend will have some shortcut to produce a check-out, user need to select the check-in date first, then select how many days (30, 60, 90, or choose the date manually dst)

#### Filter Buildings Availability:
- **Payload**
	- Check-in Date
	- Check-out Date
- **Response**
	- Dynamic Value of Availability
	
#### Filter Rooms Availability:
- **Payload**
	- Check-in Date
	- Check-out Date
- **Response**
	- Array of BuildingType
	- Dynamic Value of Availability

#### Params Screen for Review State:
- type: "REVIEW"
- Check-in Date + Time
- Check-out Date
- Building Data (There is a lot of data to send through, maybe we just need the IDs and query to the backend)
  - Building Slug
  - Room ID (Not sure if we have endpoint for this?)
  - Room Price (To query order price breakdown)

#### Params Screen for Detail State:
- type: "DETAIL"
- Order ID (Maybe we only need Invoice ID)
- Invoice ID

#### Invoice Calculation:
- **Payload**
	- Check-in Date
	- Check-out Date
	- Building Id
	- Room Id
	- Voucher Id(s)
	- Referral Code
- **Response**
	- Price Breakdown
		- [?] Structures

#### Create Booking Order
- **Payload**
	- Check-in Date
	- Check-out Date
	- Building Id
	- Room Id
	- Current availability
	- Price
	- Voucher Id(s) - If Applied
	- Referral Code - If Applied and Code Valid
- **Response**
	- Message
	- Code
		- Voucher Issues
		- Referral Issues
		- TBD
	- Midtrans Token

#### Select Payment VA
- **Payload**
	- TBD
- **Response**
	- TBD

#### Change/Cancel Payment VA
- **Payload**
	- TBD
- **Response**
	- TBD
	

# Storypoints
```
approx_sp:: 191
```

## VPD 5
```
vpd:: 5
devs:: 3
development_days:: 8
cap_each_sprint:: 120 (vpd * devs * development_days)

sprints:: 5
cap:: 600 (cap_each_sprint * sprints)

total_sprints_required:: 1.59 (approx_sp / cap_each_sprint)
```

## VPD 4
```
vpd:: 4
devs:: 3
development_days:: 8
cap_each_sprint:: 96 (vpd * devs * development_days)

sprints:: 5
cap:: 480 (cap_each_sprint * sprints)

total_sprints_required:: 1.98 (approx_sp / cap_each_sprint)
```

## VPD 3
```
vpd:: 3
devs:: 3
development_days:: 8
cap_each_sprint:: 72 (vpd * devs * development_days)

sprints:: 5
cap:: 360 (cap_each_sprint * sprints)

total_sprints_required:: 2.65 (approx_sp / cap_each_sprint)
```

## VPD 2
```
vpd:: 2
devs:: 3
development_days:: 8
cap_each_sprint:: 48 (vpd * devs * development_days)

sprints:: 5
cap:: 240 (cap_each_sprint * sprints)

total_sprints_required:: 3.97 (approx_sp / cap_each_sprint)
```

## VPD 1
```
vpd:: 1
devs:: 3
development_days:: 8
cap_each_sprint:: 24 (vpd * devs * development_days)

sprints:: 5
cap:: 120 (cap_each_sprint * sprints)
total_sprints_required:: 7.9 (approx_sp / cap_each_sprint)
```

# TODO
- [x] Explore Calendar Component
- [x] Explore Downloadable PDF
- [x] Sync with [[Aries]] about payload and response
	- [x] Building Listing Check-in Check-out Filter
	- [x] Room Listing Check-in Check-out Filter
	- [x] Invoice Price Breakdown
		- [x] Building Price, Discount, Promo 
		- [x] Voucher and Referral
	- [x] Create Booking Order
	- [x] Select Payment VA
	- [x] Change/Cancel Payment VA
- [-] Read and Plan about Tenant Phone Number Verification
- [/] Update timeline
- [ ] Make sure Building Query to BE
- [ ] Make sure Room Availability Query to BE
	- Existing room data is tight to Building Detail Query
- [ ] Make sure `isTenant` condition
- [ ] Make sure UI current invoice detail status to [[Ling]]
	- [x] Mapping Statuses
	- [ ] [[Ryan]] Check current mapping with new status at https://docs.google.com/spreadsheets/d/1lb9K039YcjFLtV3wTPpy6A0RUquIKW_Y9H8wZsn-r2Q/edit#gid=998714156
- [ ] Sync with aries about response and payload expectation to set a timeline
	- [ ] For [[Handle new Building List API using REST]]


# References
- [Flowchart - Miro](https://miro.com/app/board/uXjVOyP5eNI=/?moveToWidget=3458764530915457372&cot=14)
- [The big plan - Figjam](https://www.figma.com/file/VTqo97vMpUwJuFgGVNOVXu/SOP)
- [Order Scenario - Spreadsheets](https://docs.google.com/spreadsheets/d/1tHNTnCrc4E1g4uLl9p8DKgFWBqKwCVXqbi0nCr4Flcc/edit#gid=534091822)
- [Online Booking Requirements - Wiki](https://rukita.atlassian.net/wiki/spaces/RN/pages/2047508543/Online+booking)
- [First Invoice Requirements - Wiki](https://rukita.atlassian.net/wiki/spaces/RN/pages/1981841409/EPIC+-+Enable+1st+Payment+UIUX+Enable+First+Payment+to+Be+Paid+Using+Midtrans)
- [Order/Invoice/Payment Status Mapping - Spreadsheets](https://docs.google.com/spreadsheets/d/1lb9K039YcjFLtV3wTPpy6A0RUquIKW_Y9H8wZsn-r2Q/edit#gid=998714156)
- [(Deprecapted) Timeline - Spreadsheets](https://docs.google.com/spreadsheets/d/1ARZOUyf01BmpLZC5hobokjW7p4AQxMPRrEg5ymIWuOs/edit#gid=717484225)
- [Remove availability badge (hifi)](https://www.figma.com/file/c9zG11MpcTO7hyr3YgYX9Z/MASTER---Explore?node-id=3635%3A234385)
- [Filter checkin-out di building list (hifi)](https://www.figma.com/file/c9zG11MpcTO7hyr3YgYX9Z/MASTER---Explore?node-id=3635%3A234392)
- [Building details UX (lofi)](https://miro.com/app/board/uXjVOyP5eNI=/?moveToWidget=3458764531334127431&cot=14)
- [Order Detail (Lofi)](https://miro.com/app/board/uXjVOyP5eNI=/?moveToWidget=3458764531257154061&cot=14)

# Backlinks
- [[New Plan - Online Booking with Existing Condition]]
- [[2022-08-12 - Online Booking Flow Sync]]
- [[Personal Recap]]