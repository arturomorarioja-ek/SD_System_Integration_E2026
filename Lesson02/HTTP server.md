### HTTP server

Create a small HTTP server in the programming language of your choice from scratch (no frameworks).
- Recommended languages (in order): Python, Java, C#, Go
- Not recommended languages: Node.js, PHP

Implement the following endpoints:
- `GET /`. It returns HTML with information about the endpoints
- `GET /health`. It returns JSON with information about the service (e.g., name, status, current datetime)
- `POST /echo`. It receives raw JSON and returns it
