### REST API Assessment
Work in pairs.

Assess whether the following APIs used by the [API Consumption sample](https://github.com/arturomorarioja/js_api_consumption) are RESTful or not. Explain why.
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

- [The TicketMaster Discovery API](https://developer.ticketmaster.com/products-and-docs/apis/discovery-api/v2/). **RESTful**
   - Client-Server. Uses HTTP
   - Stateless. No relationship between requests
   - Cacheable. Uses HTTP
   - Layered system. The client is unaware of its internals
   - Uniform interface
      - Resource identification in request. Examples
        ```
          GET /discovery/v2/events
          GET /discovery/v2/events/{id}
          GET /discovery/v2/events/{id}/images
          GET /discovery/v2/venues
          GET /discovery/v2/venues/{id}
          GET /discovery/v2/attractions
          GET /discovery/v2/attractions/{id}
          GET /discovery/v2/classifications
          GET /discovery/v2/classifications/{id}
          GET /discovery/v2/classifications/genres/{id}
        ```
      - Resource manipulation through representations. As it is a read-only API, this point does not apply
      - Self-descriptive messages. By following REST naming conventions
      - HATEOAS. It includes a top level `_links` key with `self`, `first`, `last`, and `next`, the four of them containing `href`
