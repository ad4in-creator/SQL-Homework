create database [F24_class5]
use [F24_class5]

--1. Aliases

Select 'Hello World' as Description

Select 'Hello World' Description

Select BusinessEntityID as ID, JobTitle from [AdventureWorks2022].[HumanResources].[Employee]

Select COUNT(1234) as Functions

--Select * from Table1 as t1 join Table1 as t2  --We will come back this in lesson 8, 9

--Cte
/*with cte as (statement) Select * from cte*/

--2. UNION and UNION ALL

Select 1, 2, 3
union
Select 2, 3, 4

Select 'a'
union
Select 2
union
Select 'a'

create table Numbers1 (num int)
create table Numbers2 (num int)
truncate table Numbers1
insert into Numbers1 values (1), (2), (3), (4)
insert into Numbers2 values (5), (6), (3), (4)

Select * from Numbers1
union
Select * from Numbers2

Select num from Numbers1
union all
Select * from Numbers2

--Select * from Numbers4

Select BusinessEntityID as ID, JobTitle into Test1 from [AdventureWorks2022].[HumanResources].[Employee]
Select BusinessEntityID as ID, JobTitle into Test2 from [AdventureWorks2022].[HumanResources].[Employee]

Select * from Test1
union
Select * from Test2

Update Test1
Set ID = 1 where ID <= 3

--3. INTERSECT and EXCEPT

Select * from Numbers1
intersect
Select * from Numbers2

Select * from Numbers1
except
Select * from Numbers2
union
Select * from Numbers2

--4. CASE

--case 
--	when condition1 then value
--	when condition2 then value
--else value
--end

-- Case in select
Select case when 12 > 10 then 'Yes it is correct' else 'No, you are not smart' end

Select case when 14 % 2 = 0 then 'even' else 'odd' end

declare @number int = 19;

Select case when @number % 2 = 0 then 'even' else 'odd' end
--case in where
create table employees (id int, departmentName varchar(20), salary int)
       insert into employees values (1, 'IT', 2000), (2, 'HR', 3000), (3, 'Marketing', 16000),             (4, 'IT', 45000), (5, 'HR', 67000), (6, 'IT', 65000)
Select * from employees

Select *, case when salary > 10000 then 'Senior' else 'Junior' end as Title from employees

Select 
	*
from employees
where case	
		when departmentName = 'HR' and salary > 50000 then 1
		when departmentName = 'IT' and salary > 60000 then 1
		when salary < 40000 then 0
		else 0.5
	end in ('rich', 'superRich')

	drop table employees
CREATE TABLE Employees ( EmployeeID INT PRIMARY KEY, FirstName VARCHAR(50) NULL, LastName VARCHAR(50) NULL, DepartmentName VARCHAR(50), Salary DECIMAL(10, 2), HireDate DATE, Age INT, Email VARCHAR(100) NULL, Country VARCHAR(50) );

INSERT INTO Employees (EmployeeID, FirstName, LastName, DepartmentName, Salary, HireDate, Age, Email, Country) VALUES (1, 'John', 'Doe', 'IT', 55000.00, '2020-01-01', 30, 'johndoe@example.com', 'USA'), (2, 'Jane', 'Smith', 'HR', 65000.00, '2019-03-15', 28, 'janesmith@example.com', 'USA'), (3, NULL, 'Johnson', 'Finance', 45000.00, '2021-05-10', 25, NULL, 'Canada'), (4, 'James', 'Brown', 'Marketing', 60000.00, '2018-07-22', 35, 'jamesbrown@example.com', 'UK'), (5, 'Patricia', NULL, 'HR', 70000.00, '2017-08-30', 40, NULL, 'USA'), (6, 'Michael', 'Miller', 'IT', 75000.00, '2020-12-12', 27, 'michaelm@example.com', 'Germany'), (7, 'Linda', NULL, 'Finance', 48000.00, '2016-11-02', 42, NULL, 'Canada'), (8, 'David', 'Moore', 'Marketing', 85000.00, '2021-09-01', 29, 'davidm@example.com', 'UK'), (9, 'Elizabeth', 'Taylor', 'HR', 60000.00, '2019-05-18', 31, 'elizabetht@example.com', 'USA'), (10, 'William', NULL, 'IT', 64000.00, '2020-04-10', 26, NULL, 'Germany'), (11, NULL, 'Thomas', 'Finance', 47000.00, '2017-01-25', 38, NULL, 'Canada'), (12, 'Joseph', 'Jackson', 'Marketing', 78000.00, '2016-09-30', 44, 'josephj@example.com', 'UK'), (13, 'Karen', 'White', 'HR', 59000.00, '2018-06-10', 33, 'karenw@example.com', 'USA'), (14, 'Steven', NULL, 'IT', 71000.00, '2021-07-15', 24, NULL, 'Germany'), (15, 'Nancy', 'Clark', 'Finance', 45000.00, '2020-02-20', 27, 'nancyc@example.com', 'Canada'), (16, 'George', 'Lewis', 'Marketing', 80000.00, '2019-11-10', 36, 'georgel@example.com', 'UK'), (17, 'Betty', NULL, 'HR', 55000.00, '2017-04-05', 41, NULL, 'USA'), (18, 'Samuel', 'Walker', 'IT', 72000.00, '2021-03-22', 23, 'samuelw@example.com', 'Germany'), (19, 'Helen', 'Hall', 'Finance', 49000.00, '2018-10-16', 34, 'helenh@example.com', 'Canada'), (20, NULL, 'Allen', 'Marketing', 90000.00, '2015-08-11', 50, NULL, 'UK'), (21, 'Betty', 'Young', 'HR', 53000.00, '2020-05-17', 28, 'bettyy@example.com', 'USA'), (22, 'Frank', NULL, 'IT', 67000.00, '2021-02-02', 26, 'frankk@example.com', 'Germany'), (23, 'Deborah', 'Scott', 'Finance', 47000.00, '2019-07-09', 29, NULL, 'Canada'), (24, 'Matthew', 'Green', 'Marketing', 76000.00, '2021-01-15', 30, 'matthewg@example.com', 'UK'), (25, NULL, 'Adams', 'HR', 54000.00, '2020-06-21', 27, NULL, 'USA'), (26, 'Paul', 'Nelson', 'IT', 71000.00, '2018-12-03', 37, 'pauln@example.com', 'Germany'), (27, 'Margaret', NULL, 'Finance', 46000.00, '2020-08-19', 25, 'margaretc@example.com', 'Canada'), (28, 'Anthony', 'Mitchell', 'Marketing', 82000.00, '2021-04-10', 29, NULL, 'UK'), (29, 'Lisa', 'Perez', 'HR', 60000.00, '2021-03-05', 24, 'lisap@example.com', 'USA'), (30, NULL, 'Roberts', 'IT', 69000.00, '2019-09-24', 32, NULL, 'Germany'), (31, 'Jessica', 'Gonzalez', 'Finance', 47000.00, '2017-12-13', 38, 'jessicag@example.com', 'Canada'), (32, 'Brian', NULL, 'Marketing', 85000.00, '2018-11-05', 35, NULL, 'UK'), (33, 'Dorothy', 'Evans', 'HR', 59000.00, '2019-06-11', 31, 'dorothye@example.com', 'USA'), (34, 'Matthew', 'Carter', 'IT', 70000.00, '2020-01-29', 29, 'matthewc@example.com', 'Germany'), (35, NULL, 'Martinez', 'Finance', 51000.00, '2021-06-06', 22, NULL, 'Canada'), (36, 'Daniel', 'Perez', 'Marketing', 83000.00, '2021-07-01', 30, 'danielp@example.com', 'UK'), (37, 'Catherine', 'Roberts', 'HR', 60000.00, '2020-09-19', 27, 'catheriner@example.com', 'USA'), (38, 'Ronald', NULL, 'IT', 68000.00, '2017-02-04', 39, NULL, 'Germany'), (39, 'Angela', 'Jenkins', 'Finance', 52000.00, '2018-04-23', 34, 'angelaj@example.com', 'Canada'), (40, 'Gary', 'Wright', 'Marketing', 87000.00, '2021-01-10', 29, NULL, 'UK');

Select * from Employees
order by DepartmentName asc

Select *
from Employees
order by case 
		when DepartmentName = 'IT' then 1
		else 0
	end desc, Salary desc

--5. IIF

IIF(boolean_expression, true_value, false_value)

Select IIF(13>8, 'Yes', 'No')
Select IIF(13=8, 'Yes', 'No')

Select IIF(13=8, 'Yes', iif(13=10, 'Finally yes', 'Unfortunately'))

Select *
from Employees
order by IIF(departmentname = 'IT', 1, 0) desc, Salary desc

--6. IF

if 10 > 20 select 'London'
else select 'United'

declare @StudentMark int = 85

if @StudentMark >= 90 select 'congratulations'
else if @StudentMark >= 80 select 'You are good'
else select 'you failed' ;

declare @StudentMark int = 92

if @StudentMark >= 90 insert into Numbers1 values (@StudentMark)
else if @StudentMark >= 80 select 'You are good'
else select 'you failed'

Select * from Numbers1

--IF (Expression)
--                    BEGIN
--                    -- If the condition is TRUE then execute the following statement
--                    True Statements;
--                    END
--ELSE if
--                   BEGIN
--                   -- If the condition is False then execute the following statement
--                   False Statements
--END

--7. While

--while condition
--begin
--   statement
--end

declare @Counter int 
Set @Counter = 1
While @Counter <= 10
begin
	 Select @Counter as Number
	 --insert into Numbers1 values (@Counter)
	 Set @Counter = @Counter + 1
end

Select * from Numbers1

--Endless loop

declare @Counter int 
Set @Counter = 12
While (@Counter %2 = 0 or @Counter %3 = 0) or @Counter <60
begin
	 Select @Counter as Number
	 insert into Numbers1 values (@Counter)
	 set @Counter = @Counter + 1
end

Select * from Numbers1

create table numbers (number int)

insert into numbers values
(1),(2),(3),(4),(5),(6),(7),(8),(9),(10),(11),(12),(13),(14),(15),(16),(17),(18),(19),(20),(21),(22),(23),(24),(25),(26),(27),(28),(29),(30),(31),(32),(33),(34),(35),(36),(37),(38),(39),(40),(41),(42),(43),(44),(45),(46),(47),(48),(49),(50),(51),(52),(53),(54),(55),(56),(57),(58),(59),(60),(61),(62),(63),(64),(65),(66),(67),(68),(69),(70),(71),(72),(73),(74),(75),(76),(77),(78),(79),(80),(81),(82),(83),(84),(85),(86),(87),(88),(89),(90),(91),(92),(93),(94),(95),(96),(97),(98),(99),(100)

Select * from numbers
3 ga bo'linsa Fizz
5 ga bo'linsa Buzz
15 ga bo'linsa FizzBuzz deb chiqsin
else nothing
drop table test2
create table test2 (col1 int, col2 int, col3 int)

insert into test2 values (40, 30, 60), (20, 15, 42), (50, 33, 23), (25, 40, 35)
select * from test2

60
42
50
40

