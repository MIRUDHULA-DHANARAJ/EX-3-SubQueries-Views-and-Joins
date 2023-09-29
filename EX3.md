# EX 3 SubQueries, Views and Joins 
## AIM:
To create a manager database and execute DML queries using SQL
## DML:
The SQL commands that deal with the manipulation of data present in the database belong to DML or Data Manipulation Language and this includes most of the SQL statements. It is the component of the SQL statement that controls access to data and to the database. Basically, DCL statements are grouped with DML statements.

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
## OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/EX-3-SubQueries-Views-and-Joins/assets/94828147/f5eb608b-c9d1-4cc2-9603-04efe32af76c)

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
## OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/EX-3-SubQueries-Views-and-Joins/assets/94828147/cdf7e7c7-c690-4bb9-bdcb-93a6c241f5b3)

### Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.
### QUERY:
```
select ename from emp where sal>(select sal from emp where empno=7566);
```
### OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/EX-3-SubQueries-Views-and-Joins/assets/94828147/dd049984-5ccd-4d2b-9e65-b1170989a9ed)

### Q2) List the ename,job,sal of the employee who get minimum salary in the company.
### QUERY:
```
select ename,job,sal from emp where sal=(select min(sal) from emp);
```
### OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/EX-3-SubQueries-Views-and-Joins/assets/94828147/84a77109-f375-4f7a-8495-a6db9125fc82)

### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.
### QUERY:
```
SELECT ENAME, JOB FROM EMP WHERE DEPTNO = 10 AND JOB IN (SELECT JOB FROM EMP WHERE JOB='SALESMAN');
```
### OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/EX-3-SubQueries-Views-and-Joins/assets/94828147/b65ea81f-47f0-4e4b-a1a3-e2074e3f5cc4)

### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.
### QUERY:
```
create view emv5 as select empno,ename,job from emp where deptno=10;
select ename,empno,job from emv5;
```
### OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/EX-3-SubQueries-Views-and-Joins/assets/94828147/6e8bbf1e-4a6c-49da-8ed3-4420a5cef4de)

### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.
### QUERY:
```
create view empv30 as select empno,ename,sal from emp where deptno=30;
select ename,empno,sal from empv30;
```
### OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/EX-3-SubQueries-Views-and-Joins/assets/94828147/ac9f9aab-f920-4726-9c5b-0badad382ca7)

### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table
### QUERY:
```
update empv5 set sal=sal+(sal*0.1) where job='clerk';
```
### OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/EX-3-SubQueries-Views-and-Joins/assets/94828147/602ef882-8412-4733-a365-2564a2a9fb7c)


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
## OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/EX-3-SubQueries-Views-and-Joins/assets/94828147/46835868-96d1-45cf-aa26-40f0d0f516de)

### Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.
### QUERY:
```
SELECT salesman1.name AS "salesman",customer1.cust_name AS "customername", customer1.city FROM salesman1,customer1 WHERE salesman1.city=customer1.city;
```
### OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/EX-3-SubQueries-Views-and-Joins/assets/94828147/70d7f349-0ca2-4a5c-9cb6-3c396fe9206c)

### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.
### QUERY:
```
select customer1.cust_name as "CUSTOMER NAME" , customer1.city as "CUSTOMER CITY" , salesman1.name as "SALESMAN NAME" , salesman1.commission as "COMMISSION" from salesman1 INNER JOIN customer1 on salesman1.salesman_id=customer1.salesman_id where salesman1.commission > 0.13;
```
### OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/EX-3-SubQueries-Views-and-Joins/assets/94828147/231d317d-7b8a-4a1e-8375-eaac7ee0145e)

### Q9) Perform Natural join on both tables
### QUERY:
```
 select * from customer1 NATURAL JOIN salesman1;
```
### OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/EX-3-SubQueries-Views-and-Joins/assets/94828147/50b39ff8-9706-4da8-a3dc-7e5097502fcd)

### Q10) Perform Left and right join on both tables
### QUERY FOR LEFT JOIN:
```
select * from salesman1 LEFT JOIN customer1 on salesman1.salesman_id=customer1.salesman_id;
```
### OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/EX-3-SubQueries-Views-and-Joins/assets/94828147/de64e86d-6b2e-46c9-a713-c2a5be5ffd8c)

### QUERY FOR RIGHT JOIN:
```
select * from salesman1 RIGHT JOIN customer1 on salesman1.salesman_id=customer1.salesman_id;
```
### OUTPUT:

![image](https://github.com/MIRUDHULA-DHANARAJ/EX-3-SubQueries-Views-and-Joins/assets/94828147/333bb1bc-2057-4c37-b61c-0697817fac3c)

## RESULT:
The program has been executed successfully for the above queries.
