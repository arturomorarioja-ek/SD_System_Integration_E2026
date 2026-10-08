## Echo with Validation

Introduce the two following functionalities to the Echo exercise:
1. Input validation. If the message sent by the client is empty, the server will return the gRPC status code `INVALID_ARGUMENT` and an error message
2. Add a timestamp to the protocol buffer definition
    - The client will fill it and send it to the server
    - The server will return it
    - The client will display it
    - If the client does not fill it, the server will generate it

### Solution
[Python](https://github.com/arturomorarioja/py_grpc_echo_validation)
