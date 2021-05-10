a. 
```SQL
SELECT Count(Orders.OrderId)
FROM Orders
WHERE Orders.ShipperId = 1;
```
54

b.
```SQL
SELECT Employees.LastName
FROM Employees
INNER JOIN Orders
ON Employees.EmployeeID = Orders.EmployeeID
GROUP BY Orders.EmployeeID
ORDER BY COUNT(Orders.EmployeeID) DESC LIMIT 1;
```
Peacock

c. 

```SQL
SELECT p.ProductName
FROM (SELECT od.ProductID, SUM(od.Quantity) as AMOUNT
	FROM CUSTOMERS as c, ORDERS as o, OrderDetails as od
	WHERE c.Country='Germany' AND c.CustomerID = o.CustomerID AND o.OrderID = od.OrderID
	GROUP BY ProductID) as x, Products as p
WHERE x.ProductID = p.ProductID and x.AMOUNT = (SELECT MAX(AMOUNT)
	FROM (SELECT od.ProductID, SUM(od.Quantity) as AMOUNT
		FROM CUSTOMERS as c, ORDERS as o, OrderDetails as od
		WHERE c.Country='Germany' AND c.CustomerID = o.CustomerID AND o.OrderID = od.OrderID
		GROUP BY ProductID
    )
)
```
Boston Crab Meat