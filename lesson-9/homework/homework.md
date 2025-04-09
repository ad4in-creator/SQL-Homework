1. select p.productname, s.suppliername from Products p cross join suppliers s
2. select d.DepartmentName, e.Name from Departments d cross join Employees e
3. select s.SupplierName, p.ProductName from Products p join suppliers s on p.SupplierID=s.SupplierID
4. select c.FirstName, o.OrderID from Orders o join Customers c on o.CustomerID=c.CustomerID
5. select c.CourseID, s.StudentID from Courses c cross join Students s
6. select * from Products p join Orders o on p.ProductID=o.ProductID
7. select e.Name, d.DepartmentName from Departments d join Employees e on d.DepartmentID=e.DepartmentID
8. select Name, CourseID from Students join Enrollments on Students.StudentID = Enrollments.StudentID
9. select * from Payments p join Orders o on p.OrderID=o.OrderID
10. select * from Orders join Products on Orders.ProductID=Products.ProductID and Products.Price>100
11. select * from Employees join Departments on Employees.DepartmentID<>Departments.DepartmentID
12. select * from Orders o join Products p on o.ProductID=p.ProductID and o.Quantity>p.StockQuantity
13. select c.FirstName, s.ProductID from Customers c join Sales s on c.CustomerID=s.CustomerID and s.SaleAmount>=500
14. select s.Name, c.CourseName from Courses c join Enrollments e on c.CourseID=e.CourseID join Students s on s.StudentID=e.StudentID
15. select * from Products p join Suppliers s on p.SupplierID=s.SupplierID and s.SupplierName like ('%tech%')
16. select * from Orders o join Payments p on o.OrderID=p.OrderID and p.Amount<o.TotalAmount
17. select * from Employees e1 join Employees e2 on e1.ManagerID =e2.EmployeeID and e1.Salary>e2.Salary
18. select * from Products p join Categories c on p.Category=c.CategoryName where c.CategoryName='Electronics' or c.CategoryName='Furniture'
19. select * from Sales s join Customers c on s.CustomerID=c.CustomerID and c.Country = 'USA'
20. select * from Orders o join Customers c on o.CustomerID=c.CustomerID and c.Country = 'Germany' and o.TotalAmount>100
21. select distinct(e1.Name), e2.Name from Employees e1 join Employees e2 on e1.DepartmentID<>e2.DepartmentID order by e1.Name
22. select * from Payments pa join Orders o on pa.OrderID=o.OrderID join Products pr on o.ProductID=pr.ProductID where pa.Amount!=(o.Quantity*pr.Price)
23. select S.StudentID, S.Name from Students S left join Enrollments e on s.StudentID=e.StudentID left join Courses c on e.CourseID=c.CourseID where e.EnrollmentID is null
24. select * from Employees e1 join Employees e2 on e1.ManagerID=e2.EmployeeID where e2.Salary<=e1.Salary
25. select o.CustomerID from Payments pa right join Orders o on pa.OrderID=o.OrderID left join Products pr on o.ProductID=pr.ProductID where pa.Amount is null
