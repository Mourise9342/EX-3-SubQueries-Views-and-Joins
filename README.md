# EX 3 SubQueries, Views and Joins 
## DATE:29/08/2023

## Create employee Table
```sql
CREATE TABLE EMP (EMPNO NUMBER(4) PRIMARY KEY,ENAME VARCHAR2(10),JOB VARCHAR2(9),MGR NUMBER(4),HIREDATE DATE,SAL NUMBER(7,2),COMM NUMBER(7,2),DEPTNO NUMBER(2));
```
## Insert the values
```sql
INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 500, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7788, 'SCOTT', 'ANALYST', 7566, '19-APR-87', 3000, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7876, 'ADAMS', 'CLERK', 7788, '23-MAY-87', 1100, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7902, 'FORD', 'ANALYST', 7566, TO_DATE('03-DEC-81', 'DD-MON-RR'), 3000, 20, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7934, 'MILLER', 'CLERK', 7782, TO_DATE('23-JAN-82', 'DD-MON-RR'), 1300, 10, 10);
```

## Create department table
```sql
CREATE TABLE DEPT (DEPTNO NUMBER(2) PRIMARY KEY,DNAME VARCHAR2(14),LOC VARCHAR2(13));
```
## Insert the values in the department table
```sql
INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (20, 'RESEARCH', 'DALLAS');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (30, 'SALES', 'CHICAGO');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (40, 'OPERATIONS', 'BOSTON');
```

### Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.


### QUERY:
CREATE VIEW details AS SELECT ENAME FROM EMP WHERE SALARY >(select SALARY from EMP where EMPNO=7566);

### OUTPUT:
![Q1](https://github.com/AdhithiyanK/EX-3-SubQueries-Views-and-Joins/assets/121029258/355eea98-35e9-442a-b279-d8e65a9f5f13)


### Q2) List the ename,job,sal of the employee who get minimum salary in the company.

### QUERY:
 CREATE VIEW minimum AS select ENAME,JOB,SALARY from EMP where SALARY =(select MIN(SALARY) from EMP);

### OUTPUT:
![Q2](https://github.com/AdhithiyanK/EX-3-SubQueries-Views-and-Joins/assets/121029258/cea57748-28a0-4ee8-bba4-3e82f10d738a)


### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.

### QUERY:
select ENAME,JOB from EMP where  DEPTNO=10 AND JOB='SALESMAN';

### OUTPUT:
![Q3](https://github.com/AdhithiyanK/EX-3-SubQueries-Views-and-Joins/assets/121029258/552e47b2-c495-4a02-a2e3-3dc4b826bca1)



### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.

### QUERY:

create view empv5 as select EMPNO,ENAME,JOB from EMP where DEPTNO=10;
### OUTPUT:
![Q4](https://github.com/AdhithiyanK/EX-3-SubQueries-Views-and-Joins/assets/121029258/4077d0c6-83b0-488e-9c3e-dcaef7323a23)


### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.

### QUERY:
create view empv30 AS select EMPNO,ENAME,SALARY from EMP where DEPTNO=30;

### OUTPUT:
![Q5](https://github.com/AdhithiyanK/EX-3-SubQueries-Views-and-Joins/assets/121029258/96de7710-975c-4a59-aee8-5357e9a1133d)


### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table

### QUERY:
update EMP set SALARY=SALARY*1.1 WHERE JOB='clerk';

create view empv5 as select EMPNO,ENAME,SALARY,JOB from EMP;

### OUTPUT:
![Q6](https://github.com/AdhithiyanK/EX-3-SubQueries-Views-and-Joins/assets/121029258/4103d817-4537-4226-be45-16eae6df88a9)


## Create a Customer1 Table
```sql
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(20),city VARCHAR(20),grade INT,salesman_id INT);
```
## Inserting Values to the Table
```sql
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
```
## Create a Salesperson1 table
```sql
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(20),city VARCHAR(20),commission DECIMAL(4,2));
```
## Inserting Values to the Table
```sql
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```
### Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

### QUERY:

select s.name,c.cust_name,s.city from salesman1 as s ,customer1 as c where s.city=c.city;
### OUTPUT:
![Q7](https://github.com/AdhithiyanK/EX-3-SubQueries-Views-and-Joins/assets/121029258/55de0609-4a1f-4927-85a4-16eb0d0396dd)


### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.


### QUERY:
select s.name,c.cust_name,c.city,s.commission from salesman1 as s inner join customer1 as c on s.city=c.city where s.commission>0.13;

### OUTPUT:
![Q8](https://github.com/AdhithiyanK/EX-3-SubQueries-Views-and-Joins/assets/121029258/d279dc47-56b4-40dc-a044-f05fd7278d34)


### Q9) Perform Natural join on both tables

### QUERY:

 select s.name,c.cust_name,c.city,s.commission from salesman1 as s natural join customer1 as c where s.commission>0.13;
### OUTPUT:
![Q9](https://github.com/AdhithiyanK/EX-3-SubQueries-Views-and-Joins/assets/121029258/de4a4fa5-ab72-47e4-9f18-0d4bef00da11)



### Q10) Perform Left and right join on both tables

### QUERY:
select s.name,c.cust_name,c.city,s.commission from salesman1 as s left join customer1 as c on s.salesman_id=c.salesman_id where s.commission>0.13;

select s.name,c.cust_name,c.city,s.commission from salesman1 as s right join customer1 as c on s.salesman_id=c.salesman_id where s.commission>0.13;

### OUTPUT:
![Q10](https://github.com/AdhithiyanK/EX-3-SubQueries-Views-and-Joins/assets/121029258/601b9323-2b4e-4318-9e6a-413344c627db)
### RESULT :
Hence successfully created a manager database and execute DML queries using SQL.
