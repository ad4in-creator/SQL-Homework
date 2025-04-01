create database F24_class8

use F24_class8

create table Students (ID int, First_name varchar(30), age int)

insert into Students values (1, 'Farangiz', 20)
insert into Students values (2, 'Xasan', null)
insert into Students values (3, null, null)

insert into Students(ID) values (4)
insert into Students(ID, First_name) values (22, 'Mirjalol')

Select * from Students	--This shows all data in the table
Select ID, First_name, age from Students
Select age, ID, First_name from Students

--Comment This is a sentence
/*
Return the table
in any order
*/
Select * from Students

create table employees (ID int, name varchar(20), age int, salary int, dep varchar(20))

insert into employees values (1, 'Alex', 23, 1300, 'HR')
insert into employees values (2, 'Bob', 25, 1000, 'Sales')
insert into employees values (3, 'Charlie', 45, 1600, 'HR')
insert into employees values (4, 'George', 19, 800, 'Finance')
insert into employees values (5, 'Jane', 25, 1250, 'Sales')
insert into employees values (6, 'Aleksib', 36, 1520, 'Sales')
insert into employees values (7, 'Donk', 26, 1450, 'Sales')


Select * from employees

--Sum, avg, count, min, max
Select dep, SUM(Salary) as Total from employees
group by dep

Select dep, AVG(age) from employees
group by dep

Select name, AVG(age) from employees
group by name

Select AVG(salary) from employees
where dep = 'Sales'

Select * from employees

Select dep, MIN(age) as Min_age, MAX(salary) as Max_salary from employees
group by dep
order by Min_age desc, Max_salary desc

insert into employees values (8, 'John', 25, 1350, 'Accounting')

Select * from employees
Select MAX(salary) from employees

--Sales
--Salesmen

Create table salesmen (ID int, Name varchar(20), age int, years_exp int)
Create table Sales (Sale_id int, product_name varchar(20), quantity int, price int, salesman_id int)


-- Inserting 20 records into Salesmen
INSERT INTO Salesmen (ID, Name, Age, Years_Exp) VALUES
(1, 'John Doe', 35, 10),
(2, 'Alice Smith', 29, 5),
(3, 'Bob Johnson', 40, 15),
(4, 'Emma Brown', 28, 4),
(5, 'Michael White', 45, 20),
(6, 'Sophia Davis', 31, 7),
(7, 'James Wilson', 38, 12),
(8, 'Olivia Taylor', 27, 3),
(9, 'William Martin', 33, 9),
(10, 'Emily Anderson', 30, 6),
(11, 'Daniel Thomas', 36, 11),
(12, 'Charlotte Garcia', 26, 2),
(13, 'Henry Martinez', 41, 16),
(14, 'Amelia Hernandez', 32, 8),
(15, 'Benjamin Lopez', 39, 14),
(16, 'Mia Gonzalez', 25, 1),
(17, 'Alexander Lee', 34, 10),
(18, 'Harper Young', 29, 5),
(19, 'Ethan Scott', 37, 13),
(20, 'Isabella Adams', 28, 4);

-- Inserting 20 records into Sales
INSERT INTO Sales (Sale_ID, Product_Name, Quantity, Price, Salesman_ID) VALUES
(1, 'Laptop', 3, 900, 1),
(2, 'Smartphone', 5, 500, 2),
(3, 'Tablet', 2, 300, 3),
(4, 'Headphones', 7, 100, 4),
(5, 'Monitor', 4, 200, 5),
(6, 'Keyboard', 6, 50, 6),
(7, 'Mouse', 8, 30, 7),
(8, 'Printer', 2, 250, 8),
(9, 'Webcam', 3, 80, 9),
(10, 'Speaker', 5, 150, 10),
(11, 'Hard Drive', 4, 120, 11),
(12, 'SSD', 6, 180, 12),
(13, 'RAM', 7, 90, 13),
(14, 'Graphics Card', 3, 400, 14),
(15, 'Motherboard', 2, 350, 15),
(16, 'Power Supply', 5, 150, 16),
(17, 'Cooling Fan', 6, 40, 17),
(18, 'VR Headset', 2, 600, 18),
(19, 'Game Console', 4, 500, 19),
(20, 'Smartwatch', 3, 200, 20);
INSERT INTO Sales (Sale_ID, Product_Name, Quantity, Price, Salesman_ID) VALUES
(21, 'Laptop', 2, 950, 1),
(22, 'Smartphone', 4, 520, 2),
(23, 'Tablet', 3, 310, 3),
(24, 'Headphones', 6, 120, 4),
(25, 'Monitor', 5, 220, 5),
(26, 'Keyboard', 7, 55, 6),
(27, 'Mouse', 9, 35, 7),
(28, 'Printer', 3, 270, 8),
(29, 'Webcam', 2, 85, 9),
(30, 'Speaker', 6, 160, 10),
(31, 'Hard Drive', 5, 130, 11),
(32, 'SSD', 4, 190, 12),
(33, 'RAM', 8, 95, 13),
(34, 'Graphics Card', 4, 420, 14),
(35, 'Motherboard', 3, 360, 15),
(36, 'Power Supply', 6, 160, 16),
(37, 'Cooling Fan', 7, 45, 17),
(38, 'VR Headset', 3, 620, 18),
(39, 'Game Console', 5, 520, 19),
(40, 'Smartwatch', 4, 210, 20),
(41, 'Earbuds', 8, 80, 1),
(42, 'Gaming Mouse', 5, 70, 2),
(43, 'Wireless Charger', 7, 40, 3),
(44, 'Bluetooth Speaker', 4, 130, 4),
(45, '4K Monitor', 3, 500, 5),
(46, 'Gaming Keyboard', 6, 90, 6),
(47, 'External SSD', 5, 250, 7),
(48, 'Gaming Chair', 2, 300, 8),
(49, 'Mechanical Keyboard', 3, 120, 9),
(50, 'Portable Hard Drive', 4, 110, 10);

Select * from salesmen
Select * from sales

Select 
	Name, 
	SUM(price*quantity) as Total_sale 
from salesmen join Sales
on ID = salesman_id
Group by Name

--creating different sql objects
--aggregate functions
--joins
