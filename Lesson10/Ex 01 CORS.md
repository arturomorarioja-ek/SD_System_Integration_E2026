### CORS

Work in groups of 4 or 5 students.

**Scenario 1: Simple `GET`**

Request
```
GET http://127.0.0.1:3000/projects
Origin: http://127.0.0.1:5500
```
Response
```
HTTP/1.1 200 OK
Content-Type: application/json
```
1. Is this a cross-origin request?
2. Is it a simple request?
3. Will the browser be allowed to read the response?
4. If negative, what should be done and where to allow the browser to read the response?

---
**Scenario 2: `POST` with JSON**

Cross-Origin Non-Simple Request (preflight needed)
```
POST http://127.0.0.1:3000/projects
Origin: http://127.0.0.1:5500
Content-Type: application/json
```
Body
```json
{
    "title": "New project",
    "description": "Created from frontend"
}
```

1. What `OPTIONS` request will the browser send?
2. Let us assume that the server returns the following response:
   ```
   HTTP/1.1 204 No Content
   Access-Control-Allow-Origin: http://127.0.0.1:5500
   ```
   Will the browser send the actual `POST` request?
3. If negative, what should be done and where to allow the browser to send the `POST` request?

---
**Scenario 3: Custom header**

Cross-origin request
```
POST http://127.0.0.1:3000/projects
Origin: http://127.0.0.1:5500
Content-Type: text/plain
X-Requested-With: fetch
```

1. Would the browser send a preflight request? Why?
2. If affirmative, what should the preflight response look like?

---
**Scenario 4: Request with credentials**

A request with origin `http://127.0.0.1:5500` calls an API with credentials included. The API server responds:
```
HTTP/1.1 200 OK
Access-Control-Allow-Origin: *
Access-Control-Allow-Credentials: true
Content-Type: application/json
Set-Cookie: sessionId=abc123; HttpOnly
```
1. The browser will block the response. Why?
2. What should be done and where for the browser to process the response?

---
**Scenario 5: Simple request**

Request
```
GET http://127.0.0.1:3000/projects
Origin: http://127.0.0.1:3000
```
1. Is preflight necessary?
2. Can the browser read the response?
