# Assignment Questions1. 
1. Retrieve payment data from the payments table.SELECT checkNumber, paymentDate, amount FROM payments;

# Result:
| checkNumber | paymentDate | amount   |
+-------------+-------------+----------+
| HQ336336    | 2004-10-19  | 6066.78  |
| HV332211    | 2004-03-01  | 1000.00  |
| KN398765    | 2003-07-25  | 8210.00  |
| ...         | ...         | ...      |
+-------------+-------------+----------+
273 rows in set (0.00 sec)

2. Retrieve 'In Process' orders and sort by order date.SELECT orderDate, requiredDate, status FROM orders WHERE status = 'In Process' ORDER BY orderDate DESC;

# Result:
| orderDate  | requiredDate | status     |
+------------+--------------+------------+
| 2005-05-31 | 2005-06-08   | In Process |
| 2005-05-31 | 2005-06-07   | In Process |
| 2005-05-30 | 2005-06-11   | In Process |
| 2005-05-30 | 2005-06-05   | In Process |
| 2005-05-29 | 2005-06-07   | In Process |
| 2005-05-29 | 2005-06-06   | In Process |
+------------+--------------+------------+
6 rows in set (0.00 sec)

3. Display employee details for 'Sales Reps'.SELECT firstName, lastName, email FROM employees WHERE jobTitle = 'Sales Rep' ORDER BY employeeNumber DESC;

# Result:
| firstName | lastName  | email                           |
+-----------+-----------+---------------------------------+
| Martin    | Gerard    | mgerard@classicmodelcars.com    |
| Yoshimi   | Kato      | ykato@classicmodelcars.com      |
| Mami      | Nishi     | mnishi@classicmodelcars.com     |
| ...       | ...       | ...                             |
+-----------+-----------+---------------------------------+
17 rows in set (0.00 sec)

4. Retrieve all records from the offices table.SELECT * FROM offices;

# Result:
| officeCode | city          | phone            | addressLine1             | addressLine2 | state      | country   | postalCode | territory |
+------------+---------------+------------------+--------------------------+--------------+------------+-----------+------------+-----------+
| 1          | San Francisco | +1 650 219 4782  | 100 Market Street        | Suite 300    | CA         | USA       | 94080      | NA        |
| 2          | Boston        | +1 215 837 0825  | 1550 Court Place         | Suite 102    | MA         | USA       | 02107      | NA        |
| ...        | ...           | ...              | ...                      | ...          | ...        | ...       | ...        | ...       |
+------------+---------------+------------------+--------------------------+--------------+------------+-----------+------------+-----------+
7 rows in set (0.00 sec)

5. Fetch product details, sorted and limited.SELECT productName, quantityInStock FROM products ORDER BY buyPrice ASC LIMIT 5;

#Result:
| productName                               | quantityInStock |
+-------------------------------------------+-----------------+
| 1958 Chevy Corvette Limited Edition       |           2542  |
| 1982 Lamborghini Diablo                   |           7723  |
| 1938 Cadillac V-16 Presidential Limousine |           2847  |
| 1936 Mercedes Benz 500k Roadster          |           2081  |
| 1939 Chevrolet Deluxe Coupe               |           7332  |
+-------------------------------------------+-----------------+
5 rows in set (0.00 sec)
