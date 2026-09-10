### REST API Assessment
Work in pairs.

Assess whether the following APIs are RESTful or not. Explain why.
- [The OpenWeather Map "Current Weather Data" API](https://openweathermap.org/current)
- [The MapBox "Static Images" API](https://docs.mapbox.com/api/maps/#static-images)
- [The TicketMaster Discovery API](https://developer.ticketmaster.com/products-and-docs/apis/discovery-api/v2/)
  
### Solution
- [The OpenWeather Map "Current Weather Data" API](https://openweathermap.org/current). **Not RESTful**
   - Resources are identified as parameters, not as part of the URL (`/data/2.5/weather?q=Copenhagen` instead of `/cities/2618425/weather`)
   - Responses are not self-descriptive 
   - No HATEOAS. Responses do not contain links
- [The MapBox "Static Images" API](https://docs.mapbox.com/api/maps/#static-images). **Not RESTful**
   - The endpoint is named `static` instead of describing a resource
   - No HATEOAS. Responses are binary images with no further structured information
      - REST paradox: returning binary data does not invalidate an API as RESTful, yet it makes it difficult to comply with HATEOAS
      <br><br>
      > Solutions:
      >  - HATEOAS in HTTP link headers
      >  - Multipart responses
      >  - Custom binary media types with embedded metadata (e.g., SVG with hyperlinks, annotations in a PDF)

- [The TicketMaster Discovery API](https://developer.ticketmaster.com/products-and-docs/apis/discovery-api/v2/). **Not RESTful**
   - It uses verbs in the URI: `/discovery/v2/suggest`
   - It includes file extensions in the URI: `/discovery/v2/events.json?apikey={apikey}`
