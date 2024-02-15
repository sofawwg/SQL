##TASK1

``` sql
SELECT 
 c.first_name,
 c.last_name,
COUNT (o.order_id) AS quality
FROM customers c 
JOIN orders o ON c.customer_id = o.customer_id
JOIN products p ON o.product_id = p.product_id
WHERE o.order_date BETWEEN '2024-01-15' AND '2024-02-15'
GROUP BY c.customer_id 
ORDER BY quality DESC
LIMIT 1;
```

##TASK2 

``` sql
  CREATE VIEW SRU AS
SELECT  c.first_name,c.last_name,  AVG(o.quantity * p.price) AS average,
  ABS((AVG(o.quantity * p.price))-(SELECT AVG(quantity * price) AS otklonenie          FROM orders JOIN products ON orders.product_id = products.product_id))
          AS cost_deviation  FROM customers c
  JOIN orders o ON c.customer_id = o.customer_id  JOIN products p ON o.product_id = p.product_id
  GROUP BY c.customer_id,c.first_name,c.last_name
```

##TASK3 

``` sql
UPDATE Products
SET price = CASE
    WHEN category = 'clothes' THEN price * 0.875 
    ELSE price * 0.95  
END;
```


