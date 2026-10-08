[System Integration - Autumn 2026](https://github.com/arturomorarioja-ek/SD_System_Integration_E2026/blob/main/README.md)

# Lesson 7 - 8 October

## Part 1: gRPC

### Recommendation

The best programming language to Work with gRPC is Go (Golang). If you want to give it a try:
1. [Install Go](https://go.dev/dl/)
2. Install gRPC: `go install github.com/fullstorydev/grpcurl/cmd/grpcurl@latest`

### Homework
- Check out the **gRPC** slides, with especial attention to:
  - Protocol buffers
  - gRPC testing
- Check out the following Protocol Buffer examples:
  - [Telemedicine service](https://github.com/arturomorarioja-ek/SD_System_Integration_E2026/blob/main/Lesson07/telemedicine_service.proto)
  - [Telemedicine service - extended](https://github.com/arturomorarioja-ek/SD_System_Integration_E2026/blob/main/Lesson07/telemedicine_service_extended.proto)
- Check out the following code samples:
  - [Greeter service (Go)](https://github.com/arturomorarioja/go_grpc_greeter_src). You can follow the README to generate the stubs and package
  - [Greeter service (Go)](https://github.com/arturomorarioja/go_grpc_greeter). Ready-made version
  - [Rides (Python)](https://github.com/arturomorarioja/py_grpc_rides). Follow the README to try partial demos, then run the client's unary `Start` request and streaming `Track` request
- Solve the following exercises:
  - Protocol buffers: [Warehouse Robot Service](https://github.com/arturomorarioja-ek/SD_System_Integration_E2026/blob/main/Lesson07/gRPC%20Ex%2001%20Warehouse%20Robot.md)
  - gRPC server and client: [Echo](https://github.com/arturomorarioja-ek/SD_System_Integration_E2026/blob/main/Lesson07/gRPC%20Ex%2002%20Echo.md)
  - [Echo with validation](https://github.com/arturomorarioja-ek/SD_System_Integration_E2026/blob/main/Lesson07/gRPC%20Ex%2003%20Echo%20with%20Validation.md)
  - [Quiz](https://github.com/arturomorarioja-ek/SD_System_Integration_E2026/blob/main/Lesson07/gRPC%20Ex%2004%20Quiz.md)

## Part 2: WebSockets

### Homework
- Check out the following slide deck on Itslearning:
  - **WebSockets**, with especial attention to SSE and the comparisons between long polling, WebSockets, and gRPC
- Check out the following code samples:
  - [Long Polling Server (Python)](https://github.com/arturomorarioja/py_lp_server) and [Long Polling Client (JavaScript)](https://github.com/arturomorarioja/js_lp_client)
  - [WS Server (Python)](https://github.com/arturomorarioja/py_ws_server) and [WS Client (JavaScript)](https://github.com/arturomorarioja/js_ws_client)
    - To create a Postman collection, create the ws connection first, the save it in a new collection. WebSockets collections cannot be exported
  - [WS Echo Client (JavaScript)](https://echo.websocket.org/)
    - It connects to the sample WebSockets server at https://echo.websocket.org/, but you can also use it to connect to the [WS Server](https://github.com/arturomorarioja/py_ws_server)
- Solve the following exercises:
  - SSE: [Auction](https://github.com/arturomorarioja-ek/SD_System_Integration_E2026/blob/main/Lesson07/WS%20Ex%2001%20Auction.md)
  - WS: [Voting](https://github.com/arturomorarioja-ek/SD_System_Integration_E2026/blob/main/Lesson07/WS%20Ex%2002%20Voting.md) 
