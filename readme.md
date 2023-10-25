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

## sql query in the database world AND employees :

```sql
--------------------------------------------------------------------------------------
--- SELECT
---
-- 1.1
SELECT *
FROM countries;
--/-- SELECTionne tout les éléments présent dans countries (id, name, capital, phonecode, capital, etc)

-- 1.2
SELECT id, name
FROM cities;
--/-- SELECTionne l'id et le nom de tout les éléments dans cities

-- 1.3
SELECT name
FROM states;
--/-- SELECTionne le nom de tous les états dans le monde

-- 1.4
SELECT *
FROM subregions;
--/-- SELECTionne tous les éléments dans la table subregions

-- 1.5
SELECT name
FROM regions;
--/-- SELECTionne le nom de toutes les régions du monde

--------------------------------------------------------------------------------------
--- DISTINCT
---
-- 2.1
SELECT DISTINCT country_code
FROM cities;
--/-- Renvoie le nombre de country_code unique il existe (198)

-- 2.2
SELECT DISTINCT subregion
FROM countries;
--/-- Renvoie le nombre de sous-régions unique existante (23)

-- 2.3
SELECT DISTINCT country_id
FROM states;
--/-- Renvoie tout les id uniques de tout les country_id (203) 

-- 2.4
SELECT DISTINCT currency_symbol
FROM countries;
--/-- Renvoie tous les currency différents dans countries (109)

-- 2.5
SELECT DISTINCT country_id
FROM cities;
--/-- Renvoie tous les country_id présent dans cities (198)

--------------------------------------------------------------------------------------
--- WHERE
---
-- 3.world.1
SELECT *
FROM cities
WHERE state_id > 500;
--/-- Renvoie le toutes les infos dans cities avec les state_id au dessus de 500 (148566)

-- 3.world.2
SELECT name, capital
FROM countries
WHERE currency_symbol = '€'
--/-- SELECTionne toutes les villes et capitales qui ont pour devise l'euro. (35)

-- 3.world.3
SELECT name, state_id
FROM cities
WHERE latitude between 40 AND 50;
--/-- SELECTionne toutes les villes et leur id qui ont leur latitude entre 30 et 40. (56498)

-- 3.world.4
SELECT name
FROM subregions
WHERE id < 14;
--/-- SELECTionne toutes les villes dont les id sont inférieurs à 14 (13)

-- 3.world.5
SELECT name
FROM cities
WHERE state_id = 488;
--/-- SELECTionne le nom de la ville dont le state id = 488 (ANDorra la vella)

-- 3.employees.6
SELECT dept_name
FROM departments
WHERE dept_no = "d005";
--/-- Renvoie le nom du département (Development) 

-- 3.employees.7
SELECT first_name
FROM employees
WHERE lastname = "Simmel";
--/-- 167 ont pour nom de famille Simmel

-- 3.employees.8
SELECT salary
FROM salaries
WHERE salary > 100000;
--/-- SELECTionne tout les salaires quAND ils sont aux dessus de 100000 (94696) 

-- 3.employees.9
SELECT title
FROM titles
WHERE emp_no = 10010;
--/-- Renvoie ingénieur

-- 3.employees.10
SELECT first_name, last_name
FROM employees
WHERE birth_date = "1958-02-19";
--/-- renvoie les utilisateurs qui sont nés le 19 févriers (73)

--------------------------------------------------------------------------------------
--- AND, OR
---
-- 3.world.1
SELECT name, state_id
FROM cities
WHERE latitude > 40 AND latitude < 50;
--/-- renvoie le nom et le state id de toutes les villes qui sont entre 40 et 50 de latitude. (56477)

-- 3.world.2
SELECT name
FROM regions
WHERE id = 1 OR id = 4;
--/-- Afrique et Europe

-- 3.world.3
SELECT name
FROM subregions
WHERE region_id = 2 or region_id = 4;
--/-- (8)

-- 3.employees.4
SELECT birth_date
FROM employees
WHERE first_name = Parto AND last_name = Bamford;
--/-- La date de naissance de Parto Bamford est : 1959-12-03

-- 3.employees.5
SELECT emp_no
FROM salaries
WHERE salary < 70000 AND salary > 60000;
--/-- Nombres de salaire (588188)

--------------------------------------------------------------------------------------
--- IN
---
-- 4.world.1
SELECT *
FROM subregions 
WHERE name IN ("Western Africa", "toto", "tata", "yo", "Eastern Africa");
--/-- renvoie deux lignes avec Western Africa et Eastern Africa

-- 4.world.2
SELECT *
FROM countries 
WHERE name IN ("Antartica", "Belize", "Salut", "Non", "+33");
--/-- Renvoie juste Belize

-- 4.world.3
SELECT *
FROM cities 
WHERE name IN ("Paris", "Marseille", "toto", "Monluc", "New-york");
--/-- renvoie 12 lignes

-- 4.employees.4
SELECT first_name, last_name
FROM employees
WHERE birth_date IN ("1954-01-01", "1954-02-01", "1954-03-01", "1954-04-01", "1954-05-01", "1954-06-01", "1954-07-01", "1954-08-01", "1954-09-01", "1954-10-01", "1954-11-01", "1954-12-01");
--/-- 776 personnes sont nées le premiers de chaque mois de l'année 1954

-- 4.employees.5
SELECT emp_no
FROM titles
WHERE title IN ("Ingénieur", "Ingé", "Docteur", "Doctor", "Engineer", "Ingeneer") 
--/-- 115003 résultats 

--------------------------------------------------------------------------------------
--- BETWEEN
---
-- 5.world.1
SELECT name
FROM cities 
WHERE latitude BETWEEN 40 AND 50;
--/-- 56498 résultats 

-- 5.world.2
SELECT name
FROM states 	
WHERE latitude BETWEEN 40 AND 50
AND longitude BETWEEN 20 AND 40;
--/-- 315 résultats

-- 5.world.3
SELECT name
FROM subregions 	
WHERE region_id BETWEEN 1 AND 2;
--/-- 9 résultats

-- 5.employees.4
SELECT title
FROM titles
WHERE from_date BETWEEN "1990-01-01" AND "1999-12-31"; 
--/-- 308836 résultats 

-- 5.employees.5
SELECT DISTINCT emp_no
FROM salaries
WHERE salary BETWEEN 70000 and 80000;
--/-- 118269 résultats

--------------------------------------------------------------------------------------
--- LIKE
---
-- 6.world.1
SELECT name
FROM subregions
WHERE name LIKE "%Africa" 
--/-- Selectionne tous les sous-continents qui termine leur nom par "Africa". 5 résultats

-- 6.world.2
SELECT name, capital
FROM countries
WHERE capital LIKE "P%s"
--/-- Selectionne toutes les villes et leur capitale dont la capitale commence par un P majuscule et termine par un s. 3 résultats

-- 6.world.3
SELECT name
FROM cities
WHERE name LIKE "%la"
--/-- Selectionne toutes les villes qui finissent par "la" (2674) 

-- 6.employees.4
SELECT first_name, last_name
FROM employees
WHERE first_name LIKE "G%s" AND last_name LIKE "D%";
--/-- Renvoies tout les noms qui commence par G, finisse par s et dont leurs nom de famille commence par D (9)

-- 6.employees.5
SELECT salary
FROM salaries
WHERE salary LIKE "_5__6";
--/-- 26352 résultats 

--------------------------------------------------------------------------------------
--- IS
---
-- 7.world.1
SELECT *
FROM cities
WHERE name IS NOT NULL;
--/-- 150553 résultats

-- 7.world.2
SELECT *
FROM countries
WHERE name IS NOT NULL;
--/-- 250 résultats

-- 7.world.3
SELECT *
FROM regions
WHERE name IS NULL;
--/-- 0 résultats

-- 7.employees.4
SELECT first_name, last_name
FROM employees
WHERE gender IS not null;
--/-- 300024 résultats

-- 7.employees.5
SELECT dept_name
FROM departments
WHERE dept_name IS null;
--/-- 0 résultats
```

## sql query in the database employees

```sql
-- 1.5
SELECT ci.name
FROM cities as ci
inner join countries as co on ci.country_id = co.id
WHERE ci.country_id = 22
-- 1.5 : SELECTionne tous les noms de ville qui on pour contry id le 22 (Belgique). 

-- 2.1
SELECT emp_no, MAX(salary) AS max_salary
FROM salaries
GROUP BY emp_no;

-- 2.2
SELECT emp.first_name, emp.last_name
FROM employees as emp
inner join dept_emp on dept_emp.emp_no = emp.emp_no
inner join departments on departments.dept_no = dept_emp.dept_no
WHERE departments.dept_name = "Finance"

-- 2.3
SELECT emp.first_name, MAX(sal.salary) AS max_salary
FROM employees AS emp
INNER JOIN salaries AS sal ON sal.emp_no = emp.emp_no
GROUP BY emp.first_name

-- 2.4
SELECT e.first_name, e.last_name
FROM titles as t
inner join employees as e on e.emp_no = t.emp_no
WHERE t.title = "Engineer"

-- 2.5
SELECT e.first_name, s.salary
FROM employees as e
inner join titles as t on t.emp_no = e.emp_no
inner join salaries as s on s.emp_no = e.emp_no
WHERE t.title = "Staff" AND
s.salary BETWEEN 70000 AND 75000

```

2.1 : SELECTionne pour chaque employée son salaire maximal.
2.2 : renvoie les employées (nom, prénom) qui travaille dans le département Finance.
2.3 : renvoie le salaire maximun de tout les employées dont leur prénom commence par un A.
2.3 : Renvoi le nom et prénom de tout les ingénieurs.
2.3 : Renvoi le prénom et le salaire de chaque membre du "Staff" qui on un salaire entre 70k et 75k

## Mission :

For each sql query you have to determine what is their utility.\
Once you have done it you can check for the answer inside the readme.