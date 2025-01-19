# Ticket-Booking-System
This system is designed to manage parking spaces, handle vehicle entry/exit, and process payments.
## Class: User
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
## Class: Event
Attribute:
```
eventId: int
location: string
date: date
```
Methods:
```
getEventDetails()
updateAvailability()
```
## Class: Ticket
Attribute:
```
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
## Class: Payment
Atribute:
```
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
# Example Code (Python)
```
from datetime import date

class User:
    def __init__(self, user_id, email, name):
        self.user_id = user_id
        self.email = email
        self.name = name

    def search_event(self):
        # Logic to search for events
        return "Searching for events..."

    def book_ticket(self, event_id, price):
        ticket = Ticket(user_id=self.user_id, ticket_id=Ticket.generate_ticket_id(), event_id=event_id, price=price)
        return ticket

    def cancel_ticket(self, ticket_id):
        # Logic to cancel a ticket
        return f"Ticket {ticket_id} cancelled."


class Event:
    def __init__(self, event_id, location, date):
        self.event_id = event_id
        self.location = location
        self.date = date
        self.available_tickets = 100  # Example initial availability

    def get_event_details(self):
        return f"Event ID: {self.event_id}, Location: {self.location}, Date: {self.date}"

    def update_availability(self, tickets_sold):
        self.available_tickets -= tickets_sold
        return self.available_tickets

class Ticket:
    _ticket_counter = 0

    @staticmethod
    def generate_ticket_id():
        Ticket._ticket_counter += 1
        return Ticket._ticket_counter

    def __init__(self, user_id, ticket_id, event_id, price):
        self.user_id = user_id
        self.ticket_id = ticket_id
        self.event_id = event_id
        self.price = price
        self.status = "Confirmed"

    def generate_ticket(self):
        return (f"Ticket ID: {self.ticket_id}\n"
                f"Event ID: {self.event_id}\n"
                f"User ID: {self.user_id}\n"
                f"Price: #{self.price:.2f}\n"
                f"Status: {self.status}")

    def update_status(self, new_status):
        self.status = new_status
        return self.status


class Payment:
    def __init__(self, pay_id, ticket_id, amount, pay_status, pay_day):
        self.pay_id = pay_id
        self.ticket_id = ticket_id
        self.amount = amount
        self.pay_status = pay_status
        self.pay_day = pay_day

    def process_payment(self):
        # Logic to process the payment
        self.pay_status = "Successful"
        return f"Payment of #{self.amount:.2f} processed successfully on {self.pay_day}."


# Example Usage
if __name__ == "__main__":
    # Create a User
    user = User(user_id=1, email="Macdonaldweb3.com", name="Macdonald")

    # Create an Event
    event = Event(event_id=101, location="Learnable 2024", date=date(2025, 5, 20))
    print(event.get_event_details())

    # User books a ticket
    ticket = user.book_ticket(event_id=101, price=1500.0)
    print(ticket.generate_ticket())

    # Update event availability
    event.update_availability(tickets_sold=1)
    print(f"Available Tickets: {event.available_tickets}")

    # Process Payment
    payment = Payment(pay_id=1, ticket_id=ticket.ticket_id, amount=ticket.price, pay_status="Pending", pay_day=date.today())
    print(payment.process_payment())

    # Cancel Ticket
    print(user.cancel_ticket(ticket_id=ticket.ticket_id))

```
