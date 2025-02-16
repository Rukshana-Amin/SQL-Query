# SQL-Query solve: For Database assignment tasks.

--1. A database named database_assignment.

CREATE DATABASE database_assignment;

--2. A table named customers.

CREATE TABLE customers(
    id INT AUTO_INCREMENT PRIMARY KEY,
    First_Name VARCHAR(50) Not Null,
    Last_Name VARCHAR(50) Not Null,
    Date_of_Birth DATE Not Null,
    Phone VARCHAR(20),
    Address VARCHAR(30) Not Null,
    City VARCHAR(30) Not Null,
    State VARCHAR(30) Not Null,
    Points INT Not Null
);

--3. Insert the customer data.

INSERT INTO customers (First_Name, Last_Name, Date_of_Birth, Phone, Address, City, State, Points) values

    ('Babara','MacCaffrey','1986-03-28', '781-932-9754', '0 Sage Terrace', 'Waltham', 'MA', '2273'),
    ('Ines','Brushfield','1986-04-13', '804-427-9456', '14187 Commercial Trail', 'Hampton','VA', '947'),
    ('Freddi','Boagey','1985-02-07', '719-724-7869', '251 Springs Junction', 'Colorado Springs','CO', '2967'),
    ('Ambur','Roseburgh','1974-04-14', '407-231-8017', '30 Arapahoe Terrace', 'Orlando','FL', '457'),
    ('Clemmie','Betchley','1973-11-07', '', '5 Spohn Circle', 'Arlington','TX', '3675')
    ;
    
SELECT * FROM customers; 

--4. Show only 2 members whose points are more than 1000.

SELECT First_Name, Last_Name, Points FROM customers WHERE Points>1000 ORDER BY Points DESC LIMIT 2;

--5. The customers whose age is in 1980 to 1990 or points less than 1000.

SELECT * FROM customers WHERE Points<1000;

SELECT * FROM customers WHERE Date_of_Birth BETWEEN '1980-01-01' AND '1990-12-31';

--6. Order the customers by points in ascending order.

SELECT * FROM customers ORDER BY Points ASC;

--7. Find the customer whose name contains 'burgh' using Regular Expression.

SELECT * FROM customers WHERE First_Name REGEXP 'burgh';
SELECT * FROM customers WHERE Last_Name REGEXP 'burgh';

--8. Find the customer who does not have phone number.

SELECT First_Name, Last_Name FROM customers WHERE Phone LIKE '';

--9. Changing the 'Date of Birth' column name into 'dob'.

ALTER TABLE customers
RENAME COLUMN Date_of_Birth TO dob;

--10. Find the max point holder customer name.

SELECT First_Name,Last_Name,MAX(Points) FROM customers;


--11. Execute a query for the following scenario.
  --If customers have points less than 1000, they are bronze member.
  --If customers have points more than 1000 and less than 2000, they are silver member.
  --If customers have points more than 2000 and less than 3000, they are gold member.
  --If customers have points more than 3000, they are platinum member.


SELECT First_Name, Last_Name, Points,
    CASE 
        WHEN points < 1000 THEN 'they are bronze member'
        WHEN points > 1000 AND points < 2000 THEN 'they are silver member'
        WHEN points > 2000 AND points < 3000 THEN 'they are gold member'
        ELSE 'they are platinum member'
    END as 'Membership Status'
FROM customers;

