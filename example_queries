DROP TABLE employee;
CREATE TABLE employee (
    emp_id INT PRIMARY KEY,
    first_name VARCHAR(20),
    last_name VARCHAR(20),
    birth_day DATE,
    sex VARCHAR(1),
    salary INT,
    super_id INT,
    branch_id INT
);
SELECT * FROM employee;


DROP TABLE branch;
CREATE TABLE branch (
    branch_id INT PRIMARY KEY,
    branch_name VARCHAR(10),
    mgr_id INT,
    mgr_start_date DATE,
    FOREIGN KEY (mgr_id) REFERENCES employee(emp_id) ON DELETE SET NULL
);
ALTER TABLE employee ADD FOREIGN KEY (branch_id) REFERENCES branch(branch_id) ON DELETE SET NULL;
ALTER TABLE employee ADD FOREIGN KEY (super_id) REFERENCES employee(emp_id) ON DELETE SET NULL;
SELECT * FROM branch;


DROP TABLE client;
CREATE TABLE client (
    client_id INT PRIMARY KEY,
    client_name VARCHAR(30),
    branch_id INT,
    FOREIGN KEY (branch_id) REFERENCES branch(branch_id) ON DELETE SET NULL
);
SELECT * FROM client;


CREATE TABLE works_with (
    emp_id INT,
    client_id INT,
    total_sales INT,
    PRIMARY KEY(emp_id, client_id),
    FOREIGN KEY (emp_id) REFERENCES employee(emp_id) ON DELETE CASCADE,
    FOREIGN KEY (client_id) REFERENCES client(client_id) ON DELETE CASCADE
);
SELECT * FROM works_with;


CREATE TABLE branch_supplier (
    branch_id INT,
    supplier_name VARCHAR(30),
    supply_type VARCHAR(20),
    PRIMARY KEY (branch_id,supplier_name),
    FOREIGN KEY (branch_id) REFERENCES branch(branch_id) ON DELETE CASCADE
);
SELECT * FROM branch_supplier;

----inserting info for Corporate branch
INSERT INTO employee VALUES(100,'David','Wallace','1967-11-17','M','250000',NULL,NULL);

INSERT INTO branch VALUES(1,'Corporate',100,'2006-02-09');

UPDATE employee SET branch_id=1 WHERE emp_id=100;

INSERT INTO employee VALUES(101,'Jan','Levinson','1961-05-11','F','110000','100','1');

----inserting info for Scranton branch
INSERT INTO employee VALUES(102,'Michael','Scott','1964-03-15','M','75000',100,NULL);

INSERT INTO branch VALUES(2,'Scranton',102,'1992-04-06');
UPDATE employee SET branch_id=2 WHERE emp_id=102;
INSERT INTO employee VALUES(103,'Angela','Martin','1971-06-25','F','63000','102','2');
INSERT INTO employee VALUES(104,'Kelly','Kapoor','1980-02-05','F','55000','102','2');
INSERT INTO employee VALUES(105,'Stanley','Hudson','1958-02-19','M','69000','102','2');


----inserting info for Stamford branch
INSERT INTO employee VALUES(106,'Josh','Porter','1969-09-05','M','78000',100,NULL);

INSERT INTO branch VALUES(3,'Stamford',106,'1998-02-13');
UPDATE employee SET branch_id=3 WHERE emp_id=106;
INSERT INTO employee VALUES(107,'Andy','Bernard','1973-07-22','M','65000','106','3');
INSERT INTO employee VALUES(108,'Jim','Halpert','1978-10-01','M','71000','106','3');


-----inserting into client table
INSERT INTO client VALUES(400,'Dunmore Highschool',2);
INSERT INTO client VALUES(401,'Lackawana Country',2);
INSERT INTO client VALUES(402,'FedEX',3);
INSERT INTO client VALUES(403,'John Daly Law, LLC',3);
INSERT INTO client VALUES(404,'Scranton Whitepages',2);
INSERT INTO client VALUES(405,'Times Newspaper',3);
INSERT INTO client VALUES(406,'FedEX',2);



-----inserting into branch_supplier table

INSERT INTO branch_supplier VALUES(2,'Hammer Mill','Paper');
INSERT INTO branch_supplier VALUES(2,'Uni-ball','Writing Utensils');
INSERT INTO branch_supplier VALUES(3,'Patriot Paper','Paper');
INSERT INTO branch_supplier VALUES(2,'J.T. Forms & Labels','Custom Forms');
INSERT INTO branch_supplier VALUES(3,'Uni-ball','Writing Utensils');
INSERT INTO branch_supplier VALUES(3,'Hammer Mill','Paper');
INSERT INTO branch_supplier VALUES(3,'Stamford Lables','Custom Forms');
UPDATE branch_supplier SET supplier_name= 'Stamford Labels' WHERE supplier_name='Stamford Lables';


-----inserting into works_with table

INSERT INTO works_with VALUES(105,400,55000);
INSERT INTO works_with VALUES(102,401,267000);
INSERT INTO works_with VALUES(108,402,22500);
INSERT INTO works_with VALUES(107,403,5000);
INSERT INTO works_with VALUES(108,403,12000);
INSERT INTO works_with VALUES(105,404,33000);
INSERT INTO works_with VALUES(107,405,26000);
INSERT INTO works_with VALUES(102,406,15000);
INSERT INTO works_with VALUES(105,406,130000);



----- examples of basic queries
#Find all employees
SELECT * FROM employee;
#Find all clients
SELECT * FROM client;
#Find all employees ordered by salary
SELECT * FROM employee ORDER BY salary DESC;
#Find all employees ordered by sex then name
SELECT * FROM employee ORDER BY sex, first_name, last_name;
#Find the first 5 employees in the table
SELECT * FROM employee LIMIT 5;
#Find the first and last names of all employees
SELECT first_name, last_name FROM employee;
#Find the forename and suranme of all employees
SELECT first_name AS forename, last_name AS surname FROM employee;
#Find all the different genders
SELECT DISTINCT sex FROM employee;
#Find all the different branch_id
SELECT DISTINCT branch_id FROM employee;
#Find the number of employees
SELECT COUNT(emp_id) FROM employee;
#Find the number of employees that have supervisors
SELECT COUNT(super_id) FROM employee;
#Find the number of Female employees born after 1970
SELECT COUNT(emp_id) FROM employee WHERE sex='F' and birth_day>'1970-01-01';
#Find the average salary of all employees
SELECT AVG(salary) FROM employee;
#Find the average salary of all male employees
SELECT AVG(salary) FROM employee WHERE sex='M';
#Find the sum salary of all employees
SELECT SUM(salary) FROM employee;
#Find how many males and females there are
SELECT COUNT(sex), sex FROM employee GROUP BY sex;
#Find the total sales of each salesman
SELECT SUM(total_sales), emp_id from works_with GROUP BY emp_id;
#Find the total of how much each client bought
SELECT SUM(total_sales), client_id from works_with GROUP BY client_id;


------------WILDCARDS--------------
-- % = any characters, _ = One character

#Find any clients who are an LLC
SELECT * FROM client WHERE client_name LIKE '%LLC%';
#Find any clients who are in Label bussiness
SELECT * FROM branch_supplier WHERE supplier_name LIKE '%Label%';
#Find any employee born in October
SELECT * FROM employee WHERE birth_day LIKE '____-10-__';
#Find any clients who are schools
SELECT * FROM client WHERE client_name LIKE '%school%' OR '%School';


-----------UNION-------------------
SELECT first_name AS Company_names FROM employee UNION SELECT branch_name FROM branch;



----------JOIN---------------------
SELECT employee.emp_id, employee.first_name, branch.branch_name FROM employee JOIN branch ON employee.emp_id = branch.mgr_id;



---------------NESTED QUERIES------------
#Find names of all employees who have sold over 30000 to a single client
SELECT employee.first_name, employee.last_name FROM employee WHERE employee.emp_id IN (
    SELECT works_with.emp_id FROM works_with WHERE works_with.total_sales > 30000
    );

#Find all the clients who are handled by the branch that Micheal Scott manages 
SELECT client.client_name from client WHERE client.branch_id IN (
    SELECT branch.branch_id FROM branch WHERE branch.mgr_id IN (
        SELECT employee.emp_id FROM employee WHERE employee.first_name='Michael' AND employee.last_name='Scott'));





