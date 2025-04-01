
create table identitytest (id int identity, name varchar(50))
insert into identitytest values ('alex')

Select * from identitytest
insert into identitytest values ('bob')

create table identitytest2 (id int identity(100, 10), name varchar(50))
insert into identitytest2 values ('alex')
Select * from identitytest2

--insert into identitytest2 values (140, 'alex')

delete from identitytest2 where id = 120
insert into identitytest2 values ('aleksib')

--search how to turn off identity

--delete vs truncate
select * from identitytest2

delete from identitytest2

insert into identitytest2 values('Kane')

truncate table identitytest2

Select * from identitytest2

insert into identitytest2 values('Kane')


--2. Not null

create table notnull(id int not null, name varchar(20))
insert into notnull values (1, 'a')
insert into notnull values (-23, 'b')
insert into notnull values (12, 'c')
insert into notnull values (0, 'd')

Select * from notnull

insert into notnull values (null, 'd')

insert into notnull(name) values ('d')
insert into notnull values (' ', 'd')
insert into notnull values (12, ' ')

Select * from notnull

--changing existing table column to null
Alter table notnull
Alter column id int null

insert into notnull values (null, 13)

Alter table notnull
Alter column id int not null

delete from notnull
where id is null

Select * from notnull

delete from notnull
where id = 1000000

insert into notnull values (null, 'Lily')

update notnull
set id = 0
where id is null

--3. Unique

create table uniquetest (id int unique, name varchar(20))

Select * from uniquetest

insert into uniquetest values(1, 'Nathen')
insert into uniquetest values(2, 'Bobby')
insert into uniquetest values(3, 'Fischer')
insert into uniquetest values(3, 'Alex') --this throws an error

insert into uniquetest values(4, 'Fischer')

Alter table uniquetest
add constraint Uk_name unique(name)

delete from uniquetest
where id = 4

Select * from uniquetest

insert into uniquetest 
values (4, null)

delete from uniquetest
where id is null

--composite unique
create table Fullname 
(firstname varchar(50), lastname varchar(50), constraint Uk_fullname unique(firstname, lastname))

Select * from Fullname

insert into Fullname values ('Abdumannof', 'Tursunov')
insert into Fullname values ('Abdumannof', 'Zokirov')
insert into Fullname values ('Abdumannof', 'Nuriddinov')
insert into Fullname values ('Saidbek', 'Tursunov')

insert into Fullname values ('Abdumannof', 'Abdumannof')

Alter table Fullname
add constraint Uk_firstname unique(firstname)

truncate table Fullname

alter table Fullname
drop constraint [Uk_firstname]

--4. Primary key ------ unique + not null

create table Primarykey (id int primary key, name varchar(50))
Select * from Primarykey

insert into Primarykey values (1, 'Eriksen')
insert into Primarykey values (2, null)
insert into Primarykey values (3, 'Rocket')
insert into Primarykey values (2, 'John') --this throws an error

--unique vs primary key

Alter table Primarykey
add constraint pk_full primary key (id, name)

Alter table Primarykey
drop constraint [PK__Primaryk__3213E83FBD164A98]

Update Primarykey
set name = 'noname'
where name is null

Alter table Primarykey
Alter column name varchar(50) not null

Select * from Primarykey

insert into Primarykey
values (3, 'Nick')

insert into Primarykey
values (4, 'Nick')


--5. Foreign key

create table department (id int primary key, name varchar(50))
insert into department values (1, 'HR')
insert into department values (2, 'Sales')
insert into department values (4, 'Finance')

Select * from department

create table employees 
(empID int, name varchar(50), departmentID int, 
constraint Fk_todepid foreign key(departmentID) references department(id))

Select * from department
Select * from employees

insert into employees values (100, 'Alex', 1)
insert into employees values (101, 'Charlie', 4)
insert into employees values (102, 'George', 4)

alter table employees
alter column empid int not null

alter table employees
add constraint Empid primary key (empID)
create table sales (saleid int, empID int foreign key references employees(empID))

Select * from department
Select * from employees
Select * from sales

insert into sales values (1, 100)
insert into sales values (2, 102)
insert into sales values (3, 100)

insert into sales values (4, 103)

--default
--check
--update cascade and delete cascade
