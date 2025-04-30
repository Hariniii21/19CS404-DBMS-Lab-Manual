# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
-- 
![image](https://github.com/user-attachments/assets/224f184a-a01d-4af8-aa2e-ff52c1ad0178)

```sql
-- 
select gender,count(*) as TotalPatients
From Patients
Group by Gender;
```

**Output:**

![image](https://github.com/user-attachments/assets/1c997b0e-1a68-4594-b67f-ece6585c1e0c)


**Question 2**
---
--
![image](https://github.com/user-attachments/assets/ca9e3141-b4e0-42ad-a46e-75764a8af576)

```sql
--
select Diagnosis,count(*) as DiagnosisCount
from medicalrecords
group by Diagnosis
order by DiagnosisCount DESC
Limit 1;
```

**Output:**

![image](https://github.com/user-attachments/assets/668f2346-2e2f-471b-86db-474283436207)


**Question 3**
---
-- 
![image](https://github.com/user-attachments/assets/01b93cb8-276d-415d-a09e-39ed056c32d8)

```sql
--
select DoctorId,count(RecordID) as TotalRecords
from MedicalRecords
group by DoctorId;
```

**Output:**

![image](https://github.com/user-attachments/assets/7a212ede-7820-491b-9d6b-2b594bf39a23)


**Question 4**
---
--
 ![Screenshot 2025-04-30 105503](https://github.com/user-attachments/assets/17c68a94-f4ad-48db-8341-899e186207e1)

```sql
--
select sum(inventory) as total_available_amount
from fruits
where price > 0.5;
```

**Output:**

![Screenshot 2025-04-30 104257](https://github.com/user-attachments/assets/a3a0439e-b59a-4316-80c9-dac5997cbc2d)


**Question 5**
---
-- 
![Screenshot 2025-04-30 105511](https://github.com/user-attachments/assets/00d7b5d4-bc8b-42e1-8538-26710216c325)

```sql
--
select avg(income) as avg_income from employee
where name like 'A__%';
```

**Output:**

![Screenshot 2025-04-30 104508](https://github.com/user-attachments/assets/02bc0392-5f3b-497d-a401-d00cbf19dee5)


**Question 6**
---
-- 
![Screenshot 2025-04-30 105518](https://github.com/user-attachments/assets/8499292d-4881-447b-aeb4-477131fd23c9)

```sql
--
select count(*) as employees_count from employee
where income>50000;
```

**Output:**

![Screenshot 2025-04-30 104732](https://github.com/user-attachments/assets/ba26dc0e-79e7-4981-a849-c66ba3307180)


**Question 7**
---
-- 
![Screenshot 2025-04-30 105527](https://github.com/user-attachments/assets/39f5a253-5317-429a-9398-eb3c28979edb)

```sql
--
select name,length(name) as length from customer
order by length(name) DESC
LIMIT 1;
```

**Output:**

![Screenshot 2025-04-30 104840](https://github.com/user-attachments/assets/a6855226-14c0-431c-8b02-f1c09fe8cc9e)


**Question 8**
---
-- 
![Screenshot 2025-04-30 104906](https://github.com/user-attachments/assets/a3e14011-a7a5-465a-9925-ad353211d076)

```sql
--
select age, SUM(income) 
from employee
group by age
having SUM(income) > 1000000
order by age;
```

**Output:**

![Screenshot 2025-04-30 104916](https://github.com/user-attachments/assets/dabdfebf-aea1-4c99-98a1-5a5481e0ef21)

**Question 9**
---
--
![Screenshot 2025-04-30 104927](https://github.com/user-attachments/assets/4875f149-30f6-452d-99f1-2e391a8daa29)

```sql
--
select (age/5)*5 as age_group,MIN(age)
from customer1
group by age_group
HAVING MIN(age)<25;
```

**Output:**

![Screenshot 2025-04-30 104933](https://github.com/user-attachments/assets/40f9f15e-182d-4047-9a8a-7e84e2070e9a)


**Question 10**
---
--
![Screenshot 2025-04-30 104944](https://github.com/user-attachments/assets/7de3fe59-1eca-45cf-8e9d-335a3dd4bfd3)

```sql
--
select category_id,sum(price*category_id) as Revenue from products
group by category_id
having Revenue>25;
```

**Output:**

![Screenshot 2025-04-30 104951](https://github.com/user-attachments/assets/6b16917a-4a4a-4f5c-acf0-178c8f2803a6)

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
