## Echo

Using the programming language of your choice, implement the following RPC using gRPC:

```proto
rpc Echo(Message) returns (Message)
```

Specification
- `Message` has one `string text`
- The client prompts the user for a message and sends it to the server
- The server simply returns `"You said: <text>"`
- The client displays the server response

Steps
1. Create the `.proto` file
2. Generate the stubs
3. Implement the server and the client

### Solution
[Python](https://github.com/arturomorarioja/py_grpc_echo)
