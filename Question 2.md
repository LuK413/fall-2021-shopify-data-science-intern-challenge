a. Is there a way to remove the hardcoding of Speedy Express?
```SQL
SELECT Count(Orders.OrderId)
FROM Orders
WHERE Orders.ShipperId = 1;
```

b. What if there are ties?
```SQL
SELECT Employees.LastName
FROM Employees
INNER JOIN Orders
ON Employees.EmployeeID = Orders.EmployeeID
GROUP BY Orders.EmployeeID
ORDER BY COUNT(Orders.EmployeeID) DESC LIMIT 1;
```

c. 