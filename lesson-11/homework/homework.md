select 
    c.CustomerName, 
    o.OrderID, 
    o.Address, 
    o.OrderDate
from 
    Customers c
join
    Orders o on c.CustomerID = o.CustomerID
where 
    c.Country = 'USA' 
    and o.Address regeXP '^[0-9]{4}'  -- Address starts with 4 digits
    select 
    p.ProductName, 
    s.SaleDate, 
    s.SaleAmount
from 
    Products p
join 
    Sales s on p.ProductID = s.ProductID
where 
    year(s.SaleDate) = 2022 
    or s.SaleAmount > 400
  select 
    p.ProductName, 
    t.TotalSalesAmount
from 
    Products p
join 
    (select 
        ProductID, 
        SUM(SaleAmount) as TotalSalesAmount
     from 
        Sales
     group by 
        ProductID) t on p.ProductID = t.ProductID
select 
    e.EmployeeName, 
    d.DepartmentName, 
    e.Salary
from 
    Employees e
join 
    Departments d on e.DepartmentID = d.DepartmentID
where 
    d.DepartmentName = 'HR' 
    and e.Salary > 50000;
    SELECT 
    p.ProductName, 
    SUM(s.QuantitySold) AS QuantitySold, 
    p.Price
from 
    Products p
join 
    Sales s on p.ProductID = s.ProductID
GROUP BY 
    p.ProductName, p.Price
having 
    SUM(s.QuantitySold) > 100 
    and p.Price > 500;
seect 
    e.EmployeeName, 
    d.DepartmentName, 
    e.Salary
from 
    Employees e
join 
    Departments d on e.DepartmentID = d.DepartmentID
where 
    (d.DepartmentName = 'Sales' OR d.DepartmentName = 'Marketing')
    and e.Salary > 60000;
