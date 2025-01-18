# Ticket-Booking-System
This system is designed to manage parking spaces, handle vehicle entry/exit, and process payments.
##Class: User
Attribute: 
```
userId: int
email: string
name: string
```
Methods:
```
searchEvent()
bookTicket()
cancelTicket()
```
##Class: Event
```
Attribute:
eventId: int
location: string
date: date
```
Methods:
```
getEventDetails()
updateAvailability()
```
##Class: Ticket
```
Attribute:
userId: int
ticketId: int 
eventId: int
price: double
```
Methods:
```
generateTicket()
updateStatus()
```
##Class: Payment
```
Atribute
payId: int
ticketId: int
amount: double
payStatus: string
payDay: Date
```
Methods:
```
processPayment()
```
