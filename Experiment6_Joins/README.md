# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
-- 
![Screenshot 2025-04-30 185727](https://github.com/user-attachments/assets/fa335143-5230-479a-9308-b2abd1f7dd0d)

```sql
--
select c.cust_name ,s.name from customer c
left join salesman s on c.salesman_id=s.salesman_id
where c.city=s.city;
```

**Output:**

![Screenshot 2025-04-30 185736](https://github.com/user-attachments/assets/1f27ddb5-f4e5-4183-b238-64cadcbfd32f)


**Question 2**
---
--
![Screenshot 2025-04-30 185852](https://github.com/user-attachments/assets/3fb026fe-f8b8-42a2-9d80-871a44c8333d)

```sql
--
select c.cust_name,c.city,o.ord_no,o.ord_date,o.purch_amt as 'Order Amount',s.name,s.commission
from customer c
left join orders o
on o.customer_id=c.customer_id
left join salesman s
on s.salesman_id=o.salesman_id;
```

**Output:**

![Screenshot 2025-04-30 185919](https://github.com/user-attachments/assets/ce152c98-52e6-45d3-970b-298d30f5264e)

**Question 3**
---
-- 
![Screenshot 2025-04-30 185935](https://github.com/user-attachments/assets/822dca1e-2bc0-4163-bdb8-53d780c0ade1)

```sql
--
select c.cust_name,c.city,c.grade,s.name as Salesman,s.city from customer c
inner join salesman s on c.salesman_id=s.salesman_id
order by c.customer_id asc;
```

**Output:**

![Screenshot 2025-04-30 185948](https://github.com/user-attachments/assets/28749f2e-8436-42de-a5d2-8007044de39b)


**Question 4**
---
--
![Screenshot 2025-04-30 185959](https://github.com/user-attachments/assets/6b02f95c-1c82-4b22-92e7-4720ad3370ae)

```sql
--
select p.* from patients p
inner join test_results t on p.patient_id=t.patient_id
where t.test_name='X-Ray' and t.result='Normal';
```

**Output:**

![Screenshot 2025-04-30 190011](https://github.com/user-attachments/assets/fa0c1afe-bcc9-48d6-919b-6933f0172618)


**Question 5**
---
--
![Screenshot 2025-04-30 190036](https://github.com/user-attachments/assets/b33bb5e5-a8ad-4457-b067-e517b693f8fa)

```sql
--
SELECT o.ord_no,o.ord_date,o.purch_amt,c.cust_name AS "Customer Name",c.grade,s.name AS "Salesman",s.commission FROM orders o
JOIN 
    customer c ON o.customer_id = c.customer_id
JOIN 
    salesman s ON o.salesman_id = s.salesman_id;

```

**Output:**

![Screenshot 2025-04-30 190053](https://github.com/user-attachments/assets/d2388d3a-1c73-4bf0-ba2b-f7a2d0c567d1)


**Question 6**
---
--
![Screenshot 2025-04-30 190107](https://github.com/user-attachments/assets/b0256790-659c-4bf0-8751-fc9650669c4c)

```sql
--
select o.ord_no,o.purch_amt,o.ord_date,c.cust_name,c.city as customer_city,
c.grade,s.name as salesman_name,s.city as salesman_city,s.commission from orders o
join customer c on o.customer_id=c.customer_id
join salesman s on o.salesman_id=s.salesman_id;
```

**Output:**

![Screenshot 2025-04-30 190118](https://github.com/user-attachments/assets/c8f50e10-c1fd-4a0c-9190-814d9ba8d3bd)


**Question 7**
---
--
![Screenshot 2025-04-30 190132](https://github.com/user-attachments/assets/5df2c548-a129-47fe-af67-929f722541b2)

```sql
--
select p.first_name,s.*
from PATIENTS p
inner join SURGERIES s on p.patient_id = s.patient_id
where p.first_name = 'Alice';
```

**Output:**

![Screenshot 2025-04-30 190144](https://github.com/user-attachments/assets/35861e6d-76d8-4461-a3e7-308124e5f475)


**Question 8**
---
--
![Screenshot 2025-04-30 190154](https://github.com/user-attachments/assets/fa143b6e-b6db-42ba-a363-aff45f8baf0a)

```sql
--
select p.first_name as patient_name,
d.first_name as doctor_name
from PATIENTS p
inner join DOCTORS d
on p.doctor_id = d.doctor_id
where p.discharge_date is null;
```

**Output:**

![Screenshot 2025-04-30 190201](https://github.com/user-attachments/assets/5902e7ef-9728-4b39-9568-c3a4504cc434)


**Question 9**
---
-- 
![Screenshot 2025-04-30 190212](https://github.com/user-attachments/assets/c18550de-fbdb-45fe-a9ee-624f1f6dcfcb)

```
sql
--
select c.cust_name as "Customer Name",c.city,s.name as Salesman,s.city,s.commission from customer c
join salesman s on c.salesman_id=s.salesman_id
where s.commission>0.12 and c.city<>s.city;
```

**Output:**

![Screenshot 2025-04-30 190221](https://github.com/user-attachments/assets/84c2065a-0d57-48dc-b9ed-028f4ec86eb9)


**Question 10**
---
--
![Screenshot 2025-04-30 190235](https://github.com/user-attachments/assets/5a11327e-91f4-433d-b047-756e4ea6f20e)

```sql
--
select c.*
from customer c
left join orders o on o.customer_id = c.customer_id
where o.ord_date > '2012-08-17';
```

**Output:**

![Screenshot 2025-04-30 190243](https://github.com/user-attachments/assets/23945399-34af-4cb0-8198-1775daa4f09c)


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
