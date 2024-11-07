# sql_select
solution for select question from hacker rank

###**https://www.hackerrank.com/challenges/weather-observation-station-12/**
Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.
Input Format
The STATION table is described as follows:
|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |
where LAT_N is the northern latitude and LONG_W is the western longitude.

**Solution**
```sql
SELECT DISTINCT CITY FROM STATION WHERE NOT (CITY REGEXP "^[AEIOUaeiou]" or CITY REGEXP "[AEIOUaeiou]$") ORDER BY CITY ASC;
```

###**https://www.hackerrank.com/challenges/more-than-75-marks/**
Query the Name of any student in STUDENTS who scored higher than  Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.
Input Format
The STUDENTS table is described as follows:
|  Column | Type |
|---|---|
| ID  | INTEGER |
| NAME | STRING   |
| MARKS  | INTEGER  |


The Name column only contains uppercase (A-Z) and lowercase (a-z) letters.

Sample Input

|  ID | NAME | MARKS |
|---|---|----|
| 1  | ASHLEY | 81 | 
| 2 | SAMANTHA   | 75 |
| 4  | JULIA  |  76 |
| 3  | JULIA  |  84 |

Sample Output

Ashley
Julia
Belvet
Explanation

Only Ashley, Julia, and Belvet have Marks > 75. If you look at the last three characters of each of their names, there are no duplicates and 'ley' < 'lia' < 'vet'.

**Solution**
```sql
SELECT Name FROM STUDENTS 
WHERE Marks >75
ORDER BY RIGHT(Name, 3) ASC, ID;
```

###**https://www.hackerrank.com/challenges/name-of-employees/**
Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.

Input Format

The Employee table containing employee data for a company is described as follows:

|  Column | Type |
|---|---|
| employee_id  | INTEGER |
| name | STRING   |
| months | INTEGER  |
| salary | INTEGER |

where employee_id is an employee's ID number, name is their name, months is the total number of months they've been working for the company, and salary is their monthly salary.

Sample Input

|  employee_id | name | marks | salary  |
|---|---|----|-----|
| 12228 | Rose | 15 | 1968 |
| 33645 | Angela   | 1 | 3443 |
| 45692  | Frank  | 17  | 1608  |
| 56118  | Patrick  |  7 | 1345
| 59725 | Lisa | 11 | 2330 |
| 74197 | Kimberly   | 16 | 4372 |
| 78454  | Bonnie  |  8 | 1771 |
| 83565 | Michael |  6 | 2017
| 98607  | Todd  |  5 | 3396 |
| 99989 | Joe |  9 | 3573 |

Sample Output
Angela
Bonnie
Frank
Joe
Kimberly
Lisa
Michael
Patrick
Rose
Todd

**Solution**
```sql
SELECT Name FROM EMPLOYEE ORDER BY Name ASC;
```

###**[Employee Salaries](https://www.hackerrank.com/challenges/salary-of-employees/problem)**

Write a query that prints a list of employee names (i.e.: the name attribute) for employees in Employee having a salary greater than $2000 per month who have been employees for less than 10 months. Sort your result by ascending employee_id.

Input Format

The Employee table containing employee data for a company is described as follows:

|  Column | Type |
|---|---|
| employee_id  | INTEGER |
| name | STRING   |
| months | INTEGER  |
| salary | INTEGER |

where employee_id is an employee's ID number, name is their name, months is the total number of months they've been working for the company, and salary is the their monthly salary.

**Solution**
```sql
SELECT Name FROM Employee
WHERE salary >2000 AND months<10
ORDER BY employee_id ASC;
```

###**(https://www.hackerrank.com/challenges/weather-observation-station-15/problem)

Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in STATION that is less than . Round your answer to decimal places.

Input Format

The STATION table is described as follows:


|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |

where LAT_N is the northern latitude and LONG_W is the western longitude.

**Solution**
```sql
select round(LONG_W, 4) from station where LAT_N = (select max(LAT_N) from station where LAT_N<137.2345)
```

###**(https://www.hackerrank.com/challenges/weather-observation-station-16/problem)

Query the smallest Northern Latitude (LAT_N) from STATION that is greater than 38.7780 . Round your answer to 4 decimal places.

Input Format

The STATION table is described as follows:


|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |

where LAT_N is the northern latitude and LONG_W is the western longitude.

**Solution**
```sql
SELECT ROUND(LAT_N, 4) FROM STATION WHERE LAT_N = (SELECT MIN(LAT_N) FROM STATION WHERE LAT_N > 38.7780)
```

###**(https://www.hackerrank.com/challenges/weather-observation-station-17/problem)

Query the Western Longitude (LONG_W)where the smallest Northern Latitude (LAT_N) in STATION is greater than 38.7780 . Round your answer to 4 decimal places.

Input Format

The STATION table is described as follows:


|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |

where LAT_N is the northern latitude and LONG_W is the western longitude.

**Solution**
```sql
SELECT ROUND(LONG_W, 4) FROM STATION WHERE LAT_N = (SELECT MIN(LAT_N) FROM STATION WHERE LAT_N >38.7780) 
```

###**(https://www.hackerrank.com/challenges/weather-observation-station-18/problem)

Consider P1(a, b)and P2(c,d) to be two points on a 2D plane.
a happens to equal the minimum value in Northern Latitude (LAT_N in STATION).
b happens to equal the minimum value in Western Longitude (LONG_W in STATION).
c happens to equal the maximum value in Northern Latitude (LAT_N in STATION).
d happens to equal the maximum value in Western Longitude (LONG_W in STATION).
Query the Manhattan Distance between points P1 and P2 and round it to a scale of 4 decimal places.

Input Format

The STATION table is described as follows:


|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |

where LAT_N is the northern latitude and LONG_W is the western longitude.

**Solution**
```sql
SELECT ROUND((MAX(LAT_N) - MIN(LAT_N) + MAX(LONG_W) - MIN(LONG_W)), 4) AS D
FROM STATION
```

###**(https://www.hackerrank.com/challenges/weather-observation-station-19/problem)

Consider P1(a, b)and P2(c,d) to be two points on a 2D plane.
a happens to equal the minimum value in Northern Latitude (LAT_N in STATION).
c happens to equal the minimum value in Western Longitude (LONG_W in STATION).
b happens to equal the maximum value in Northern Latitude (LAT_N in STATION).
d happens to equal the maximum value in Western Longitude (LONG_W in STATION).
Query the Euclidean Distance between points P1 and P2 and round it to a scale of 4 decimal places.

Input Format

The STATION table is described as follows:


|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |

where LAT_N is the northern latitude and LONG_W is the western longitude.

**Solution**
```sql
SELECT ROUND(
            SQRT(
                POW( (MAX(LAT_N) - MIN(LAT_N)), 2) + 
                POW( (MAX(LONG_W) - MIN(LONG_W)), 2)
            )
        , 4)
FROM STATION
```

###**(https://www.hackerrank.com/challenges/weather-observation-station-20/problem)

A median is defined as a number separating the higher half of a data set from the lower half. Query the median of the Northern Latitudes (LAT_N) from STATION and round your answer to 4 decimal places.

Input Format

The STATION table is described as follows:


|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |

where LAT_N is the northern latitude and LONG_W is the western longitude.

**Solution**
```sql
SELECT ROUND(LAT_N, 4) AS MEDIAN
FROM STATION AS S
WHERE 
(SELECT COUNT(*) FROM STATION WHERE LAT_N > S.LAT_N) = (SELECT COUNT(*) FROM STATION WHERE LAT_N < S.LAT_N)
```
###**([https://www.hackerrank.com/challenges/the-pads/])

Generate the following two result sets:

-- Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).
-- Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format: 

-- There are total [occupation_count] [occupation]s.
-- where [occupation_count] is the number of occurrences of an occupation in OCCUPATIONS and [occupation] is the lowercase occupation name. If more than one Occupation has the same [occupation_count], they should be ordered alphabetically.

**Solution**
```sql
SELECT concat(NAME,'(',LEFT(OCCUPATION,1),')' )AS NAME_PROF FROM OCCUPATIONS ORDER BY NAME ASC ;
SELECT CONCAT("There are a total of ",COUNT(OCCUPATION)," ",LOWER(OCCUPATION),"s.") AS COUNT_PROF FROM OCCUPATIONS GROUP BY OCCUPATION ORDER BY COUNT(OCCUPATION) ASC,LOWER(OCCUPATION) ASC ;
```

###**([https://www.hackerrank.com/challenges/the-pads/])

Pivot the Occupation column in OCCUPATIONS so that each Name is sorted alphabetically and displayed underneath its corresponding Occupation. The output column headers should be Doctor, Professor, Singer, and Actor, respectively.
Note: Print NULL when there are no more names corresponding to an occupation..

**Solution**
```sql
with occupation_order as ( select Occupation, Name, row_number() over(partition by Occupation order by Name) name_order from Occupations ) select MAX(case when Occupation = 'Doctor' then Name else NULL end) as Doctor, MAX(case when Occupation = 'Professor' then Name else NULL end) as Professor, MAX(case when Occupation = 'Singer' then Name else NULL end) as Singer, MAX(case when Occupation = 'Actor' then Name else NULL end) as Actor from occupation_order group by name_order order by name_order;
```

###**([(https://www.hackerrank.com/challenges/binary-search-tree-1/)])

You are given a table, BST, containing two columns: N and P, where N represents the value of a node in Binary Tree, and P is the parent of N. Write a query to find the node type of Binary Tree ordered by the value of the node. Output one of the following for each node:
Root: If node is root node.
Leaf: If node is leaf node.
Inner: If node is neither root nor leaf node.
**Solution**
```sql
(SELECT n, 'Root' AS node_type 
FROM bst 
WHERE p IS NULL
UNION 
SELECT n, 'Inner' 
FROM bst 
WHERE n IN (SELECT DISTINCT p FROM bst) AND p is not null
UNION 
SELECT n, 'Leaf' 
FROM bst 
WHERE n NOT IN (select distinct p from bst where p is not null))
ORDER BY n;
```
###**([(https://www.hackerrank.com/challenges/the-company/)])

- Amber's conglomerate corporation just acquired some new companies. Each of the companies follows this hierarchy: 
-- Given the table schemas below, write a query to print the company_code, founder name, total number of lead managers, total number of senior managers, total number of managers, and total number of employees. Order your output by ascending company_code.
-- Note:
-- The tables may contain duplicate records.
-- The company_code is string, so the sorting should not be numeric. For example, if the company_codes are C_1, C_2, and C_10, then the ascending company_codes will be C_1, C_10, and C_2.

**Solution**
```sql
SELECT C.company_code, founder, num_lm, num_sm, num_m, num_e
FROM Company AS C
JOIN (SELECT company_code, count(distinct lead_manager_code) AS num_lm
     FROM Lead_Manager
     GROUP BY company_code) AS LM ON C.company_code = LM.company_code
JOIN (SELECT company_code, count(distinct senior_manager_code) AS num_sm
     FROM Senior_Manager
     GROUP BY company_code) AS SM ON C.company_code = SM.company_code
JOIN (SELECT company_code, count(distinct manager_code) AS num_m
     FROM Manager
     GROUP BY company_code) AS M ON C.company_code = M.company_code
JOIN (SELECT company_code, count(distinct employee_code) AS num_e
     FROM Employee
     GROUP BY company_code) AS E ON C.company_code = E.company_code
ORDER BY C.company_code
```

###**([https://www.hackerrank.com/challenges/weather-observation-station-13/])
PrepareSQLAggregationWeather Observation Station 13
Query the sum of Northern Latitudes (LAT_N) from STATION having values greater than 38.7880 and less than 137.2345. Truncate your answer to  4 decimal places.

**Solution**
```sql
SELECT ROUND(SUM(LAT_N), 4) FROM STATION WHERE LAT_N > 38.7880 AND LAT_N < 137.2345
```

###**([https://www.hackerrank.com/challenges/weather-observation-station-14/])
PrepareSQLAggregationWeather Observation Station 14
Query the greatest value of the Northern Latitudes (LAT_N) from STATION that is less than 137.2345 . Truncate your answer to 4 decimal places.

**Solution**
```sql
SELECT ROUND(MAX(LAT_N), 4) FROM STATION WHERE LAT_N < 137.2345
```

###**([https://www.hackerrank.com/challenges/symmetric-pairs/problem])
PrepareSQLAdvanced Join Symmetric Pairs
-- You are given a table, Functions, containing two columns: X and Y. Y is the value of some function F at X -- i.e. Y = F(X).
-- Two pairs (X1, Y1) and (X2, Y2) are said to be symmetric pairs if X1 = Y2 and X2 = Y1.
-- Write a query to output all such symmetric pairs in ascending order by the value of X.

**Solution**
```sql
SELECT Distinct A.X, A.Y
FROM Functions AS A
JOIN Functions AS B
ON A.X = B.Y
AND B.X = A.Y
where A.X < A.Y

union

SELECT Distinct X, Y
FROM Functions 
where X = Y
group by X, Y
having count(*) > 1

order by X
```


###**([(https://www.hackerrank.com/challenges/interviews/problem)])
PrepareSQLAdvanced JoinInterviews

Samantha interviews many candidates from different colleges using coding challenges and contests. Write a query to print the contest_id, hacker_id, name, and the sums of total_submissions, total_accepted_submissions, total_views, and total_unique_views for each contest sorted by contest_id. Exclude the contest from the result if all four sums are 0.
-- Note: A specific contest can be used to screen candidates at more than one college, but each college only holds screening contest.

**Solution**
```sql
SELECT CT.contest_id, CT.hacker_id, CT.name, SUM(TS), SUM(TAS), SUM(TV), SUM(TUV)
FROM Contests AS CT
JOIN Colleges AS CL ON CT.contest_id = CL.contest_id
JOIN Challenges AS CH ON CH.college_id = CL.college_id
left JOIN ( SELECT CHALLENGE_ID, SUM(total_views) AS TV, SUM(total_unique_views) AS TUV FROM View_Stats GROUP BY CHALLENGE_ID )  VS ON CH.challenge_id = VS.challenge_id
left JOIN (SELECT CHALLENGE_ID, SUM(TOTAL_SUBMISSIONS) AS TS, SUM(TOTAL_ACCEPTED_SUBMISSIONS) AS TAS FROM Submission_Stats GROUP BY CHALLENGE_ID ) AS SS ON CH.challenge_id = SS.challenge_id
GROUP BY CT.contest_id
ORDER BY CT.contest_id
```


###**([(https://www.hackerrank.com/challenges/interviews/problem)])
PrepareSQLAdvanced JoinInterviews

Samantha interviews many candidates from different colleges using coding challenges and contests. Write a query to print the contest_id, hacker_id, name, and the sums of total_submissions, total_accepted_submissions, total_views, and total_unique_views for each contest sorted by contest_id. Exclude the contest from the result if all four sums are 0.
-- Note: A specific contest can be used to screen candidates at more than one college, but each college only holds screening contest.

**Solution**
```sql
SELECT CT.contest_id, CT.hacker_id, CT.name, SUM(TS), SUM(TAS), SUM(TV), SUM(TUV)
FROM Contests AS CT
JOIN Colleges AS CL ON CT.contest_id = CL.contest_id
JOIN Challenges AS CH ON CH.college_id = CL.college_id
left JOIN ( SELECT CHALLENGE_ID, SUM(total_views) AS TV, SUM(total_unique_views) AS TUV FROM View_Stats GROUP BY CHALLENGE_ID )  VS ON CH.challenge_id = VS.challenge_id
left JOIN (SELECT CHALLENGE_ID, SUM(TOTAL_SUBMISSIONS) AS TS, SUM(TOTAL_ACCEPTED_SUBMISSIONS) AS TAS FROM Submission_Stats GROUP BY CHALLENGE_ID ) AS SS ON CH.challenge_id = SS.challenge_id
GROUP BY CT.contest_id
ORDER BY CT.contest_id
```


