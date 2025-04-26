1.
select s2.StudentID, s2.FullName, s2.Grade+isnull(s1.Grade,0) SumGrade from Students s1 right join Students s2 on s1.StudentID=s2.StudentID-1;
2.
select e3.EmployeeID, e3.ManagerID, e3.JobTitle,
case when floor((isnull(e1.ManagerID,0) + isnull(e2.ManagerID,0) + isnull(e3.ManagerID,0))/3) < 333
then 0
when floor((isnull(e1.ManagerID,0) + isnull(e2.ManagerID,0) + isnull(e3.ManagerID,0))/3) < 1001
then 1
else 2
end Depth
from Employee e1 right join Employee e2 on e1.EmployeeID=e2.ManagerID right join Employee e3 on e2.EmployeeID=e3.ManagerID;
3.
  I know the solution is wrong, but heres something than nothing:
with cte as (
select
SUBSTRING(Equation,1,1) a,
SUBSTRING(Equation,2,1) b ,
SUBSTRING(Equation,3,1) c,
SUBSTRING(Equation,4,1) d,
SUBSTRING(Equation,5,1) e
from Equations
)
select *, isnull(char(ascii(a)),'')+isnull(char(ascii(b)),'')+isnull(char(ascii(c)),'')+isnull(char(ascii(d)),'')+isnull(char(ascii(e)),'') from cte
4.
select * from Student
select s1.StudentName, s2.StudentName, s1.Birthday from Student s1 join Student s2 on s1.Birthday=s2.Birthday and s1.StudentName>s2.StudentName;
5.
select p1.PlayerA, p1.PlayerB, p1.Score+p2.Score totalscore from PlayerScores p1 join PlayerScores p2 on p1.PlayerA=p2.PlayerB and p1.Score>p2.Score
6.
select employee_ID, hire_date, case 
when datediff(YEAR, HIRE_DATE, GETDATE()) < 1 then 'New Hire'
when datediff(YEAR, HIRE_DATE, GETDATE()) between 1 and 4 then 'Junior'
when datediff(YEAR, HIRE_DATE, GETDATE()) between 5 and 9 then 'Mid-Level'
when datediff(YEAR, HIRE_DATE, GETDATE()) between 10 and 19 then 'Senior' else 'Veteran'
end as Employment_Stage from Employees;
7. 
select e.* from Employees e join (select departmen_ID, AVG(salary) as avg_salary from Employees group by department_ID) dept_avg on e.department_ID = dept_avg.department_ID where e.salary > dept_avg.avg_salary;
8.
select * from Employees where (lower(first_name) || lower(last_name)) like '%a%' and salary % 5 = 0;
9.
select department_ID, count(*) as total_employees, SUM(case where datediff(year, hire_date, getdate()) > 3 then 1 else 0 end) as over_3_years, round(100.0 * SUM(CASE WHEN DATEDIFF(YEAR, HIRE_DATE, GETDATE()) > 3 THEN 1 ELSE 0 END) / COUNT(*), 2) as percent_over_3_years from Employees group by department_ID;
10.
select * from (select job_description, spaceman_ID, hire_date,
rank() over (partition by job_description order by hiire_date ASC) as most_experienced,
rank() over (partition by job_description order by hire_date DESC) as least_experienced from Personal) ranked where most_experienced = 1 or least_experienced = 1;






