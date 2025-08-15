# Stored-Procedures-and-Functions

**Objective:**
Learn to create reusable SQL blocks using Stored Procedures and Functions for modular and efficient database logic.

**Tool Used:**
MySQL Workbench

**Database Overview**

Database: company

Table: users → Stores user details including ID, name, gender, age, and salary.

**Queries Performed**

1️⃣ Creating a Stored Procedure – Get Users with Salary Above a Given Amount

DELIMITER $$

CREATE PROCEDURE GetHighSalaryUsers(IN min_salary INT)
BEGIN
    SELECT id, name, salary 
    FROM users 
    WHERE salary > min_salary;
END$$

DELIMITER ;

-- Call the procedure

CALL GetHighSalaryUsers(80000);

2️⃣ Creating a Function – Calculate Bonus Based on Salary

DELIMITER $$

CREATE FUNCTION CalculateBonus(salary INT)
RETURNS INT
DETERMINISTIC
BEGIN
    IF salary > 80000 THEN
        RETURN salary * 0.10;
    ELSE
        RETURN salary * 0.05;
    END IF;
END$$

DELIMITER ;

-- Using the function

SELECT name, salary, CalculateBonus(salary) AS Bonus FROM users;

**Key Learnings**

Stored Procedures allow storing reusable SQL logic that can take parameters.

Functions return a single value and can be used directly inside SELECT statements.

Modular SQL helps reduce repetition and makes code easier to maintain.
