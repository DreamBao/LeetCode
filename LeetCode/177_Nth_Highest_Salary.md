# 177. Nth Highest Salary
Nth Highest Salary

## Code
    CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
    BEGIN
        set N=N-1;
    RETURN (
        # Write your MySQL query statement below.
        # need repeat
        select distinct Salary from Employee order by Salary desc limit N,1
        
    );
    END