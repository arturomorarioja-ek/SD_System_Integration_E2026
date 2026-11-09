### Partitioning by Key Hash
Implement partitioning by key hash in MySQL or the relational database of your choice.

Create a table `user_sessions` with the following structure and seed data:

```sql
CREATE TABLE user_sessions (
    session_id INT NOT NULL,
    user_id INT NOT NULL,
    login_time DATETIME NOT NULL,
    PRIMARY KEY (session_id, user_id)
)
```

```sql
INSERT INTO user_sessions (session_id, user_id, login_time)
VALUES
    (1, 10, '2026-04-15 08:55:00'),
    (2, 11, '2026-04-15 09:02:00'),
    (3, 12, '2026-04-15 09:08:00'),
    (4, 13, '2026-04-15 09:13:00'),
    (5, 14, '2026-04-15 09:21:00'),
    (6, 15, '2026-04-15 09:27:00'),
    (7, 16, '2026-04-15 09:35:00'),
    (8, 17, '2026-04-15 09:41:00'),
    (9, 18, '2026-04-15 09:48:00'),
    (10, 19, '2026-04-15 09:56:00'),
    (11, 20, '2026-04-15 10:03:00'),
    (12, 21, '2026-04-15 10:11:00'),
    (13, 22, '2026-04-15 10:18:00'),
    (14, 23, '2026-04-15 10:26:00'),
    (15, 24, '2026-04-15 10:34:00'),
    (16, 25, '2026-04-15 10:42:00'),
    (17, 26, '2026-04-15 10:51:00'),
    (18, 27, '2026-04-15 10:59:00'),
    (19, 28, '2026-04-15 11:07:00'),
    (20, 29, '2026-04-15 11:16:00'),
    (21, 30, '2026-04-15 11:24:00'),
    (22, 31, '2026-04-15 11:33:00'),
    (23, 32, '2026-04-15 11:41:00'),
    (24, 33, '2026-04-15 11:50:00');
```

Divide the table into 4 partitions based on hashing `user_id`. Find out about your relational database's default hashing method in order to make it work.
