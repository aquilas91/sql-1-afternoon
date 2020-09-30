## Table - person

### Instructions
1. Create a table called person that records a person's id, name, age, height ( in cm ), city, favorite_color. 
    * id should be an auto-incrementing id/primary key - Use type: SERIAL
2. Add 5 different people into the person database. 
    * Remember to not include the person_id because it should auto-increment.
3. List all the people in the person table by height from tallest to shortest.
4. List all the people in the person table by height from shortest to tallest.
5. List all the people in the person table by age from oldest to youngest.
6. List all the people in the person table older than age 20.
7. List all the people in the person table that are exactly 18.
8. List all the people in the person table that are less than 20 and older than 30.
9. List all the people in the person table that are not 27 (Use not equals).
10. List all the people in the person table where their favorite color is not red.
11. List all the people in the person table where their favorite color is not red and is not blue.
12. List all the people in the person table where their favorite color is orange or green.
13. List all the people in the person table where their favorite color is orange, green or blue (use IN).
14. List all the people in the person table where their favorite color is yellow or purple (use IN).

### Solution

CREATE TABLE person ( person_id SERIAL PRIMARY KEY, name VARCHAR(200), age INTEGER, height INTEGER, city VARCHAR(200), favorite_color VARCHAR(200) );

INSERT INTO person ( name, age, height, city, favorite_color ) VALUES ( 'AQUILAS AGUIYA', 30,195, 'ST PAUL', 'BLUE' );

INSERT INTO person ( name, age, height, city, favorite_color ) VALUES ( 'CREDO AGUIYA', 32,186, 'MINNEAPOLIS', 'GREEN' );

INSERT INTO person ( name, age, height, city, favorite_color ) VALUES ( 'CARESA LEGGE', 26182, 'NEW YORK ', 'purple' );

INSERT INTO person ( name, age, height, city, favorite_color ) VALUES ( 'PACHEL ANTHONY', 36,182, 'BERLIN', 'orange' );

INSERT INTO person ( name, age, height, city, favorite_color ) VALUES ( 'MONTCHO HENNOCK', 27,192, 'COTONOU', 'YELLOW' );

SELECT * FROM person ORDER BY height DESC;

SELECT * FROM person ORDER BY height ASC;

SELECT * FROM person ORDER BY age DESC;

SELECT * FROM person WHERE age > 20;

SELECT * FROM person WHERE age = 18;

SELECT * FROM person WHERE age < 20 OR age > 30;

SELECT * FROM person WHERE age != 27;

SELECT * FROM person WHERE favorite_color != 'red';

SELECT * FROM person WHERE favorite_color != 'red' AND favorite_color != 'blue';

SELECT * FROM person WHERE favorite_color = 'orange' OR favorite_color = 'green';

SELECT * FROM person WHERE favorite_color IN ( 'orange', 'green', 'blue' );

SELECT * FROM person WHERE favorite_color IN ( 'yellow', 'purple' )

## Table - orders

### Instructions

1. Create a table called orders that records: order_id, person_id, product_name, product_price, quantity.
2. Add 5 orders to the orders table.
    * Make orders for at least two different people.
    * person_id should be different for different people.
3. Select all the records from the orders table.
4. Calculate the total number of products ordered.
5. Calculate the total order price.
6. Calculate the total order price by a single person_id.

### Solution

CREATE TABLE orders ( order_id SERIAL PRIMARY KEY, person_id INTEGER, product_name VARCHAR(200), product_price NUMERIC, quantity INTEGER );

INSERT INTO orders ( person_id, product_name, product_price, quantity ) VALUES ( 56, 'iphone', 750, 1 );
INSERT INTO orders ( person_id, product_name, product_price, quantity ) VALUES ( 14, 'laptop', 800, 2 );
INSERT INTO orders ( person_id, product_name, product_price, quantity ) VALUES ( 27, 'mouse', 45.50, 1 );
INSERT INTO orders ( person_id, product_name, product_price, quantity ) VALUES ( 33, 'keybord', 32.50, 2 );
INSERT INTO orders ( person_id, product_name, product_price, quantity ) VALUES ( 45, 'headphone', 15, 3 );

SELECT * FROM orders;

SELECT SUM(quantity) FROM orders;

SELECT SUM(product_price * quantity) FROM orders;

SELECT SUM(product_price * quantity) FROM orders WHERE person_id = 0;

</details>

## Table - artist

### Instructions

1. Add 3 new artists to the artist table. ( It's already created )
2. Select 10 artists in reverse alphabetical order.
3. Select 5 artists in alphabetical order.
4. Select all artists that start with the word 'Black'.
5. Select all artists that contain the word 'Black'.

### Solution 

INSERT INTO artist ( name ) VALUES ( 'don mooen' );
INSERT INTO artist ( name ) VALUES ( 'tasha cobbs' );
INSERT INTO artist ( name ) VALUES ( 'travis greene' );

SELECT * FROM artist ORDER BY name DESC LIMIT 10;

SELECT * FROM artist ORDER BY name ASC LIMIT 5;

SELECT * FROM artist WHERE name LIKE 'Black%';

SELECT * FROM artist WHERE name LIKE '%Black%';

## Table - employee

### Instructions

1. List all employee first and last names only that live in Calgary.
2. Find the birthdate for the youngest employee.
3. Find the birthdate for the oldest employee.
4. Find everyone that reports to Nancy Edwards (Use the ReportsTo column).
   * You will need to query the employee table to find the Id for Nancy Edwards
5. Count how many people live in Lethbridge.

### Solution


SELECT first_name, last_name FROM employee WHERE city = 'Calgary';

SELECT MIN(birth_date) from employee;

SELECT MAX(birth_date) from employee;

SELECT * FROM employee WHERE reports_to = 2;

SELECT COUNT(*) FROM employee WHERE city = 'Lethbridge';


## Table - invoice 

### Instructions

1. Count how many orders were made from the USA.
2. Find the largest order total amount.
3. Find the smallest order total amount.
4. Find all orders bigger than $5.
5. Count how many orders were smaller than $5.
6. Count how many orders were in CA, TX, or AZ (use IN).
7. Get the average total of the orders.
8. Get the total sum of the orders.

### Solution


SELECT COUNT(*) FROM invoice WHERE billing_country = 'USA';

SELECT MAX(total) FROM invoice;

SELECT MIN(total) FROM invoice;

SELECT * FROM invoice WHERE total > 5;

SELECT COUNT(*) FROM invoice WHERE total < 5;

SELECT COUNT(*) FROM invoice WHERE billing_state in ('CA', 'TX', 'AZ');

SELECT AVG(total) FROM invoice;

SELECT SUM(total) FROM invoice;
