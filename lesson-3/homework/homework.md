bulk Products
from 'C:\path\to\your\file.txt'
with (
    fieldterminator = ',',  -- Define the delimiter between fields (e.g., comma for CSV)
    rowterminator = '\n',   -- Define the delimiter between rows (new line for CSV)
    firstrow = 2           -- If your file contains headers, start from the second row
);
alter table Products
add constraint FK_Products_Categories
foreighn key (CategoryID)
references Categories(CategoryID);
create table Employees (
    EmployeeID int primary key,
        EmployeeEmail varchar(100) unique,
    EmployeeName varchar(100)
);
alter table Products
add constraint ck_Price_Positive
check (Price > 0);
alter table Products
add Stock int not null;
select ProductID, isnull(Price, 0) as Price
from Products;
alter table Products
add constraint fk_Products_Categories
foreighn key (CategoryID)
references Categories(CategoryID)
on delete casedate
on update casedate;

