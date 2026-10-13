###### **Query1 :** 



SELECT e.first\_name, e.last\_name, d.department\_name
FROM Employees e
LEFT JOIN Department d
ON e.department\_id = d.department\_id;

mysql> SELECT e.first\_name, e.last\_name, d.department\_name

&#x20;   -> FROM Employees e

&#x20;   -> LEFT JOIN Departments d

&#x20;   -> ON e.department\_id = d.department\_id;

+------------+-----------+-----------------+

| first\_name | last\_name | department\_name |

+------------+-----------+-----------------+

| Ravi       | Sharma    | IT              |

| Neha       | Kapoor    | HR              |

| Jyoti      | Verma     | IT              |

| Anil       | Patil     | Sales           |

|  Pooja     | Singh     | Finance         |

| Sanjay     | Iyer      | Sales           |

| Jatin      | Reddy     | HR              |

| Shreya     | Mehta     | Marketing       |

| Rajesh     | Gupta     | IT              |

| Kavita     | Nair      | HR              |

+------------+-----------+-----------------+

10 rows in set (0.00 sec)


**QUERY2 :** 
---



mysql> SELECT e.\*

&#x20;   -> FROM Employees e

&#x20;   -> JOIN Departments d

&#x20;   ->     ON e.department\_id = d.department\_id

&#x20;   -> WHERE d.department\_name = 'IT'

&#x20;   ->   AND e.salary > 50000;

+-------------+------------+-----------+-------------------------------+------------+----------+---------------+

| employee\_id | first\_name | last\_name | email                         | hire\_date  | salary   | department\_id |

+-------------+------------+-----------+-------------------------------+------------+----------+---------------+

|         101 | Ravi       | Sharma    | ravi.sharma@specialforce.com  | 2017-05-15 | 55000.00 |             1 |

|         103 | Jyoti      | Verma     | jyoti.verma@specialforce.com  | 2020-11-02 | 60000.00 |             1 |

|         109 | Rajesh     | Gupta     | rajesh.gupta@specialforce.com | 2020-08-11 | 90000.00 |             1 |

+-------------+------------+-----------+-------------------------------+------------+----------+---------------+

3 rows in set (0.02 sec)





mysql> SELECT first\_name, last\_name, email

&#x20;   -> FROM Employees

&#x20;   -> WHERE first\_name LIKE 'J%'

&#x20;   -> AND email LIKE '%specialforce.com%';

+------------+-----------+------------------------------+

| first\_name | last\_name | email                        |

+------------+-----------+------------------------------+

| Jyoti      | Verma     | jyoti.verma@specialforce.com |

| Jatin      | Reddy     | jatin.reddy@specialforce.com |

+------------+-----------+------------------------------+

2 rows in set (0.00 sec)







mysql> SELECT DISTINCT department\_name FROM DEPARTMENTS;

+-----------------+

| department\_name |

+-----------------+

| IT              |

| HR              |

| Sales           |

| Finance         |

| Marketing       |

+-----------------+

5 rows in set (0.01 sec)







mysql> SELECT d.department\_name, SUM(e.salary)

&#x20;   -> FROM Employees e

&#x20;   -> JOIN Departments d

&#x20;   ->     ON e.department\_id = d.department\_id

&#x20;   -> GROUP BY d.department\_name;

+-----------------+---------------+

| department\_name | SUM(e.salary) |

+-----------------+---------------+

| IT              |     205000.00 |

| HR              |     183000.00 |

| Sales           |     145000.00 |

| Finance         |      40000.00 |

| Marketing       |      30000.00 |

+-----------------+---------------+

5 rows in set (0.00 sec)







mysql> SELECT AVG(e.salary)

&#x20;   -> FROM Employees e

&#x20;   -> JOIN Departments d

&#x20;   -> ON e.department\_id = d.department\_id

&#x20;   -> where d.department\_name = 'Finance';

+---------------+

| AVG(e.salary) |

+---------------+

|  40000.000000 |

+---------------+

1 row in set (0.02 sec)







mysql> SELECT MIN(e.salary), MAX(e.salary)

&#x20;   -> FROM Employees e

&#x20;   -> JOIN Departments d

&#x20;   -> ON e.department\_id = d.department\_id

&#x20;   -> WHERE department\_name = 'Sales';

+---------------+---------------+

| MIN(e.salary) | MAX(e.salary) |

+---------------+---------------+

|      70000.00 |      75000.00 |

+---------------+---------------+

1 row in set (0.01 sec)





mysql> SELECT d.department\_name,COUNT(e.employee\_id)

&#x20;   -> FROM EMPLOYEES E

&#x20;   -> JOIN DEPARTMENTS D

&#x20;   -> ON E.DEPARTMENT\_ID = D.DEPARTMENT\_ID

&#x20;   -> GROUP BY D.DEPARTMENT\_NAME;

+-----------------+----------------------+

| department\_name | COUNT(e.employee\_id) |

+-----------------+----------------------+

| IT              |                    3 |

| HR              |                    3 |

| Sales           |                    2 |

| Finance         |                    1 |

| Marketing       |                    1 |

+-----------------+----------------------+

5 rows in set (0.00 sec)







mysql> SELECT \*

&#x20;   -> FROM Employees

&#x20;   -> WHERE hire\_date BETWEEN '2018-01-01' AND '2020-12-31'

&#x20;   -> ORDER BY hire\_date ASC;

+-------------+------------+-----------+-------------------------------+------------+----------+---------------+

| employee\_id | first\_name | last\_name | email                         | hire\_date  | salary   | department\_id |

+-------------+------------+-----------+-------------------------------+------------+----------+---------------+

|         106 | Sanjay     | Iyer      | Sanjay.iyer@specialforce.com  | 2018-01-22 | 75000.00 |             3 |

|         104 | Anil       | Patil     | anil.patil@specialforce.com   | 2018-09-18 | 70000.00 |             3 |

|         102 | Neha       | Kapoor    | neha.kapoor@specialforce.com  | 2019-03-23 | 48000.00 |             2 |

|         109 | Rajesh     | Gupta     | rajesh.gupta@specialforce.com | 2020-08-11 | 90000.00 |             1 |

|         103 | Jyoti      | Verma     | jyoti.verma@specialforce.com  | 2020-11-02 | 60000.00 |             1 |

+-------------+------------+-----------+-------------------------------+------------+----------+---------------+

5 rows in set (0.00 sec)









mysql> SELECT \* FROM Employees WHERE email IS NULL;

Empty set (0.00 sec)







mysql> SELECT e.\* FROM Employees e

&#x20;   -> JOIN Departments d

&#x20;   -> ON d.department\_id = d.department\_id

&#x20;   -> WHERE d.department\_name IN ('HR', 'Finance', 'IT');

+-------------+------------+-----------+-------------------------------+------------+----------+---------------+

| employee\_id | first\_name | last\_name | email                         | hire\_date  | salary   | department\_id |

+-------------+------------+-----------+-------------------------------+------------+----------+---------------+

|         101 | Ravi       | Sharma    | ravi.sharma@specialforce.com  | 2017-05-15 | 55000.00 |             1 |

|         101 | Ravi       | Sharma    | ravi.sharma@specialforce.com  | 2017-05-15 | 55000.00 |             1 |

|         101 | Ravi       | Sharma    | ravi.sharma@specialforce.com  | 2017-05-15 | 55000.00 |             1 |

|         102 | Neha       | Kapoor    | neha.kapoor@specialforce.com  | 2019-03-23 | 48000.00 |             2 |

|         102 | Neha       | Kapoor    | neha.kapoor@specialforce.com  | 2019-03-23 | 48000.00 |             2 |

|         102 | Neha       | Kapoor    | neha.kapoor@specialforce.com  | 2019-03-23 | 48000.00 |             2 |

|         103 | Jyoti      | Verma     | jyoti.verma@specialforce.com  | 2020-11-02 | 60000.00 |             1 |

|         103 | Jyoti      | Verma     | jyoti.verma@specialforce.com  | 2020-11-02 | 60000.00 |             1 |

|         103 | Jyoti      | Verma     | jyoti.verma@specialforce.com  | 2020-11-02 | 60000.00 |             1 |

|         104 | Anil       | Patil     | anil.patil@specialforce.com   | 2018-09-18 | 70000.00 |             3 |

|         104 | Anil       | Patil     | anil.patil@specialforce.com   | 2018-09-18 | 70000.00 |             3 |

|         104 | Anil       | Patil     | anil.patil@specialforce.com   | 2018-09-18 | 70000.00 |             3 |

|         105 |  Pooja     | Singh     | pooja.singh@specialforce.com  | 2021-06-10 | 40000.00 |             4 |

|         105 |  Pooja     | Singh     | pooja.singh@specialforce.com  | 2021-06-10 | 40000.00 |             4 |

|         105 |  Pooja     | Singh     | pooja.singh@specialforce.com  | 2021-06-10 | 40000.00 |             4 |

|         106 | Sanjay     | Iyer      | Sanjay.iyer@specialforce.com  | 2018-01-22 | 75000.00 |             3 |

|         106 | Sanjay     | Iyer      | Sanjay.iyer@specialforce.com  | 2018-01-22 | 75000.00 |             3 |

|         106 | Sanjay     | Iyer      | Sanjay.iyer@specialforce.com  | 2018-01-22 | 75000.00 |             3 |

|         107 | Jatin      | Reddy     | jatin.reddy@specialforce.com  | 2021-12-12 | 85000.00 |             2 |

|         107 | Jatin      | Reddy     | jatin.reddy@specialforce.com  | 2021-12-12 | 85000.00 |             2 |

|         107 | Jatin      | Reddy     | jatin.reddy@specialforce.com  | 2021-12-12 | 85000.00 |             2 |

|         108 | Shreya     | Mehta     | Shreya.mehta@specialforce.com | 2022-04-19 | 30000.00 |             5 |

|         108 | Shreya     | Mehta     | Shreya.mehta@specialforce.com | 2022-04-19 | 30000.00 |             5 |

|         108 | Shreya     | Mehta     | Shreya.mehta@specialforce.com | 2022-04-19 | 30000.00 |             5 |

|         109 | Rajesh     | Gupta     | rajesh.gupta@specialforce.com | 2020-08-11 | 90000.00 |             1 |

|         109 | Rajesh     | Gupta     | rajesh.gupta@specialforce.com | 2020-08-11 | 90000.00 |             1 |

|         109 | Rajesh     | Gupta     | rajesh.gupta@specialforce.com | 2020-08-11 | 90000.00 |             1 |

|         110 | Kavita     | Nair      | Kavita.nair@specialforce.com  | 2021-02-07 | 50000.00 |             2 |

|         110 | Kavita     | Nair      | Kavita.nair@specialforce.com  | 2021-02-07 | 50000.00 |             2 |

|         110 | Kavita     | Nair      | Kavita.nair@specialforce.com  | 2021-02-07 | 50000.00 |             2 |

+-------------+------------+-----------+-------------------------------+------------+----------+---------------+

30 rows in set (0.00 sec)







mysql> SELECT first\_name, last\_name, salary

&#x20;   -> FROM Employees

&#x20;   -> WHERE salary BETWEEN 30000 AND 70000

&#x20;   -> ORDER BY salary DESC;

+------------+-----------+----------+

| first\_name | last\_name | salary   |

+------------+-----------+----------+

| Anil       | Patil     | 70000.00 |

| Jyoti      | Verma     | 60000.00 |

| Ravi       | Sharma    | 55000.00 |

| Kavita     | Nair      | 50000.00 |

| Neha       | Kapoor    | 48000.00 |

|  Pooja     | Singh     | 40000.00 |

| Shreya     | Mehta     | 30000.00 |

+------------+-----------+----------+

7 rows in set (0.00 sec)

