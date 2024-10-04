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

### Basic Codes Used
``` SQL
CREATE TABLE Employees_Detail(
  employee_id INT PRIMARY KEY NOT NULL AUTO_INCREMENT,
  first_name TEXT,
  last_name TEXT,
  email_address TEXT,
  username varchar(50) DEFAULT NULL,
  employment_date DATE NULL);
```
