
--Puzzle 1
--Question: If all the columns have zero values, 
--then don’t show that row. In this case, we have to remove the 5th row while selecting data.

--### Table Schema:
CREATE TABLE TestMultipleZero (
    A INT NULL,
    B INT NULL,
    C INT NULL,
    D INT NULL
);

--### Sample Data:
INSERT INTO TestMultipleZero(A,B,C,D)
VALUES 
    (0,0,0,1),
    (0,0,1,0),
    (0,1,0,0),
    (1,0,0,0),
    (0,0,0,0),
    (1,1,1,0);

Select * from TestMultipleZero

select top 5 * from TestMultipleZero order by A desc, B desc, C desc, D desc

select * from TestMultipleZero
where  A != 0 or B != 0 or C != 0 or D != 0

SELECT *
FROM TestMultipleZero
WHERE NOT (A = 0 AND B = 0 AND C = 0 AND D = 0);

select * from TestMultipleZero
where  A != 0 and B != 0 and C != 0 and D != 0

INSERT INTO TestMultipleZero(A,B,C,D)
VALUES 
    (4,3,2,1)

Select * from TestMultipleZero
where (A + B + C + D)>0

--Puzzle 2
CREATE TABLE InputTbl (
    col1 VARCHAR(10),
    col2 VARCHAR(10)
);
    INSERT INTO InputTbl (col1, col2) VALUES 
('a', 'b'),
('a', 'b'),
('b', 'a'),
('c', 'd'),
('c', 'd'),
('m', 'n'),
('n', 'm');

Select * from InputTbl

--a b
--c d
--m n

Select case when 'a' < 'ab' then 'a' else 'b' end  --, case when 'a' > 'b' then 'a' else 'b' end

Select distinct case when col1 < col2 then col1 else col2 end, case when col1 > col2 then col1 else col2 end
from InputTbl

SELECT col1, col2
FROM InputTbl 
WHERE col1 < col2  
UNION  
SELECT col2, col1
FROM InputTbl
WHERE col2 < col1;

delete from InputTbl
where col1 ='m'

Select * from InputTbl

select least(col1, col2) as first_col, greatest(col1, col2) as second_col from InputTbl

create table InputTbl2 (col1 VARCHAR(10),
    col2 VARCHAR(10), col3 varchar(10))
 INSERT INTO InputTbl2 (col1, col2, col3) VALUES 
('a', 'b', 'c'),
('a', 'b', 'c'),
('a', 'b', 'b'),
('a', 'b', 'a'),
('a', 'a', 'c')

Select * from InputTbl2
--Puzzle 3 Find those with odd ids

create table section1(id int, name varchar(20))
insert into section1 values (1, 'Been'),
       (10, 'Abbos'),
       (3, 'Steven'),
       (4, 'Paulo'),
       (5, 'Genryh'),
       (6, 'Bruno'),
       (7, 'Fred'),
       (8, 'Andro')

Select * from section1
where id % 2 = 0

Select 12%2
Select 13%5

--## Puzzle 4: Person with the smallest id (use the table in puzzle 3)
Select top 1 * from section1 order by id asc
---

--## Puzzle 5: Person with the highest id (use the table in puzzle 3)
Select top 1 * from section1 order by id desc
---

--Puzzle 6: People whose name starts with b (use the table in puzzle 3)
Select * from section1
where name like 'B%'

--Puzle 7: Write a query to return only the rows where the code contains the literal underscore _ (not as a wildcard).

CREATE TABLE ProductCodes (
    Code VARCHAR(20)
);

INSERT INTO ProductCodes (Code) VALUES
('X_%23'),
('X_456'),
('X#789'),
('X-001'),
('X%202'),
('X_ABC'),
('X#DEF'),
('X-999');

Select * from ProductCodes
where Code like '%1_1%%' escape '1'

Select * from ProductCodes
where Code like '%[_]%'
