### Data Warehouse
Using the programming language of your choice, code an ETL process that creates a data warehouse based on the [tenant-based sharding example](https://github.com/arturomorarioja/mysql_sharding_tenant_based).

The data warehouse will perform an ETL process, consolidating data from all three shards into a new database.

The new database will contain the same tables as the shards (`continents`, `customers`, and `invoices`), yet changes must be made to accommodate all the data, since the same customer IDs and invoice IDs are used in the three shards.

The source shards must remain unchanged and the destination schema must preserve the relationships between customers and invoices.

Accessing the data sources (example with the first shard):

#### PHP PDO

```php
new PDO(
    'mysql:host=127.0.0.1;port=19409;dbname=customer_sharding_by_continent;charset=utf8mb4',
    'warehouse_reader',
    'warehouse_reader'
);
```

#### Python / mysql-connector-python

```python
mysql.connector.connect(
    host="127.0.0.1",
    port=19409,
    database="customer_sharding_by_continent",
    user="warehouse_reader",
    password="warehouse_reader",
)
```

Use ports 19410 and 19411 for the other shards.

#### Node.js / mysql2

```javascript
{
  host: "127.0.0.1",
  port: 19409,
  database: "customer_sharding_by_continent",
  user: "warehouse_reader",
  password: "warehouse_reader"
}
```

#### Java JDBC

```text
jdbc:mysql://127.0.0.1:19409/customer_sharding_by_continent
```

#### C# / MySqlConnector

```text
Server=127.0.0.1;Port=19409;Database=customer_sharding_by_continent;User ID=warehouse_reader;Password=warehouse_reader;
```

#### Go / go-sql-driver/mysql

```text
warehouse_reader:warehouse_reader@tcp(127.0.0.1:19409)/customer_sharding_by_continent
```

### Solution
[PHP/MySQL](https://github.com/arturomorarioja/mysql_data_warehouse)
