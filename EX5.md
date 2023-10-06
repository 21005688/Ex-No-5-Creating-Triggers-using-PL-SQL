# Ex. No: 5 Creating Triggers using PL/SQL

### AIM: To create a Trigger using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

### Program:
### Create employee table
```
(
empid NUMBER,
empname VARCHAR2(10),
dept VARCHAR2(10),
salary NUMBER
);
```
### Output:

![h1](https://github.com/21005688/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94747031/5e56a030-dee6-4e21-9b0a-3486ad08599a)


### Create salary_log table
```
(
log_id NUMBER GENERATED ALWAYS AS IDENTITY,
empid NUMBER,
empname VARCHAR2(10),
old_salary NUMBER,
new_salary NUMBER,
update_date DATE
);
```

### Output:

![h2](https://github.com/21005688/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94747031/cf86a363-7966-4917-9726-deda10951dc7)


### PLSQL Trigger code
```
CREATE OR REPLACE TRIGGER logging_sal_update2
BEFORE UPDATE ON empl7
FOR EACH ROW
BEGIN
IF :OLD.salary != :NEW.salary THEN
INSERT INTO log3 (empid, empname, old_salary, new_salary, update_date)
VALUES (:OLD.empid, :OLD.empname, :OLD.salary, :NEW.salary, SYSDATE);
END IF;
END;
/
```

### Output:

![h3](https://github.com/21005688/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94747031/c4a1e489-0a84-4c60-8e87-e30c59cd51d3)


### Inserting data into the employed table:

```
insert into empl7 values(1,'nive','IT',50000);
insert into empl7 values(2,'mei','sales',100000);
insert into empl7 values(3,'mena','hr',10000);
```

### Update the salary of an employed:
```
UPDATE empl7
SET salary = 50000
where empid=3;
```
### Display the employee table:
```
select * from empl7;
```
### Output:

![h4](https://github.com/21005688/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94747031/c090e04e-6089-43ab-8fde-f37ab9bf066b)
### Display the salary_log table:

```
 select * from log3;
```
### Output:

![h5](https://github.com/21005688/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/94747031/0a7a1b92-4959-4c9a-8b9e-c2f213095ce9)

### Result:
The program has been implemented successfully.
