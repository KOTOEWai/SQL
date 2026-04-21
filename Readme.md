# SQL (Structured Query Language)

---

## Table of Contents

- [What is SQL?](#what-is-sql)
- [SQL Introduction](#sql-introduction)
- [SQL ၏ အဓိက အမျိုးအစားများ](#sql-၏-အဓိက-အမျိုးအစားများ)
- [အခြေခံ Commands များ](#အခြေခံ-commands-များ)
  - [CREATE & INSERT](#database-နှင့်-table-ဖန်တီးခြင်း-ddl)
  - [SELECT](#data-ရှာဖွေခြင်း-select)
  - [UPDATE](#data-ပြင်ဆင်ခြင်း-update)
  - [DELETE](#data-ဖျက်ခြင်း-delete)
- [WHERE Clause](#where-clause-အသေးစိတ်)
- [Aggregate Functions](#aggregate-functions)
- [JOIN များ](#join-များ)
- [Constraints](#constraints-ကန့်သတ်ချက်များ)
- [Subquery](#subquery)
- [အသုံးဝင်သောနည်းပညာများ](#အသုံးဝင်သောနည်းပညာများ)
- [လေ့ကျင့်ရန် နမူနာ Queries](#လေ့ကျင့်ရန်-နမူနာ-queries)
- [နောက်ထပ် လေ့လာရန်](#နောက်ထပ်-လေ့လာရန်-အကြံပြုချက်)

---

## What is SQL?

**SQL** (**S**tructured **Q**uery **L**anguage) ဆိုသည်မှာ **Relational Database** များကို စီမံခန့်ခွဲရန် အသုံးပြုသော standard ဘာသာစကားတစ်မျိုးဖြစ်သည်။

> SQL ကို **"sequel"** ဟု အသံထွက်နိုင်သည်။

### SQL ဖြင့် ဘာတွေ လုပ်နိုင်သလဲ?

| လုပ်ဆောင်ချက် | ရှင်းလင်းချက် |
|---|---|
| **Create** | Database နှင့် Table ဖန်တီးနိုင်သည် |
| **Read** | Data ကို ရှာဖွေ ဖတ်ရှု နိုင်သည် |
| **Update** | Data ကို ပြင်ဆင် မွမ်းမံ နိုင်သည် |
| **Delete** | Data ကို ဖျက်ပစ် နိုင်သည် |

### SQL ကို မည်သည့် Database များတွင် သုံးသနည်း?

```
MySQL  •  PostgreSQL  •  Microsoft SQL Server  •  SQLite  •  Oracle  •  MariaDB
```

[Back to Top](#sql-structured-query-language)

---

## SQL Introduction

### သမိုင်းကြောင်း

SQL ကို **1970** ခုနှစ်တွင် IBM မှ **Donald D. Chamberlin** နှင့် **Raymond F. Boyce** တို့ဖွဲ့ဖန်တီးခဲ့သည်။ **1987** ခုနှစ်တွင် ISO Standard အဖြစ် အသိအမှတ်ပြုခဲ့ပြီး ယနေ့တိုင် ကမ္ဘာ့ Data Engineering နှင့် Backend Development တွင် မရှိမဖြစ် ဘာသာစကားတစ်ခုဖြစ်သည်။

### Relational Database ဆိုတာ ဘာလဲ?

Data ကို **Table** (row နှင့် column) ပုံစံဖြင့် သိမ်းဆည်းသောနည်းစနစ်ဖြစ်သည်။ Excel Spreadsheet နှင့် ဆင်တူသော်လည်း ထိုထက် အဆမတန် ပိုမို အစွမ်းထက်သည်။

**ဥပမာ - students Table:**

| id | name     | age | grade |
|----|----------|-----|-------|
| 1  | Mg Mg    | 20  | A     |
| 2  | Su Su    | 19  | B     |
| 3  | Ko Ko    | 21  | A     |

### SQL ၏ အပိုင်းများ (Anatomy of a SQL Statement)

```sql
SELECT  name, age          -- ဘာကို ယူမည်ဆိုသော Column များ
FROM    students           -- မည်သည့် Table မှ ယူမည်
WHERE   grade = 'A'        -- မည်သည့် အချက်အလက်ကို စစ်ထုတ်မည်
ORDER BY age DESC          -- မည်သို့ စီစဉ်မည်
LIMIT   10;                -- မည်မျှ ယူမည်
```

### SQL ကို ဘာကြောင့် သင်ရမလဲ?

- **Data Analyst** — Data ကို စစ်ဆေးလေ့လာနိုင်ရန်
- **Backend Developer** — Database နှင့် ချိတ်ဆက် Applications တည်ဆောက်နိုင်ရန်
- **Data Engineer / Scientist** — Big Data pipeline များ ဆောက်နိုင်ရန်
- **Interview** — Tech company အများစုတွင် SQL test ဖြေဆိုရသည်

[Back to Top](#sql-structured-query-language)

---

## SQL ၏ အဓိက အမျိုးအစားများ

| အမျိုးအစား | အမည် | ဥပမာ Command များ |
|---|---|---|
| **DDL** | Data Definition Language | `CREATE`, `ALTER`, `DROP` |
| **DML** | Data Manipulation Language | `SELECT`, `INSERT`, `UPDATE`, `DELETE` |
| **DCL** | Data Control Language | `GRANT`, `REVOKE` |
| **TCL** | Transaction Control Language | `COMMIT`, `ROLLBACK` |

[Back to Top](#sql-structured-query-language)

---

## အခြေခံ Commands များ

### Database နှင့် Table ဖန်တီးခြင်း (DDL)

```sql
-- Database တစ်ခုဖန်တီးခြင်း
CREATE DATABASE school;

-- Database ကိုသုံးခြင်း
USE school;

-- Table တစ်ခုဖန်တီးခြင်း
CREATE TABLE students (
    id         INT PRIMARY KEY AUTO_INCREMENT,
    name       VARCHAR(100) NOT NULL,
    age        INT,
    grade      CHAR(1),
    email      VARCHAR(150) UNIQUE,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP
);
```

### Data ထည့်သွင်းခြင်း (INSERT)

```sql
-- တစ်ကြောင်းတည်း ထည့်သွင်း
INSERT INTO students (name, age, grade, email)
VALUES ('Mg Mg', 20, 'A', 'mgmg@example.com');

-- တစ်ကြောင်းထက်မက ထည့်သွင်း
INSERT INTO students (name, age, grade, email)
VALUES
    ('Su Su',   19, 'B', 'susu@example.com'),
    ('Ko Ko',   21, 'A', 'koko@example.com'),
    ('Ma Hnin', 22, 'C', 'mahnin@example.com');
```

### Data ရှာဖွေခြင်း (SELECT)

```sql
-- Column အားလုံး ကြည့်ခြင်း
SELECT * FROM students;

-- သတ်မှတ် Column များသာ ကြည့်ခြင်း
SELECT name, age, grade FROM students;

-- စစ်ထုတ်ခြင်း (WHERE)
SELECT * FROM students WHERE grade = 'A';

-- စီစဉ်ခြင်း (ORDER BY)
SELECT * FROM students ORDER BY age ASC;   -- ငယ်မှကြီး
SELECT * FROM students ORDER BY age DESC;  -- ကြီးမှငယ်

-- အကန့်အသတ်ဖြင့် ယူခြင်း (LIMIT)
SELECT * FROM students LIMIT 5;
```

### Data ပြင်ဆင်ခြင်း (UPDATE)

```sql
UPDATE students
SET grade = 'A', age = 23
WHERE id = 3;
```

> **သတိပေးချက်**: `WHERE` မပါဘဲ `UPDATE` လုပ်ပါက Row **အားလုံး** ပြောင်းသွားမည်!

### Data ဖျက်ခြင်း (DELETE)

```sql
-- တစ်ကြောင်းတည်း ဖျက်ပစ်ခြင်း
DELETE FROM students WHERE id = 2;

-- Record အားလုံး ဖျက် (Table structure ကျန်)
DELETE FROM students;

-- Table အပြည့်အဝ ရှင်းလင်းခြင်း
TRUNCATE TABLE students;
```

[Back to Top](#sql-structured-query-language)

---

## WHERE Clause အသေးစိတ်

```sql
-- နှိုင်းယှဉ် Operators
SELECT * FROM students WHERE age > 20;
SELECT * FROM students WHERE age >= 20;
SELECT * FROM students WHERE age != 20;

-- AND / OR
SELECT * FROM students WHERE age > 18 AND grade = 'A';
SELECT * FROM students WHERE grade = 'A' OR grade = 'B';

-- BETWEEN
SELECT * FROM students WHERE age BETWEEN 18 AND 22;

-- IN
SELECT * FROM students WHERE grade IN ('A', 'B');

-- LIKE (pattern ရှာဖွေခြင်း)
SELECT * FROM students WHERE name LIKE 'Mg%';   -- Mg နှင့်စသော
SELECT * FROM students WHERE name LIKE '%Ko';   -- Ko နှင့်ဆုံးသော
SELECT * FROM students WHERE name LIKE '%u%';   -- u ပါသော

-- NULL စစ်ဆေးခြင်း
SELECT * FROM students WHERE email IS NULL;
SELECT * FROM students WHERE email IS NOT NULL;
```

[Back to Top](#sql-structured-query-language)

---

## Aggregate Functions

```sql
SELECT COUNT(*) AS total_students FROM students;        -- ဦးရေ
SELECT AVG(age)  AS average_age   FROM students;        -- ပျမ်းမျှ
SELECT MAX(age)  AS oldest        FROM students;        -- အကြီးဆုံး
SELECT MIN(age)  AS youngest      FROM students;        -- အငယ်ဆုံး
SELECT SUM(age)  AS total_age     FROM students;        -- ပေါင်းလဒ်

-- Grade အလိုက် အုပ်စုဖွဲ့ ရေတွက် (GROUP BY)
SELECT grade, COUNT(*) AS count
FROM students
GROUP BY grade;

-- GROUP BY အပြီး စစ်ထုတ်ခြင်း (HAVING)
SELECT grade, COUNT(*) AS count
FROM students
GROUP BY grade
HAVING COUNT(*) > 1;
```

[Back to Top](#sql-structured-query-language)

---

## JOIN များ

```sql
-- ဥပမာ Table ဖန်တီးခြင်း
CREATE TABLE courses (
    id         INT PRIMARY KEY AUTO_INCREMENT,
    name       VARCHAR(100),
    student_id INT,
    FOREIGN KEY (student_id) REFERENCES students(id)
);
```

### INNER JOIN — နှစ်ဖက်လုံးတွင် ကိုက်ညီသော record များ

```sql
SELECT s.name, c.name AS course
FROM students s
INNER JOIN courses c ON s.id = c.student_id;
```

### LEFT JOIN — ဘယ်ဘက် Table အားလုံး

```sql
SELECT s.name, c.name AS course
FROM students s
LEFT JOIN courses c ON s.id = c.student_id;
```

### RIGHT JOIN — ညာဘက် Table အားလုံး

```sql
SELECT s.name, c.name AS course
FROM students s
RIGHT JOIN courses c ON s.id = c.student_id;
```

[Back to Top](#sql-structured-query-language)

---

## Constraints (ကန့်သတ်ချက်များ)

```sql
CREATE TABLE employees (
    id       INT PRIMARY KEY AUTO_INCREMENT,      -- Unique identifier
    emp_code VARCHAR(10) UNIQUE,                  -- ထပ်တူမရှိနိုင်
    name     VARCHAR(100) NOT NULL,               -- NULL မဖြစ်ရ
    salary   DECIMAL(10,2) DEFAULT 0.00,          -- Default တန်ဖိုး
    dept_id  INT,
    FOREIGN KEY (dept_id) REFERENCES departments(id)
);
```

[Back to Top](#sql-structured-query-language)

---

## Subquery

Query တစ်ခုထဲတွင် Query တစ်ခုထပ်ထည့်ခြင်း

```sql
-- Grade 'A' ရသော ကျောင်းသားများ၏ courses ကိုကြည့်ခြင်း
SELECT * FROM courses
WHERE student_id IN (
    SELECT id FROM students WHERE grade = 'A'
);
```

[Back to Top](#sql-structured-query-language)

---

## အသုံးဝင်သောနည်းပညာများ

```sql
-- DISTINCT - ထပ်တူများ ဖယ်ရှားခြင်း
SELECT DISTINCT grade FROM students;

-- ALIAS - ခေါင်းစဉ် ပြောင်းလဲခြင်း
SELECT name AS 'ကျောင်းသားအမည်', age AS 'အသက်' FROM students;

-- String Functions
SELECT UPPER(name)                    FROM students;  -- အကြီးစာ
SELECT LOWER(name)                    FROM students;  -- အသေးစာ
SELECT LENGTH(name)                   FROM students;  -- စာလုံးရေ
SELECT CONCAT(name, ' - ', grade)     FROM students;  -- ပေါင်းစပ်

-- Date Functions
SELECT NOW();                                         -- လက်ရှိ DateTime
SELECT CURDATE();                                     -- လက်ရှိ Date
SELECT YEAR(created_at) FROM students;                -- နှစ်ကိုထုတ်ယူ
```

[Back to Top](#sql-structured-query-language)

---

## လေ့ကျင့်ရန် နမူနာ Queries

```sql
-- ကျောင်းသား မှတ်ပုံတင်စာရင်း အပြည့်အစုံ
SELECT
    s.id,
    s.name,
    s.age,
    s.grade,
    COUNT(c.id) AS total_courses
FROM students s
LEFT JOIN courses c ON s.id = c.student_id
GROUP BY s.id, s.name, s.age, s.grade
ORDER BY s.grade ASC, s.name ASC;
```

[Back to Top](#sql-structured-query-language)

---

## နောက်ထပ် လေ့လာရန် အကြံပြုချက်

1. **SQLZoo** — [sqlzoo.net](https://sqlzoo.net) တွင် Interactive လေ့ကျင့်ပါ
2. **LeetCode** — SQL Interview questions များ ဖြေဆိုလေ့ကျင့်ပါ
3. **Mode Analytics** — Real-world SQL practice ပြုလုပ်ပါ
4. **PostgreSQL Docs** — [postgresql.org/docs](https://www.postgresql.org/docs/) တွင် reference ကြည့်ပါ

[Back to Top](#sql-structured-query-language)

---

*ဤ document ကို SQL Exercises Folder တွင် reference အဖြစ်သုံးနိုင်သည်။*
