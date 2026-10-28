### JWT authenticated to do list
Implement JWT authentication in the To Do list REST API with the following requirements:
- User credentials must be stored in a relational database (e.g., SQLite, MySQL)
- Choose a token revocation strategy (blacklist or whitelist). Store the JWT IDs in a key-value store (e.g., Redis)
- Login endpoint: `/auth/login`. Body parameters: `username` and `password`
- All other endpoints must be authenticated via the JWT as a bearer token
- Logout endpoint: `/auth/logout`
- User creation is not necessary
