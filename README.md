# PAYROLL_DB

### Project Title : Employee Management and Analysis System
---
### Project Overview : The purpose of this project is to create a structured database for managing employee information, analyzing salary data, and processing employee payment method. The goal is to enable efficiet management of employee records, provide insights into workforce distribution and salary structure, and streamline the analysis process usogn SQL and Excel
---
### Scope :

- Employee Details : Stores basic employee details such as employee id, first name, last name, email address, username, and employment date.
- Salary Table : Contains salary nformation linked to each employee, along with deparment details.
- Payment Method Table : Maintains payment details like bank name and account number.
---
### Key Analysis Areas

1 Employee Data Management 
- Maintain comprehensive employee records.
- Ensure data integrity and consistency across tables.
  
2 Salary Analysis
- Determine salary distribution and trends
- Compare salaries by department
  
3 Payment Method Analysis
- Identify account number

### Tools Used
- SQL : For database creation, management, and analysis
- Excel : For data visualization, trend analysis, and insights through pivot table and charts.

### Expected Outcomes
- A queryable database for storing and retrieving employee data.
- Analytical report on salary distribution, employee demographics, and department insights.
- Visual represention of key metrics using Excel.

### Data Analysis
Basic Codes Used
``` SQL
CREATE TABLE Employees_Detail(
  employee_id INT PRIMARY KEY NOT NULL AUTO_INCREMENT,
  first_name TEXT,
  last_name TEXT,
  email_address TEXT,
  username varchar(50) DEFAULT NULL,
  employment_date DATE NULL);
INSERT INTO Employees_Detail(employee_id, first_name, last_name, email_address, username,employment_date)
 VALUES(1201, 'Oluwabusayo', 'Udogu', 'oluwabusayo.udogu@gmail.com', 'OLUUGO123', '2018-10-02'),
(1202, 'Alvin', 'Daniel', 'alvin.daniel@gmail.com', 'ALVDA521', '2014-03-02'),
(1203, 'Oluwafeyi', 'Udogu', 'oluwafeyi.udogu@gmail.com', 'OLUFE345', '2015-05-09'),
(1204, 'Grant', 'James',' grant.james@gmail.com', 'GRAJA864', '2015-10-02'),
(1205, 'Joseph', 'Ayodeji', 'joseph.ayodeji@gmail.com', 'JOAY431', '2016-06-02'),
(1206, 'Ruth', 'Paul', 'ruth.paul@gmail.com', 'RUPA247', '2018-10-10'),
(1207, 'Femi', 'Idowu', 'femi.idowu@gmail.com', 'FEID532', '2015-03-02'),
(1208, 'Ojay', 'Shaun', 'ojay.shaun@gmail.com', 'SHAOJ894', '2015-09-02'),
(1209, 'Helen', 'George',' helen.george@gmail.com', 'HEGEO643', '2015-10-02'),
(1210, 'Dune', 'Drake', 'dune.drake@gmail.com', 'DUDRA945', '2017-07-04');
  

SELECT * FROM Employees_Detail;

-- Select firstname that begins with 'O'

SELECT first_name FROM Employees_Detail WHERE 
  first_name LIKE ("O%");

==Select first name that ends with 'i'

SELECT first_name FROM Employees_Detail WHERE 
  first_name LIKE ("%i");

--Salary Table--

CREATE TABLE Salary(
id INT AUTO_INCREMENT PRIMARY KEY,
employee_id INT,
FOREIGN KEY (employee_id)REFERENCES Employees_Detail(employee_id),
department TEXT, salary DECIMAL (10, 3));

INSERT INTO Salary (employee_id, department,salary.Salary)
VALUES(1201,'it','45000.467'),
(1202, 'hr', '30000.978'),
(1203, 'operation', '25000.12'),
(1204, 'customer care', '20000.967'),
(1205, 'it', '45000.467'),
(1206, 'hr', '30000.97'),
(1207, 'it', '45000.467'),
(1208, 'operation', '25000.123'),
(1209, 'operation', '25000.123'),
(1210, 'it', '45000.467');

SELECT* FROM Salary;

--IN Clause  

SELECT salary, department FROM Salary
WHERE department IN ('it','hr');

SELECT salary, first_name, last_name
 FROM Employees_Detail
 INNER JOIN Salary
 ON Employees_Detail.employee_id = Salary.employee_id;
 
 SELECT SUM(salary) FROM Salary;
 
 SELECT DISTINCT(department) FROM Salary;

--Payment_Method Table--
 
 CREATE TABLE payment_method 
  (id INT AUTO_INCREMENT, FOREIGN KEY (id) REFERENCES Salary(id),
  bank VARCHAR (255) DEFAULT 'zenith bank', account_number BIGINT);
  
  INSERT INTO payment_method(account_number)
  VALUES( 1297452835),
  (8745379263),
  (7562740256),
  ( 5638209456),
  (5789234510),
  ( 5683219456),
  (9563420127),
  (5638193452),
  (8452814795),
  (5638941286);
  
  SELECT * FROM payment_method;
--Two tables join

SELECT salary, department,account_number
 FROM Salary
 INNER JOIN payment_method
 ON Salary.id = payment_method.id ORDER BY department ASC;

-- Three tables Join
SELECT a.first_name, a.last_name, b.salary, c.account_number FROM
Employees_Detail AS a 
INNER JOIN Salary AS b ON a.employee_id = b.employee_id
INNER JOIN payment_method AS c ON b.id = c.id;

-- Calculate 5% of Salary as bonus--

SELECT salary, 
    (salary * 0.05) AS bonus 
FROM Salary;

--Calculate total salary by department--

SELECT SUM(salary),
  department FROM SALARY
GROUP BY department;

--Average salary--

SELECT AVG(salary), 
  department FROM SALARY 
GROUP BY department;

```
