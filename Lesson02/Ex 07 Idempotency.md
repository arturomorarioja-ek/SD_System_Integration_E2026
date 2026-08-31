### Idempotency
Implement an idempotent `POST /reservations` endpoint of a restaurant reservation service using a relational database as data storage. Choose one of these three schemes:
- **Database unique constraints**. The idempotency key is stored in the database together with the reservation, with a unique constraint preventing duplicates.
- **In-memory tracking**. The server stores used idempotency keys and their responses in a local in-memory data structure.
- **Distributed cache**. The server stores used idempotency keys in a shared cache such as Redis, so several server instances can check the same keys.

Use the following data schema (SQLite, adapt it to the RDB of your choice):

```sqlite
CREATE TABLE IF NOT EXISTS reservations (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    idempotency_key TEXT UNIQUE,
    request_hash TEXT,
    idempotency_expires_at REAL,
    customer_name TEXT NOT NULL,
    date TEXT NOT NULL,
    time TEXT NOT NULL,
    persons INTEGER NOT NULL,
    status TEXT NOT NULL
)
```
