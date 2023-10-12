# Introduction

This is a python script made to initialize databases for practicing SQL.

## Installation

Unzip all databases in the databases folder. Make sure all files have the same name as the zip files, but with the .sql extension.

## Execution

```bash
# Windows
py main.py

# Mac / Linux
python3 main.py
```

## 5 sql query in the database world :

```sql
-- 1.1
SELECT name, capital
FROM countries
Where currency_symbol = '€'

-- 1.2
SELECT name
FROM subregions
WHERE name LIKE "%Africa" 

-- 1.3
SELECT name, state_id
FROM cities
WHERE latitude between 40 AND 50
AND longitude between 20 AND 30;

-- 1.4
SELECT name, capital
FROM countries
WHERE capital LIKE "P%s"

-- 1.5
SELECT ci.name
FROM cities as ci
inner join countries as co on ci.country_id = co.id
Where ci.country_id = 22
```

<div class="meta_for_parser tablespecs" style="visibility:hidden">
    <ul>
        <li>
            1.1 : selectionne toutes les villes et capitales qui ont pour devise l'euro.
        </li>
        <li>
            1.2 : selectionne tous les sous-continents qui termine leur nom par "Africa".
        </li>
        <li>
            1.3 : Selectionne toutes les villes et leur id qui ont leur latitude entre 30 et 40 ainsi que leur longitude entre 20 et 30.
        </li>
        <li>
            1.4 : Selectionne toutes les villes et leur capitale dont la capitale commence par un P majuscule et termine par un s.
        </li>
        <li>
            1.5 : Selectionne tous les noms de ville qui on pour contry id le 22 (Belgique). 
        </li>
    </ul>
</div>


## 5 sql query in the database employees

```sql
-- 2.1
SELECT emp_no, MAX(salary) AS max_salary
FROM salaries
GROUP BY emp_no;

-- 2.2
select emp.first_name, emp.last_name
from employees as emp
inner join dept_emp on dept_emp.emp_no = emp.emp_no
inner join departments on departments.dept_no = dept_emp.dept_no
where departments.dept_name = "Finance"

-- 2.3
SELECT emp.first_name, MAX(sal.salary) AS max_salary
FROM employees AS emp
INNER JOIN salaries AS sal ON sal.emp_no = emp.emp_no
GROUP BY emp.first_name

-- 2.4
select e.first_name, e.last_name
from titles as t
inner join employees as e on e.emp_no = t.emp_no
where t.title = "Engineer"

-- 2.5
select e.first_name, s.salary
from employees as e
inner join titles as t on t.emp_no = e.emp_no
inner join salaries as s on s.emp_no = e.emp_no
WHERE t.title = "Staff" and
s.salary BETWEEN 70000 and 75000

```
<div class="meta_for_parser tablespecs" style="visibility:hidden">
    <ul>
        <li>
            2.1 : selectionne pour chaque employée son salaire maximal.
        </li>
        <li>
            2.2 : renvoie les employées (nom, prénom) qui travaille dans le département Finance.
        </li>
        <li>
            2.3 : renvoie le salaire maximun de tout les employées dont leur prénom commence par un A.
        </li>
        <li>
            2.3 : Renvoi le nom et prénom de tout les ingénieurs.
        </li>
        <li>
            2.3 : Renvoi le prénom et le salaire de chaque membre du "Staff" qui on un salaire entre 70k et 75k
        </li>
    </ul>
</div>

## Mission :

For each sql query you have to determine what is their utility.\
Once you have done it you can check for the answer inside the readme.