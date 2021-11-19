###  Create a database using the attached "Jaunty Coffee Co. ERD" by doing the following:

1.  Develop SQL code to create each table as specified in the attached “Jaunty Coffee Co. ERD” by doing the following:
a.  Provide the SQL code you wrote to create all the tables.

```sh
CREATE TABLE IF NOT EXISTS COFFEE_SHOP(
shop_id INT AUTO_INCREMENT,
shop_name VARCHAR(50),
city VARCHAR(50),
state CHAR(2),
PRIMARY KEY (shop_id)
);

CREATE TABLE IF NOT EXISTS SUPPLIER(
supplier_id INT AUTO_INCREMENT,
company_name VARCHAR(50),
country VARCHAR(30),
sales_contact_name VARCHAR(60),
email VARCHAR(50) NOT NULL,
PRIMARY KEY (supplier_id)
);

CREATE TABLE IF NOT EXISTS COFFEE(
coffee_id INT AUTO_INCREMENT,
shop_id INT,
supplier_id INT,
coffee_name VARCHAR(30),
price_per_pound NUMERIC(5,2),
PRIMARY KEY (coffee_id),
FOREIGN KEY (shop_id) REFERENCES COFFEE_SHOP(shop_id),
FOREIGN KEY (supplier_id) REFERENCES SUPPLIER(supplier_id)
);

CREATE TABLE IF NOT EXISTS EMPLOYEE(
employee_id INT AUTO_INCREMENT,
first_name VARCHAR(30),
last_name VARCHAR(30),
hire_date DATETIME,
job_title VARCHAR(50),
shop_id INT,
PRIMARY KEY (employee_id),
FOREIGN KEY (shop_id) REFERENCES COFFEE_SHOP(shop_id)
);
```
b.  Demonstrate that you tested your code by providing a screenshot showing your SQL commands and the database server’s response.


2.  Develop SQL code to populate each table in the database design document by doing the following:
 
Note: This data is not provided. You will be fabricating the data for this step.

```sh
CREATE TABLE IF NOT EXISTS `COFFEE_SHOP` (
`shop_id` INT AUTO_INCREMENT,
`shop_name` VARCHAR(50),
`city` VARCHAR(50),
`state` CHAR(2),
PRIMARY KEY (`shop_id`)
) DEFAULT CHARSET=utf8;
INSERT INTO `COFFEE_SHOP` (`shop_id`, `shop_name`, `city`, `state`) VALUES
('1', 'Cat & Cloud', 'Santa Cruz','77'),
('2', 'Orchard Coffee', 'Waynesville','77'),
('3', 'Mom \'n \'Em Coffee', 'Cincinnati','77');

CREATE TABLE IF NOT EXISTS `SUPPLIER`(
`supplier_id` INT AUTO_INCREMENT,
`company_name` VARCHAR(50),
`country` VARCHAR(30),
`sales_contact_name` VARCHAR(60),
`email` VARCHAR(50) NOT NULL,
PRIMARY KEY (`supplier_id`)
) DEFAULT CHARSET=utf8;
INSERT INTO `SUPPLIER` (`supplier_id`, `company_name`, `country`, `sales_contact_name`, `email`) VALUES
('1', 'AmericanoCorp', 'Canada', 'Leonardo', 'leonardo@americano.com'),
('2', 'MacchiatoCorp', 'USA', 'Albert', 'albert@macchiato.com'),
('3', 'EspressoCorp', 'Mexico', 'Nicolo', 'nicolotesla@espresso.com');

CREATE TABLE IF NOT EXISTS `COFFEE`(
`coffee_id` INT AUTO_INCREMENT,
`shop_id` INT,
`supplier_id` INT,
`coffee_name` VARCHAR(30),
`price_per_pound` NUMERIC(5,2),
PRIMARY KEY (`coffee_id`),
FOREIGN KEY (`shop_id`) REFERENCES `COFFEE_SHOP`(`shop_id`),
FOREIGN KEY (`supplier_id`) REFERENCES `SUPPLIER`(`supplier_id`)
) DEFAULT CHARSET=utf8;
INSERT INTO `COFFEE` (`coffee_id`, `shop_id`, `supplier_id`, `coffee_name`, `price_per_pound`) VALUES
('1', '1', '3', 'Espresso', '3.00'),
('2', '2', '2', 'Macchiato', '4.00'),
('3', '2', '1', 'Americano', '2.77');

CREATE TABLE IF NOT EXISTS `EMPLOYEE`(
`employee_id` INT AUTO_INCREMENT,
`first_name` VARCHAR(30),
`last_name` VARCHAR(30),
`hire_date` DATETIME not null default current_timestamp,
`job_title` VARCHAR(50),
`shop_id` INT,
PRIMARY KEY (`employee_id`),
FOREIGN KEY (`shop_id`) REFERENCES `COFFEE_SHOP`(`shop_id`)
) DEFAULT CHARSET=utf8;
INSERT INTO `EMPLOYEE` (`employee_id`, `first_name`, `last_name`, `job_title`, `shop_id`) VALUES
('1', 'albert', 'einstein', 'mc square executive', '2'),
('2', 'nicolo', 'tesla', 'ac executive', '3'),
('3', 'leonardo', 'da Vinci', 'versetile executive', '1');
```

### After Successful Build, run this on right side
```sh
SELECT * FROM coffee;
SELECT * FROM coffee_shop;
SELECT * FROM employee;
SELECT * FROM supplier;
```
 
a.  Provide the SQL code you wrote to populate the tables with at least three rows of data in each table.
b.  Demonstrate that you tested your code by providing a screenshot showing your SQL commands and the database server’s response.


3.  Develop SQL code to create a view by doing the following: 
a.  Provide the SQL code you wrote to create your view. The view should show all of the information from the “Employee” table but
concatenate each employee’s first and last name, formatted with a space between the first and last name, into a new attribute called employee_full_name.

```sh
SELECT employee_id, CONCAT(first_name, ' ', last_name) AS employee_full_name, job_title, shop_id FROM EMPLOYEE;
```

4.  Develop SQL code to create an index on the coffee_name field by doing the following:
a.  Provide the SQL code you wrote to create your index on the coffee_name field from the “Coffee” table.
b.  Demonstrate that you tested your code by providing a screenshot showing your SQL commands and the database server’s response.

```sh
CREATE INDEX CoffeeIndex On COFFEE(coffee_name);
SHOW INDEX FROM `COFFEE`;
```

5.  Develop SQL code to create an SFW (SELECT–FROM–WHERE) query for any of your tables or views by doing the following: 
a.  Provide the SQL code you wrote to create your SFW query.
b.  Demonstrate that you tested your code by providing a screenshot showing your SQL commands and the database server’s response.
6.  Develop SQL code to create a query by doing the following:
a.  Provide the SQL code you wrote to create your table joins query. The query should join together three different tables and include
attributes from all three tables in its output.
b.  Demonstrate that you tested your code by providing a screenshot showing your SQL commands and the database server’s response.
 
C.  Submit parts A and B as a PDF, with each part clearly labeled.
 
D.  Demonstrate professional communication in the content and presentation of your submission.