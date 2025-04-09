select top 5 * from Employees;
select distinct ProductName from Products;
select * from Products where Price > 100;
select * from Customers where FirstName like 'A%';
select * from Products order by Price asc;
select * from Employees where Salary >= 60000 and DepartmentName = 'HR';
select isnull (Email, 'noemail@example.com') as 'No email' from Employees;
select * from products where Price > 50 and Price < 100;
select distinct Category, ProductName from Products;
select distinct Category, ProductName from Products order by ProductName desc;
select top 10 * from Products order by Price DESC;
select COALESCE (FirstName, LastName) as AnyAvailableName from Employees;
select distinct Category, Price from Products;
select * from Employees where Age > 30 and Age < 40 or DepartmentName = 'Marketing';
select * from Employees order by Salary DESC offset 10 rows FETCH next 10 rows only;
select * from products where Price <= 1000 and StockQuantity > 50 order by StockQuantity asc;
select * from products where ProductName LIKE '%E%';
SELECT * from Employees where DepartmentName in ('HR', 'IT', 'Finance');
select * from Customers order by City asc, PostalCode desc;
select top 10 * from Sales order by SaleAmount DESC;
select FirstName + ' ' + LastName as FullName from Employees;
select distinct Category, ProductName, Price from products where Price > 50;
select * from Products where Price < 0.1 * (select AVG(price) from Products);
select * from Employees where Age < 30 and DepartmentName in ('HR', 'IT');
select * from Employees where Email like '%@gmail.com';
select * from Employees where Salary > All (select Salary from Employees where DepartmentName = 'Sales')
Select * from Orders where OrderDate between dateadd (DAY, -180, getDATE()) and getDATE()
