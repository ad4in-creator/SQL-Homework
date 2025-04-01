-lesson-7

--Aggregate Functions, filtering aggregated
--data

--1. Explaining MIN and MAX (apply these to numbers and characters)

--2. Showing the difference COUNT (*), COUNT (columnname) and Count (distinct columnname)

--3. Explaining AVG and SUM

--4. Applying Aggregate functions with Group by

--5. Filtering aggregated data with HAVING

--Avg, sum, count, min, max

--create database F24_class7
use F24_class7

CREATE TABLE Products (
    ProductID INT,
    ProductName VARCHAR(50),
    Price DECIMAL(10, 2)
);

INSERT INTO Products VALUES
(1, 'Apple', 1.50),
(2, 'Banana', 1.00),
(3, 'Mango', 2.00),
(4, 'Orange', 1.20);

Select * from Products

--1. Explaining MIN and MAX (apply these to numbers and characters)
Select MAX(price) from Products	--numeric data
Select Min(price) from Products	--numeric data

Select MAX(ProductName) from Products
Select Min(ProductName) from Products

Select * from Products

--2. Showing the difference COUNT (*), COUNT (columnname) and Count (distinct columnname)

Select COUNT(ProductName) from Products
Select COUNT(*) from Products

insert into Products values (5, null, 1.75)

Select COUNT(Price) from Products

Select COUNT(*) from Products

insert into Products values (null, null, null)

Select COUNT(productid) from Products

insert into Products values (6, '', 1.25)

Select * from Products
Select COUNT(ProductName) from Products	
insert into Products values (8, 'Apple', 1.25)
insert into Products values (10, 'Banana', 1.55)

Select * from Products
Select COUNT(distinct ProductName) from Products

Select distinct ProductName from Products

--3. Explaining AVG and SUM

Select * from Products
Select AVG(price) from Products
Select SUM(price)/COUNT(price) from Products
Select COUNT(price) from Products

Select AVG(Productname) from Products

--insert into Products values (11, 'Banana', '') This throws an error

Select * from Products

--4. Applying Aggregate functions with Group by

Select ProductName, AVG(price) from Products
group by ProductName

Update Products
set Price = 0
where Price is null

Select ProductID, AVG(price) from Products
group by ProductID

Select * from Products

insert into Products values (1, 'Apple', 3.00)

--5. Filtering aggregated data with HAVING

Select ProductName, AVG(price) from Products
group by ProductName
having AVG(price) > 1.5

Select ProductName, AVG(price) from Products
group by ProductName
having AVG(price) > 1.5

--Select * from Products
--having Price > 1.5  ----Column 'Products.Price' is invalid in the HAVING clause because it is not contained in either an aggregate function or the GROUP BY clause.

--Puzzle 1
CREATE TABLE Sales (
    SaleID INT PRIMARY KEY,
    ProductName VARCHAR(50),
    Quantity INT,
    Price DECIMAL(10,2)
);

INSERT INTO Sales (SaleID, ProductName, Quantity, Price) VALUES
(1, 'Laptop', 2, 800.00),
(2, 'Phone', 3, 500.00),
(3, 'Laptop', 1, 800.00),
(4, 'Tablet', 5, 300.00),
(5, 'Phone', 2, 500.00);

Select * from Sales

--Find total revenue (Quantity × Price) for each product.

--Laptop 2400
--Phone 2500
--Tablet 1500

Select ProductName,SaleID, SUM(Quantity*Price) from Sales
group by ProductName, SaleID

Select * from Sales

--insert into Sales values (1, 'Laptop', 1, 500)

--Puzzle 2
CREATE TABLE EmployeeSalaries (
    EmpID INT PRIMARY KEY,
    EmpName VARCHAR(50),
    Department VARCHAR(50),
    Salary DECIMAL(10,2)
);

INSERT INTO EmployeeSalaries (EmpID, EmpName, Department, Salary) VALUES
(1, 'John', 'HR', 50000),
(2, 'Mary', 'IT', 70000),
(3, 'Steve', 'IT', 72000),
(4, 'Sara', 'Finance', 60000),
(5, 'Mike', 'HR', 55000);

Select * from EmployeeSalaries
--Find Average Salary per Department
--HR 1500
--Finance	1260
--IT 2560

Select Department, Avg(salary) Avgsalary from EmployeeSalaries
group by Department
