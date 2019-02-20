# DATABASE ASSIGNMENT

## ER Diagram:
![ER Diagram](
https://github.com/parichay28/SQL_Queries/blob/master/Sample%20ER%20Diagram.jpg)

## Write Queries for:
  1. List the customer name, check number, payment date and amount for the customer with customer number 1001.
  2. List the employee number, last name and first name for all the employees  who reports to their manager with employee id 1001.
  3. List the customer name, phone and total amount of all customers with credit limit greater than 10000.
  4. List all the order number, order date, product code, product name, quantity ordered, price each  for the customer with customer number 1001.
  

## Queries:

#### 1
```
SELECT customers.customerName,
payments.checkNumber,
payments.paymentDate,
payments.amount FROM(customers
INNER JOIN payments
ON customers.customerNumber = payments.customerNumber)
WHERE customers.customerNumber = 1001
```

#### 2
```
SELECT employee.employeeNumber, employee.firstName, employee.lastName
FROM(employees employee
INNER JOIN employees manager
ON employee.reportsTo = manager.employeeNumber)
WHERE employee.reportsTo = 1001
```

#### 3
```
SELECT customerName, phone, SUM(payments.amount)
FROM customers
JOIN payments
ON customers.customerNumber = payments.customerNumber
WHERE creditLimit > 10000
GROUP BY payments.amount;
```

#### 4
```
SELECT o.orderNumber, o.orderDate, od.productCode, p.productName, od.quantityOrdered, od.priceEach
FROM products p
JOIN orderdetails od
ON p.productCode = od.productCode
JOIN orders o
ON o.orderNumber = od.orderNumber
WHERE o.customerNumber = 1001
```
