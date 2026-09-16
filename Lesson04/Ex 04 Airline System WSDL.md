### Airline system
Write code in the programming language of your choice that generates a WSDL document that implements the `SearchFlights` operation for an airline system with the following requirements:

- Core data types
  - Simple types
    - `IataCode`: string (IATA 3-letter airport code, e.g., `CPH`, `MAD`)
    - `CabinClass` (enum): `ECONOMY`, `PREMIUM_ECONOMY`, `BUSINESS`, `FIRST`
  - Complex types
    - `PassengerCount`: number of adults, children and infants
    - `Money`: amount and currency
    - `Flight`. Including the following fields:
      - `carrier`. Airline name
      - `flightNumber`. Can contain alphanumeric characters
      - `departDateTime`
      - `arriveDateTime`
      - `origin`. `IataCode`
      - `destination`. `IataCode`
      - `price`. `Money`
- Messages
  - `SearchFlightsRequest`. Fields:
    - `origin`. `IataCode`
    - `destination`. `IataCode`
    - `departureDate`
    - `returnDate`
    - `passengers`. `PassengerCount`
    - `cabin`. `CabinClass`
  - `SearchFlightsResponse`. Fields:
    - `flights`. List of `Flight`
   
No regEx is necessary.
