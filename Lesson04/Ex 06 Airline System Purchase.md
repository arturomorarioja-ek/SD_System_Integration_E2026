### Airline system
Expand [the Airline system SOAP API](https://github.com/arturomorarioja/php_soap_airline_system) with the following operations and data types:

- Messages
  - `PurchaseTicket`
    - Request `PurchaseTicketRequest`
      - `pnr` (string). Passenger name record
      - `payment` (PaymentInfo)
      - `billingEmail` (string)
    - Response `PurchaseTicketResponse`
      - `tickets` (array of Ticket) (one per passenger)
      - `booking` (Booking)

- Core data types
  - `PaymentInfo`
    - `method` (PaymentMethod)
    - `card` (PaymentCard, optional)
    - `amount` (decimal)
    - `currency` (CurrencyCode)
  - `PaymentMethod` (enum): `CARD`, `WALLET`, `BANK_TRANSFER`
  - `PaymentCard`
    - `holderName` (string)
    - `number` (string)
    - `expiryMonth` (int)
    - `expiryYear` (int)
    - `cvv` (string)
  - `Ticket`
    - `ticketNumber` (string)
    - `status` (TicketStatus)
    - `issuedAt` (DateTime)
  - `TicketStatus` (enum): `ISSUED`, `VOIDED`, `REFUNDED`
  - `Booking`
    - `pnr` (string)
    - `status` (BookingStatus)
    - `passengers` (array of Passenger)
  - `BookingStatus` (enum): `ON_HOLD`, `TICKETED`, `CANCELLED`
  - `Passenger`
    - `type` (PassengerType)
    - `name` (Name)
    - `dob` (Date, optional)
    - `loyaltyNumber` (string, optional)
  - `PassengerType` (enum): `ADT`, `CHD`, `INF` (adult, child, infant)

The client will output:
- For each purchased ticket:
  - Number, status, issue date and time
- For each booking:
  - PNR, status, passengers
  - For each passenger:
    - Full name, passenger type, date of birth, loyalty card number
- The XML request
- The XML response
