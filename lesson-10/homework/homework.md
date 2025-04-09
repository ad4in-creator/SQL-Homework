select 
    d.DepartmentName,
    count(e.EmployeeID) as EmployeeCount
from 
    Departments d
join 
    Employees e on d.DepartmentID = e.DepartmentID
group by
    d.DepartmentName
having 
    count(e.EmployeeID) > 10;
select 
    p.ProductID,
    p.ProductName
from 
    Products p
left join 
    Sales s on p.ProductID = s.ProductID
where 
    s.ProductID is null;
select 
    e.EmployeeName,
    d.DepartmentName
from 
    Employees e
join 
    Departments d on e.DepartmentID = d.DepartmentID;
select 
    e1.EmployeeName AS Employee1,
    e2.EmployeeName AS Employee2,
    e1.ManagerID
from 
    Employees e1
join 
    Employees e2 ON e1.ManagerID = e2.ManagerID
where 
    e1.EmployeeID != e2.EmployeeID;
select 
    o.OrderID,
    o.OrderDate,
    c.FirstName,
    c.LastName
from 
    Orders o
join 
    Customers c on o.CustomerID = c.CustomerID
where 
    year(o.OrderDate) = 2022;
    SELECT 
    e.EmployeeName,
    e.Salary,
    d.DepartmentName
from 
    Employees e
join 
    Departments d on e.DepartmentID = d.DepartmentID
where 
    d.DepartmentName = 'Sales'
    andSELECT 
    o.OrderID,
    o.OrderDate,
    p.PaymentDate,
    p.Amount
from 
    Orders o
join 
    Payments p ON o.OrderID = p.OrderID;
 e.Salary > 60000;
select 
    p.ProductID,
    p.ProductName
from 
    Products p
left join 
    OrderDetails od on p.ProductID = od.ProductID
where 
    od.ProductID is null;
