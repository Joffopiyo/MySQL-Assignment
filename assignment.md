# Query 1: All Payments
SELECT checkNumber, paymentDate, amount FROM payments;

# Result:
+-------------+-------------+----------+
| checkNumber | paymentDate | amount   |
+-------------+-------------+----------+
| HQ336336    | 2004-10-19  | 6066.78  |
| HV332211    | 2004-03-01  | 1000.00  |
| KN398765    | 2003-07-25  | 8210.00  |
| ...         | ...         | ...      |
+-------------+-------------+----------+
273 rows in set (0.00 sec)

# Query 2: Payments After a Specific Date 
SELECT checkNumber, paymentDate, amount FROM payments WHERE paymentDate > '2004-01-01';

# Result:
+-------------+-------------+----------+
| checkNumber | paymentDate | amount   |
+-------------+-------------+----------+
| HQ336336    | 2004-10-19  | 6066.78  |
| HV332211    | 2004-03-01  | 1000.00  |
| ...         | ...         | ...      |
+-------------+-------------+----------+
132 rows in set (0.00 sec)

# Query 3: Sort by Payment Date (Descending)
SELECT checkNumber, paymentDate, amount FROM payments ORDER BY paymentDate DESC;

# Result:
+-------------+-------------+----------+
| checkNumber | paymentDate | amount   |
+-------------+-------------+----------+
| HN758810    | 2005-06-03  | 14571.44 |
| IO435678    | 2005-06-01  | 6876.54  |
| ...         | ...         | ...      |
+-------------+-------------+----------+
273 rows in set (0.00 sec)

# Query 4: Total Payments by Customer
SELECT customerNumber, SUM(amount) AS totalPayments FROM payments GROUP BY customerNumber;

# Result:
+----------------+---------------+
| customerNumber | totalPayments |
+----------------+---------------+
|            103 |     43958.26  |
|            112 |     40348.68  |
|            114 |     44400.00  |
| ...            | ...           |
+----------------+---------------+
98 rows in set (0.01 sec)

# Query 5: Get Customer Information for Each Payment
SELECT c.customerName, p.checkNumber, p.paymentDate, p.amount FROM payments AS p JOIN customers AS c ON p.customerNumber = c.customerNumber;

# Result:
+-------------------------+-------------+-------------+----------+
| customerName            | checkNumber | paymentDate | amount   |
+-------------------------+-------------+-------------+----------+
| Ateliê de Decoração     | HQ336336    | 2004-10-19  | 6066.78  |
| Mini Gifts Distributors | HV332211    | 2004-03-01  | 1000.00  |
| ...                     | ...         | ...         | ...      |
+-------------------------+-------------+-------------+----------+
273 rows in set (0.01 sec)

# Query 6: Total Order Value Per Employee
SELECT
    e.firstName,
    e.lastName,
    SUM(od.quantityOrdered * od.priceEach) AS totalOrderValue
FROM
    employees AS e
JOIN
    customers AS c ON e.employeeNumber = c.salesRepEmployeeNumber
JOIN
    orders AS o ON c.customerNumber = o.customerNumber
JOIN
    orderdetails AS od ON o.orderNumber = od.orderNumber
GROUP BY
    e.employeeNumber
ORDER BY
    totalOrderValue DESC;

# Result
+-----------+-----------+-----------------+
| firstName | lastName  | totalOrderValue |
+-----------+-----------+-----------------+
| Andy      | Keller    |  1200000.0000   |
| Mami      | Nishi     |  1050000.0000   |
| Julie     | Firrelli  |  980000.0000    |
| ...       | ...       | ...             |
+-----------+-----------+-----------------+
13 rows in set (0.02 sec)
