### Bearer token authenticated to do list
Implement bearer token authentication in the To Do list REST API with the following requirements:
- User credentials must be stored in a relational database (e.g., SQLite, MySQL)
- The bearer tokens must be stored in a key-value store (e.g., Redis)
- The bearer tokens must be hardened via hashing
- Login endpoint: `/auth/login`. Body parameters: `username` and `password`
- All other endpoints must be authenticated via the bearer token
- Logout endpoint: `/auth/logout`. It will delete the bearer token
- User creation is not necessary

### Solution
[SQLite/Redis/Python/Flask](https://github.com/arturomorarioja/auth_bearer_token_to_do_list_rest_api)
