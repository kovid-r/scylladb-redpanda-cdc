## Create a Keyspace

```sql 
CREATE KEYSPACE quickstart_keyspace WITH REPLICATION = {'class': 'SimpleStrategy', 'replication_factor': 1};
USE quickstart_keyspace;
```

## Create an `orders` table
CREATE TABLE orders(
   customer_id int,
   order_id int,
   product text,
   PRIMARY KEY(customer_id, order_id)) WITH cdc = {'enabled': true};
   
## Insert initial data

```sql
INSERT INTO orders(customer_id, order_id, product) VALUES (1, 1, 'pizza');
INSERT INTO orders(customer_id, order_id, product) VALUES (1, 2, 'cookies');
INSERT INTO orders(customer_id, order_id, product) VALUES (1, 3, 'tea');
```

## Insert new data

```sql
INSERT INTO orders(customer_id, order_id, product) VALUES (1, 4, 'chips');
INSERT INTO orders(customer_id, order_id, product) VALUES (1, 5, 'lollies');
INSERT INTO orders(customer_id, order_id, product) VALUES (1, 5, 'pasta');
```

## Update one of the records

```sql
UPDATE orders SET product = 'spaghetti' WHERE order_id = 6 and customer_id = 1;
```
