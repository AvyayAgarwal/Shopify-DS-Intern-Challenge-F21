# Question 2

---

#### a). How many orders were shipped by Speedy Express in total?

> 54

```
SELECT count(OrderID) AS "No of Orders Shipped by Speedy Express"
FROM Shippers s, Orders od
WHERE s.ShipperName = "Speedy Express"
AND s.ShipperID = od.ShipperID
```

#### b). What is the last name of the employee with the most orders?

> Peacock

```
SELECT emp.LastName
FROM Orders ord, Employees emp
WHERE emp.EmployeeID = ord.EmployeeID
GROUP BY ord.EmployeeID
ORDER BY COUNT(ord.OrderID) DESC
LIMIT 1
```

#### c). What product was ordered the most by customers in Germany?

> Boston Crab Meat

```
SELECT prod.ProductName
FROM Products prod, Customers cust, Orders ord, OrderDetails ordeets
WHERE cust.Country = "Germany"
	AND cust.CustomerID = ord.CustomerID
	AND ord.OrderID = ordeets.OrderID
    AND ordeets.ProductID = prod.ProductID
GROUP BY ordeets.ProductID
ORDER BY SUM(ordeets.Quantity) DESC
LIMIT 1
```