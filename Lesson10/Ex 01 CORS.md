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

#### SOLUTION
1. Is this a cross-origin request?
  
    - Yes, because the ports differ

2. Is this a simple request?
  
    - Yes (`GET`, no non-simple headers, no non-simple content type)

3. Will the browser be allowed to read the response?
  
    - No

4. If negative, what should be done and where to allow the browser to read the response?
  
    - The server should return an `Access-Control-Allow-Origin` header that includes the origin (e.g., `Access-Control-Allow-Origin: http://127.0.0.1:5500`, `Access-Control-Allow-Origin: *`)

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

#### SOLUTION
1. What `OPTIONS` request will the browser send?

    ```
    OPTIONS http://127.0.0.1:3000/projects
    Origin: http://127.0.0.1:5500
    Access-Control-Request-Method: POST
    Access-Control-Request-Headers: content-type
    ```
2. Let us assume that the server returns the following response:
   ```
   HTTP/1.1 204 No Content
   Access-Control-Allow-Origin: http://127.0.0.1:5500
   ```
   Will the browser send the actual `POST` request?

    - No
4. If negative, what should be done and where to allow the browser to send the `POST` request?

    - The server should allow this origin, the `POST` method, and the `Content-Type` header by returning headers similar to the following:
      ```
      Access-Control-Allow-Origin: http://127.0.0.1:5500
      Access-Control-Allow-Methods: POST
      Access-Control-Allow-Headers: Content-Type      
      ```
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

#### SOLUTION

1. Would the browser send a preflight request? Why?

    - Yes, because the request includes a custom header (`X-Requested-With`)

2. If affirmative, what should the preflight response look like?

    ```
    Access-Control-Allow-Origin: http://127.0.0.1:5500
    Access-Control-Allow-Methods: POST
    Access-Control-Allow-Headers: Content-Type, X-Requested-With
    ```
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

#### SOLUTION
1. The browser will block the response. Why?

    - With credentials, the server cannot return `Access-Control-Allow-Origin: *`
2. What should be done and where for the browser to process the response?

    - The server should return a more specific value for the `Access-Control-Allow-Origin` header (e.g., `Access-Control-Allow-Origin: http://127.0.0.1:5500`)

---
**Scenario 5: Simple request**

Request
```
GET http://127.0.0.1:3000/projects
Origin: http://127.0.0.1:3000
```
1. Is preflight necessary?
2. Can the browser read the response?

#### SOLUTION
1. Is preflight necessary?

    - No, because it is a same-origin request (origin and destination protocol, host, and port match)
2. Can the browser read the response?

    - Yes, because CORS does not apply
