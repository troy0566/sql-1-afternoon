## Table - People

### Instructions
1. Create a table called Person that records a person's ID, Name, Age, Height ( in cm ), City, FavoriteColor. 
    * ID should be an auto-incrementing id/primary key - Use type: INTEGER PRIMARY KEY AUTOINCREMENT

CREATE TABLE PERSON( 
	ID				INTEGER PRIMARY KEY	AUTOINCREMENT NOT Null,
	Name 			TEXT(40), 
	Age  			INT,
	Height 			TEXT(20),
	City 			TEXT(40),
	FavoriteColor 	TEXT(20)
  );


2. Add 5 different people into the Person database. 
INSERT INTO PERSON VALUES (1, "Bruce Wayne", 42, "6' 4", "Gothem", "Black");
INSERT INTO PERSON VALUES (2, "Clark Kent", 35, "6' 5", "Metroplis", "Blue");
INSERT INTO PERSON VALUES (3, "Barry Allen", 28, "6' 0", "Central City", "Red");
INSERT INTO PERSON VALUES (4, "Hal Jordan", 34, "6' 2", "Coast City", "Green");
INSERT INTO PERSON VALUES (5, "Oliver Queen", 36, "6' 2", "Star City", "Green");


3. List all the people in the Person table by Height from tallest to shortest.
SELECT * FROM PERSON Order by height DESC;

4. List all the people in the Person table by Height from shortest to tallest.
SELECT * FROM PERSON Order by height DESC;

5. List all the people in the Person table by Age from oldest to youngest.
SELECT * FROM PERSON ORDER by age DESC;

6. List all the people in the Person table older than age 20.
SELECT * FROM PERSON ORDER by age > 20;

7. List all the people in the Person table that are exactly 18.
SELECT * FROM PERSON ORDER by age = 20;

8. List all the people in the Person table that are less than 20 and older than 30.
SELECT * FROM PERSON ORDER by age < 20 AND age > 30;

9. List all the people in the Person table that are not 27 (Use not equals).
SELECT * FROM PERSON ORDER by age != 27;

10. List all the people in the Person table where their favorite color is not red.
SELECT * FROM PERSON ORDER by favoritecolor != 'Red';

11. List all the people in the Person table where their favorite color is not red and is not blue.
SELECT * FROM PERSON WHERE FavoriteColor <> "Red" AND FavoriteColor <> "Blue";

12. List all the people in the Person table where their favorite color is orange or green.
SELECT * FROM PERSON WHERE FavoriteColor = "Orange" OR FavoriteColor = "Green";

13. List all the people in the Person table where their favorite color is orange, green or blue (use IN).
SELECT * FROM PERSON WHERE FavoriteColor IN ("Orange", "Blue", "Green");

14. List all the people in the Person table where their favorite color is yellow or purple (use IN).
SELECT * FROM PERSON WHERE FavoriteColor IN ("Yellow", "Purple");

## Table - Orders

### Instructions

1. Create a table called Orders that records: PersonID, ProductName, ProductPrice, Quantity.
/* CREATE TABLE ORDERS( 
	PersonID		INTEGER PRIMARY KEY	AUTOINCREMENT NOT Null,
	ProductName 	TEXT(40), 
	ProductPrice  	DECIMAL,
	Quantity 		INTEGER
  );

2. Add 5 Orders to the Orders table.
    * Make orders for at least two different people.
    * PersonID should be different for different people.
  INSERT INTO ORDERS VALUES (1, "Bat-a-rangs", 49.99, 100);
  INSERT INTO ORDERS VALUES (2, "Trick Arrow", 30.50, 1000);
  INSERT INTO ORDERS VALUES (3, "Kryptonite", 1000.25, 50);
  INSERT INTO ORDERS VALUES (4, "Power Ring", 1000.25, 5);
  INSERT INTO ORDERS VALUES (5, "Mother Box", 5000.75, 15);

3. Select all the records from the Orders table.
  SELECT * FROM ORDERS;

4. Calculate the total number of products ordered.
 SELECT SUM(QUANTITY) FROM ORDERS;

5. Calculate the total order price.
 SELECT SUM(PRODUCTPRICE) * SUM(QUANTITY) FROM ORDERS;

6. Calculate the total order price by a single PersonID.  
SELECT PERSONID, SUM(PRODUCTPRICE) * SUM(QUANTITY) FROM ORDERS
  GROUP BY PERSONID;


## Table - Artist

### Instructions

1. Add 3 new Artists to the Artist table. ( It's already created )
INSERT INTO ARTIST VALUES (276, "Wyld Stallyns");
INSERT INTO ARTIST VALUES (277, "Disaster Area");
INSERT INTO ARTIST VALUES (278, "Spinal Tap");

2. Select 10 artists in reverse alphabetical order.
SELECT name from Artist ORDER by name DESC LIMIT 10;

3. Select 5 artists in alphabetical order.
SELECT name from Artist ORDER by name ASC LIMIT 5;

4. Select all artists that start with the word "Black".
SELECT name from Artist WHERE name LIKE "black%";

5. Select all artists that contain the word "Black".
SELECT name from Artist WHERE name LIKE "%black%";

## Table - Employee

### Instructions

1. List all Employee first and last names only that live in Calgary.
SELECT FirstName, LastName from Employee WHERE City = "Calgary";

2. Find the first and last name and birthdate for the youngest employee.
SELECT FirstName, LastName, BirthDate from Employee ORDER by BirthDate DESC LIMIT 1;

3. Find the first and last name and birthdate for the oldest employee.
SELECT FirstName, LastName, BirthDate from Employee ORDER by BirthDate ASC LIMIT 1;

4. Find everyone that reports to Nancy Edwards (Use the ReportsTo column).
   * You will need to query the employee table to find the Id for Nancy Edwards
Select * from Employee
where Reportsto = (SELECT EmployeeID FROM Employee
WHERE FirstName = "Nancy" and LastName = "Edwards");

5. Count how many people live in Lethbridge.
Select Count(*) from Employee
where City = "Lethbridge";

## Table - Invoice 

### Instructions

1. Count how many orders were made from the USA.
SELECT COUNT(*) FROM INVOICE
WHERE BillingCountry = 'USA';

2. Find the largest order total amount.
SELECT * FROM INVOICE
Order by Total DESC LIMIT 1;

3. Find the smallest order total amount.
SELECT * FROM INVOICE
Order by Total ASC LIMIT 1;

4. Find all orders bigger than $5.
SELECT * FROM INVOICE
WHERE Total > 5.00;

5. Count how many orders were smaller than $5.
SELECT * FROM INVOICE
WHERE Total < 5.00;

6. Count how many orders were in CA, TX, or AZ (use IN).
SELECT Count(*) FROM INVOICE
WHERE BillingState in ('CA', 'TX', 'AZ', 'IN');

7. Get the average total of the orders.
SELECT Avg(total) FROM INVOICE;

8. Get the total sum of the orders.
SELECT SUM(total) FROM INVOICE;