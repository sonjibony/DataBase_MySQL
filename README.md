# Data_Base

### Create a table name Employee 
      CREATE TABLE EMPLOYEE (
    EMPLOYEE_ID int,
    LAST_NAME varchar(255),
    FIRST_NAME varchar(255),
    MIDDLE_NAME varchar(255),
    JOB_ID INT,
    MANAGER_ID INT,
    HIRE_DATE DATETIME,
    SALARY INT,
    COMM INT,
    DEPARTMENT_ID INT,
    PRIMARY KEY (EMPLOYEE_ID),
    FOREIGN KEY (JOB_ID) REFERENCES JOB(JOB_ID),
    FOREIGN KEY (DEPARTMENT_ID) REFERENCES DEPARTMENT(DEPARTMENT_ID)
    );

     INSERT INTO EMPLOYEE VALUES
	  (7369, 'SMITH', 'JOHN', 'Q', 667, 7902, '17-Dec-84', 800, NULL, 20),
    (7499, 'ALLEN', 'KEVIN', 'J', 670, 7698, '20-Feb-85', 1600, 300, 30),
    (7505, 'DOYLE', 'JEAN', 'K', 671, 7839, '4-Apr-85', 2850, NULL, 30),
    (7506, 'DENNIS', 'LYNN', 'S', 671, 7839, '15-May-85', 2750, NULL, 30),
    (7507, 'BAKER', 'LESLIE', 'D', 671, 7839, '10-Jun-85', 2200, NULL, 40),
    (7521, 'WARK', 'CYNTHIA', 'D', 670, 7698, '22-Feb-85', 1250, NULL, 40);

#### Fetch all columns from the Employee table:
      SELECT * from EMPLOYEE;
![image](https://github.com/user-attachments/assets/9ce2ded3-5c25-470f-b9ad-b55188c28bfa)


#### Fetch last_name, first_name, salary of Employee
      SELECT last_name, first_name, salary
       FROM EMPLOYEE;
![image](https://github.com/user-attachments/assets/42dd43fa-e97a-4d78-a4b2-d1bdb01bb302)


#### Fetch all different/distinct JOB_Id of the Employee table
      SELECT DISTINCT job_id from EMPLOYEE;
![image](https://github.com/user-attachments/assets/b26d7433-f346-4af8-adcd-1d21574d74b1)


#### Fetch the details of David's employee from Employee.
      SELECT * FROM Employee WHERE name='David'
![image](https://github.com/user-attachments/assets/de3074da-a3ae-4f76-8c2d-271dc7bb352a)

#### Fetch details of employees that their salary is neither '800' nor '1250'.
      SELECT * FROM Employee 
      WHERE salary != 800
      AND salary != 1250
![image](https://github.com/user-attachments/assets/989cc491-2909-433e-9931-0cdd343f28e5)

#### Fetch names of employees that start with a 'D' or end with an 'N'
      SELECT * FROM Employee 
      WHERE last_name LIKE 'D%'
      OR  last_name LIKE '%N'
![image](https://github.com/user-attachments/assets/da347cc0-0cc5-4848-b694-3c4c9bddec03)

#### Fetch names of employers that have a salary between 800 and 1500.
      SELECT first_name,last_name 
      FROM Employee 
      WHERE salary 
      BETWEEN 800 and 1500;
![image](https://github.com/user-attachments/assets/04968645-bce4-4258-9194-3cca898e29db)

#### Fetch job_id, and manager_id sorted by the manager_id column in the default ascending order:
      SELECT job_id, manager_id from EMPLOYEE ORDER by manager_id ASC
![image](https://github.com/user-attachments/assets/af833775-09b8-44eb-bb51-2a96ea586491)
  
#### Fetch data of Employees from the first 3.
       SELECT * from EMPLOYEE LIMIT 3
![image](https://github.com/user-attachments/assets/1e68b44f-7c7b-46ae-9b59-4b87fb0fb027)

#### Find out the Highest and Lowest salary from employees
        SELECT MAX(salary) AS HighestSalary,
        MIN (Salary) AS LowestSaraly
        from EMPLOYEE
![image](https://github.com/user-attachments/assets/f033b62c-1210-477a-99f3-c63fd7a3eff6)

#### Find out the 2nd Highest salary from employees
      SELECT MAX(salary) As secondHigh
      from EMPLOYEE
      WHERE salary < (SELECT MAX(salary) FROM EMPLOYEE)
![image](https://github.com/user-attachments/assets/ddf09720-5a78-4066-b9ea-27ab854b3f46)

#### Find out the number of employees:
      SELECT COUNT(*)
      from EMPLOYEE;
![image](https://github.com/user-attachments/assets/44632a13-daa0-4696-a769-bab751a76601)


## DB_Table-1:Customers
![image](https://github.com/user-attachments/assets/04a2725c-9046-4f9e-ad3a-8610d66d771d)

## DB_Table-2:Suppliers
![image](https://github.com/user-attachments/assets/b0250d90-9bf6-438d-9ae0-4500c0ef7d5a)

#### Fetch the cities from both the "Customers" and the "Suppliers" table:
    SELECT City FROM Customers
    UNION ALL
    SELECT City FROM Suppliers
    ORDER BY City;
![image](https://github.com/user-attachments/assets/a5e49927-c6fb-4f1d-a601-97c7ee5ae0ca)

#### Lists all customers and suppliers in a one table
      SELECT 'Customer' AS Type, ContactName, City, Country
      FROM Customers
      UNION
      SELECT 'Supplier', ContactName, City, Country
      FROM Suppliers
![image](https://github.com/user-attachments/assets/2a5797e1-b726-422f-8702-4da617432513)

#### Lists the number of customers in each country.
    SELECT COUNT(CustomerID), Country
    FROM Customers
    GROUP BY Country;
![image](https://github.com/user-attachments/assets/80e1020e-302b-45ec-a151-2b9ee8c25156)

#### Lists the number of customers in each country, sorted high to low.
      SELECT COUNT(CustomerID), Country 
      FROM Customers 
      GROUP BY Country 
      ORDER BY COUNT(CustomerID) DESC
![image](https://github.com/user-attachments/assets/21dba029-0c2d-4255-8075-b90d3dae0476)

#### Lists the number of customers in each country. Only include countries with more than 5 customers.
      SELECT COUNT(CustomerID), Country 
      FROM Customers 
      GROUP BY Country 
      HAVING COUNT(CustomerID) > 5;
![image](https://github.com/user-attachments/assets/800aac6b-b750-4347-8f75-3aabf5cbda56)

## DB_Table-1:Orders
![image](https://github.com/user-attachments/assets/9ba3fc84-e062-4aed-8f6d-2cb967a9054c)
## DB_Table-2:Customers
![image](https://github.com/user-attachments/assets/87111c5d-cbbb-464c-944f-2bd8591fddf4)

#### Fetch OrderID, CustomerName, ContactName, and OrderDate from two tables.
      SELECT Orders.OrderID, Customers.CustomerName, Customers.ContactName, Orders.OrderDate
      FROM Orders
      INNER JOIN Customers
      ON Orders.CustomerID = Customers.CustomerID;
![image](https://github.com/user-attachments/assets/53acafdc-1a35-4fba-a03e-ab16b6dee664)
    
#### Fetch CustomerName, ContactName,from customer(left) table and OrderDate(right) from Orders table.
      SELECT Customers.CustomerName, Customers.ContactName, Orders.OrderDate
      FROM Customers
      LEFT JOIN Orders
      ON Customers.CustomerID=Orders.CustomerID
![image](https://github.com/user-attachments/assets/f3598861-78a5-4bbf-962b-e9634de8108d)

## DB_Table-1:Orders
![image](https://github.com/user-attachments/assets/706513f4-f1fb-460e-a198-105c3b9e8101)
## DB_Table-2:Shippers
![image](https://github.com/user-attachments/assets/e975562d-6531-47e8-8d3e-5c7c66149070)
## DB_Table-3:Employees
![image](https://github.com/user-attachments/assets/8e7dd1c7-4a43-4dd7-bd06-6a648c502f8b)


#### Lists the number of orders sent by each shipper.
      SELECT COUNT(Orders.OrderID) AS TotalOrder, Shippers.ShipperName
      FROM Orders
      LEFT JOIN Shippers
      ON Orders.ShipperID = Shippers.ShipperID
      GROUP BY ShipperName
![image](https://github.com/user-attachments/assets/9c3a659f-c0fc-4037-90fe-071759ab6cfa)

####  Lists the employees(t-3) that have registered more than 10 orders(t-1):
      SELECT COUNT(Orders.OrderID) AS NumberOfOrder, Employees.LastName 
      FROM Orders 
      INNER JOIN Employees 
      ON Orders.EmployeeID = Employees.EmployeeID 
      GROUP BY LastName 
      HAVING COUNT(Orders.OrderID) > 10
![image](https://github.com/user-attachments/assets/26e8e2bc-a13e-4b6a-9193-c6fbdec0157a)

#### Lists if the employees "Davolio" or "Fuller" have registered more than 25 orders.
      SELECT COUNT(Orders.OrderID) AS NumberOfOrder, Employees.LastName
      FROM Orders
      INNER JOIN Employees
      ON Orders.EmployeeID = Employees.EmployeeID
      WHERE LastName = 'Davolio' OR LastName = 'Fuller'
      GROUP BY LastName
      HAVING COUNT(Orders.OrderID) > 25
![image](https://github.com/user-attachments/assets/8a64e14d-5404-4e02-8998-19a8d5d4fa92)

#### Update Customers table with name 'BugsBD' and address 'Dhaka,Bangladesh'
      UPDATE Customers
      SET CustomerName= 'BugsBD', Address='Dhaka,Bangladesh'
      WHERE CustomerID=2;
![image](https://github.com/user-attachments/assets/464ced5b-f0ea-4431-92f6-ed8100e19b10)

#### Delete 'BugsDB' row from Customers table.
      DELETE FROM Customers WHERE CustomerName='BugsBD';
![image](https://github.com/user-attachments/assets/a5a3d875-d7a3-4a92-a808-c142305034a5)
