### Bearer token authenticated to do list
Implement bearer token authentication in the To Do list REST API with the following requirements:
- User credentials must be stored in a relational database (e.g., SQLite, MySQL)
- The bearer tokens must be stored in a key-value store (e.g., Redis)
- Login endpoint: `/auth/login`. Body parameters: `username` and `password`
- All other endpoints must be authenticated via the bearer token
- Logout endpoint: `/auth/logout`. It will delete the bearer token
- User creation is not necessary
