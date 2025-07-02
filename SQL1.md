# MySQL---Window-Functions

-- Create a table emp:

CREATE TABLE emp (
    emp_id INT PRIMARY KEY,           -- Unique employee ID
    first_name VARCHAR(50),          -- Employee's first name
    last_name VARCHAR(50),           -- Employee's last name
    department VARCHAR(50),          -- Department name
    position VARCHAR(50),            -- Job title or position
    hire_date DATE,                  -- Date of hiring
    salary DECIMAL(10, 2),           -- Monthly salary
    email VARCHAR(100),              -- Contact email
    phone VARCHAR(15)                -- Contact phone number
);


-- Insert values to the emp table:

INSERT INTO emp (emp_id, first_name, last_name, department, position, hire_date, salary, email, phone) VALUES
(1, 'Amit', 'Sharma', 'Sales', 'Sales Executive', '2020-03-15', 45000.00, 'amit.sharma@example.com', '9876543210'),
(2, 'Priya', 'Verma', 'HR', 'HR Manager', '2019-07-01', 60000.00, 'priya.verma@example.com', '9876543211'),
(3, 'Rahul', 'Singh', 'IT', 'Software Engineer', '2021-01-10', 75000.00, 'rahul.singh@example.com', '9876543212'),
(4, 'Sneha', 'Patel', 'Finance', 'Accountant', '2018-11-20', 55000.00, 'sneha.patel@example.com', '9876543213'),
(5, 'Vikram', 'Rao', 'Marketing', 'Marketing Analyst', '2022-05-05', 48000.00, 'vikram.rao@example.com', '9876543214'),
(6, 'Neha', 'Jain', 'IT', 'System Administrator', '2020-08-25', 70000.00, 'neha.jain@example.com', '9876543215'),
(7, 'Karan', 'Mehta', 'Sales', 'Sales Manager', '2017-04-18', 65000.00, 'karan.mehta@example.com', '9876543216'),
(8, 'Divya', 'Kapoor', 'HR', 'Recruiter', '2023-02-12', 40000.00, 'divya.kapoor@example.com', '9876543217'),
(9, 'Ankit', 'Gupta', 'Finance', 'Financial Analyst', '2021-09-30', 58000.00, 'ankit.gupta@example.com', '9876543218'),
(10, 'Riya', 'Sen', 'Marketing', 'Content Strategist', '2022-12-01', 47000.00, 'riya.sen@example.com', '9876543219');


-- Finding the nth highest salary by department

-- WITH CTE AS (
-- SELECT 
--     CONCAT(first_name, " ", last_name) AS name,
--     department, 
--     salary,
--     row_number() over(partition by department ORDER BY salary DESC) as sal_rank
-- FROM emp)
-- SELECT * FROM CTE
-- WHERE sal_rank = 1 ;

-- Finding the nth next salary, previous salary

-- WITH CTE AS (
-- SELECT 
--     CONCAT(first_name, " ", last_name) AS name,
--     department, 
--     salary,
--     LEAD(salary) over(ORDER BY salary DESC) as next_sal,
--     LAG(salary)  over(ORDER BY salary DESC) as previous_sal
-- FROM emp
-- );


-- Removing Duplicate Rows:

-- INSERT INTO emp (emp_id, first_name, last_name, department, position, hire_date, salary, email, phone) VALUES
-- (11, 'Amit', 'Sharma', 'Sales', 'Sales Executive', '2020-03-15', 45000.00, 'amit.sharma@example.com', '9876543210'),
-- (12, 'Priya', 'Verma', 'HR', 'HR Manager', '2019-07-01', 60000.00, 'priya.verma@example.com', '9876543211');

-- WITH CTE AS (
-- SELECT *, 
--     row_number() over(partition by first_name,last_name,department,salary ORDER BY emp_id ASC) as rn
-- FROM emp)

-- DELETE FROM emp WHERE emp_id IN
--     (SELECT emp_id 
--      FROM CTE 
--      WHERE rn > 1) 
-- ;

-- SELECT * FROM emp
