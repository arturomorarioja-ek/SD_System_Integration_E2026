### Auction
Write an SSE server and an SSE client in the programming language(s) of your choice.

The SSE server will stream auction bids from the [Auction REST Service](https://github.com/arturomorarioja/py_rest_auction). The SSE client will display the said bids as they come (a console log is enough).

The Auction REST Service includes a Postman collection and environment for testing. Notice that the SSE server will need to access the Auction REST Service's SQLite database directly, so use proper OS paths.

### Solution
- [Server](https://github.com/arturomorarioja/js_sse_auction_server) (Express / Node.js)
- [Client](https://github.com/arturomorarioja/js_sse_auction_client)
