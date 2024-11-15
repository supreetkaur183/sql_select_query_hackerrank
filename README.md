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

SELECT
    con.contest_id,
    con.hacker_id,
    con.name,
    SUM(s.total_submissions) as total_submissions,
    SUM(s.total_accepted_submissions)  as total_accepted_submissions,
    SUM(vs.total_views)  as total_views,
    SUM(vs.total_unique_views) as total_unique_views
FROM contests as con
    LEFT JOIN colleges  as col
        ON con.contest_id = col.contest_id
    LEFT JOIN challenges  as ch
        ON ch.college_id = col.college_id
    LEFT JOIN (
        SELECT
            challenge_id,
            SUM(total_submissions)  as total_submissions,
            SUM(total_accepted_submissions) as total_accepted_submissions
        FROM Submission_Stats
        GROUP BY challenge_id
    ) as s
        ON s.challenge_id = ch.challenge_id
    LEFT JOIN (
        SELECT
            challenge_id,
            SUM(total_views) as total_views,
            SUM(total_unique_views) as total_unique_views
        FROM view_stats
        GROUP BY challenge_id
    ) as vs
        ON vs.challenge_id = ch.challenge_id
GROUP BY con.contest_id, con.hacker_id, con.name
HAVING SUM(vs.total_views) + SUM(s.total_submissions) > 0
ORDER BY con.contest_id
```


###**([https://www.hackerrank.com/challenges/15-days-of-learning-sql/problem])
PrepareSQLAdvanced Join15 Days of Learning SQL

Julia conducted a  days of learning SQL contest. The start date of the contest was March 01, 2016 and the end date was March 15, 2016.
Write a query to print total number of unique hackers who made at least  submission each day (starting on the first day of the contest), and find the hacker_id and name of the hacker who made maximum number of submissions each day. If more than one such hacker has a maximum number of submissions, print the lowest hacker_id. The query should print this information for each day of the contest, sorted by the date.

**Solution**
```sql
SELECT SUBMISSION_DATE,
(SELECT COUNT(DISTINCT HACKER_ID)  
 FROM SUBMISSIONS S2  
 WHERE S2.SUBMISSION_DATE = S1.SUBMISSION_DATE AND    
(SELECT COUNT(DISTINCT S3.SUBMISSION_DATE) 
 FROM SUBMISSIONS S3 WHERE S3.HACKER_ID = S2.HACKER_ID AND S3.SUBMISSION_DATE < S1.SUBMISSION_DATE) = DATEDIFF(S1.SUBMISSION_DATE , '2016-03-01')),
(SELECT HACKER_ID FROM SUBMISSIONS S2 WHERE S2.SUBMISSION_DATE = S1.SUBMISSION_DATE 
GROUP BY HACKER_ID ORDER BY COUNT(SUBMISSION_ID) DESC, HACKER_ID LIMIT 1) AS TMP,
(SELECT NAME FROM HACKERS WHERE HACKER_ID = TMP)
FROM
(SELECT DISTINCT SUBMISSION_DATE FROM SUBMISSIONS) S1
GROUP BY SUBMISSION_DATE;
```

###**([https://www.hackerrank.com/challenges/the-blunder/problem])
PrepareSQLAggregationThe Blunder
Samantha was tasked with calculating the average monthly salaries for all employees in the EMPLOYEES table, but did not realize her keyboard's key was broken until after completing the calculation. She wants your help finding the difference between her miscalculation (using salaries with any zeros removed), and the actual average salary.
Write a query calculating the amount of error (i.e.:  average monthly salaries), and round it up to the next integer.

**Solution**
```sql
select ceil(avg(salary)- avg(Replace(salary,'0',''))) from employees
```

###**([https://www.hackerrank.com/challenges/earnings-of-employees/problem])
PrepareSQLAggregationTop Earners
We define an employee's total earnings to be their monthly salary * months worked, and the maximum total earnings to be the maximum total earnings for any employee in the Employee table. Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings. Then print these values as  space-separated integers.

**Solution**
```sql

select max(salary * months), count(salary * months) from employee group by (salary * months) desc limit 1;
```

###**([https://www.hackerrank.com/challenges/the-report/problem])
PrepareSQLBasic JoinThe Report
You are given two tables: Students and Grades. Students contains three columns ID, Name and Marks. Ketty gives Eve a task to generate a report containing three columns: Name, Grade and Mark. Ketty doesn't want the NAMES of those students who received a grade lower than 8. The report must be in descending order by grade -- i.e. higher grades are entered first. If there is more than one student with the same grade (8-10) assigned to them, order those particular students by their name alphabetically. Finally, if the grade is lower than 8, use "NULL" as their name and list them by their grades in descending order. If there is more than one student with the same grade (1-7) assigned to them, order those particular students by their marks in ascending order.
Write a query to help Eve

**Solution**
```sql
select (case when g.grade >=8 then s.name else null end), g.grade, s.marks from students s join grades g on s.marks between g.min_mark and g.max_mark order by g.grade desc, s.name asc, s.marks asc
```

###**([https://www.hackerrank.com/challenges/full-score/problem])
PrepareSQLBasic JoinTop Competitors
Julia just finished conducting a coding contest, and she needs your help assembling the leaderboard! Write a query to print the respective hacker_id and name of hackers who achieved full scores for more than one challenge. Order your output in descending order by the total number of challenges in which the hacker earned a full score. If more than one hacker received full scores in same number of challenges, then sort them by ascending hacker_id.

**Solution**
```sql
SELECT S.hacker_id, H.name FROM Hackers H left JOIN Submissions S ON S.hacker_id = H.hacker_id left JOIN Challenges CH ON S.challenge_id = CH.challenge_id left JOIN Difficulty D ON CH.difficulty_level = D.difficulty_level WHERE S.score = D.score
GROUP BY S.hacker_id, H.name HAVING COUNT(DISTINCT S.challenge_id) > 1 ORDER BY count(s.hacker_id) DESC, S.hacker_id ASC
```

###**([https://www.hackerrank.com/challenges/harry-potter-and-wands/problem])
PrepareSQLBasic JoinOllivander's Inventory
Harry Potter and his friends are at Ollivander's with Ron, finally replacing Charlie's old broken wand.
Hermione decides the best way to choose is by determining the minimum number of gold galleons needed to buy each non-evil wand of high power and age. Write a query to print the id, age, coins_needed, and power of the wands that Ron's interested in, sorted in order of descending power. If more than one wand has same power, sort the result in order of descending age.

**Solution**
```sql
SELECT W.ID, P.AGE, W.COINS_NEEDED, W.POWER 
FROM WANDS AS W
JOIN WANDS_PROPERTY AS P
ON (W.CODE = P.CODE) 
WHERE P.IS_EVIL = 0 AND W.COINS_NEEDED = (SELECT MIN(COINS_NEEDED) 
                                          FROM WANDS AS X
                                          JOIN WANDS_PROPERTY AS Y 
                                          ON (X.CODE = Y.CODE) 
                                          WHERE X.POWER = W.POWER AND Y.AGE = P.AGE) 
ORDER BY W.POWER DESC, P.AGE DESC;
```

###**([https://www.hackerrank.com/challenges/challenges/problem])
PrepareSQLBasic JoinChallenges
Julia asked her students to create some coding challenges. Write a query to print the hacker_id, name, and the total number of challenges created by each student. Sort your results by the total number of challenges in descending order. If more than one student created the same number of challenges, then sort the result by hacker_id. If more than one student created the same number of challenges and the count is less than the maximum number of challenges created, then exclude those students from the result.

**Solution**
```sql
SELECT H.HACKER_ID, 
       H.NAME, 
       COUNT(C.CHALLENGE_ID) AS C_COUNT
FROM HACKERS H
JOIN CHALLENGES C ON C.HACKER_ID = H.HACKER_ID
GROUP BY H.HACKER_ID, H.NAME
HAVING C_COUNT = 
    (SELECT COUNT(C2.CHALLENGE_ID) AS C_MAX
     FROM CHALLENGES AS C2
     GROUP BY C2.HACKER_ID 
     ORDER BY C_MAX DESC LIMIT 1)
OR C_COUNT IN 
    (SELECT DISTINCT C_COMPARE AS C_UNIQUE
     FROM (SELECT H2.HACKER_ID, 
                  H2.NAME, 
                  COUNT(CHALLENGE_ID) AS C_COMPARE
           FROM HACKERS H2
           JOIN CHALLENGES C ON C.HACKER_ID = H2.HACKER_ID
           GROUP BY H2.HACKER_ID, H2.NAME) COUNTS
     GROUP BY C_COMPARE
     HAVING COUNT(C_COMPARE) = 1)
ORDER BY C_COUNT DESC, H.HACKER_ID;
/*
OR
*/
WITH cte AS ( SELECT c.hacker_id, h.name, COUNT(c.challenge_id) AS cc 
             FROM Challenges AS c 
             JOIN Hackers AS h 
             ON c.hacker_id = h.hacker_id 
             GROUP BY c.hacker_id, h.name ) 
SELECT hacker_id, name, cc 
FROM cte 
WHERE cc = (SELECT MAX(cc) FROM cte) 
or cc in ( SELECT cc FROM cte 
          GROUP BY cc 
          HAVING COUNT(cc) = 1 ) 
ORDER BY cc DESC, hacker_id;
```
###**([https://www.hackerrank.com/challenges/contest-leaderboard/problem])
PrepareSQLBasic JoinContest Leaderboard
You did such a great job helping Julia with her last coding contest challenge that she wants you to work on this one, too!
The total score of a hacker is the sum of their maximum scores for all of the challenges. Write a query to print the hacker_id, name, and total score of the hackers ordered by the descending score. If more than one hacker achieved the same total score, then sort the result by ascending hacker_id. Exclude all hackers with a total score of  from your result.

**Solution**
```sql
with cte1 as 
    (select s.hacker_id, h.name, s.challenge_id, max(s.score) as scores 
    from submissions  as s 
    join hackers as h 
    on h.hacker_id=s.hacker_id 
    group by s.hacker_id,h.name, s.challenge_id ) 
 select hacker_id, name, sum(scores) as sumscore 
 from cte1 
 group by hacker_id, name 
 having sum(scores) > 0 
 order by sumscore desc, hacker_id asc;
```

###**([https://www.hackerrank.com/challenges/sql-projects/problem])
PrepareSQLAdvanced JoinSQL Project Planning
You are given a table, Projects, containing three columns: Task_ID, Start_Date and End_Date. It is guaranteed that the difference between the End_Date and the Start_Date is equal to 1 day for each row in the table.If the End_Date of the tasks are consecutive, then they are part of the same project. Samantha is interested in finding the total number of different projects completed.
Write a query to output the start and end dates of projects listed by the number of days it took to complete the project in ascending order. If there is more than one project that have the same number of completion days, then order by the start date of the project.

**Solution**
```sql
WITH numbered_projects AS (
                            SELECT start_date, end_date, 
                            ROW_NUMBER() OVER (ORDER BY end_date) AS rn 
                            FROM projects
                           )
SELECT MIN(start_date) AS pes, MAX(end_date) AS ped
FROM numbered_projects
GROUP BY DATE_SUB(end_date, INTERVAL rn DAY)
ORDER BY (ped - pes);
```

###**([https://www.hackerrank.com/challenges/placements/problem])
PrepareSQLAdvanced JoinPlacements
You are given three tables: Students, Friends and Packages. Students contains two columns: ID and Name. Friends contains two columns: ID and Friend_ID (ID of the ONLY best friend). Packages contains two columns: ID and Salary (offered salary in $ thousands per month).Write a query to output the names of those students whose best friends got offered a higher salary than them. Names must be ordered by the salary amount offered to the best friends. It is guaranteed that no two students got same salary offer.

**Solution**
```sql
SELECT s.Name
FROM Students AS s
LEFT JOIN Friends AS f 
ON s.ID = f.ID
LEFT JOIN Packages AS p_stu
ON s.ID = p_stu.ID
LEFT JOIN Packages AS p_fri
ON f.Friend_ID = p_fri.ID
WHERE  p_fri.Salary > p_stu.Salary
ORDER BY p_fri.Salary ASC
```
