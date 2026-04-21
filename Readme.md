# SQL (Structured Query Language)

---

## Table of Contents

- [What is SQL?](#what-is-sql)
- [SQL Introduction](#sql-introduction)
- [SQL ၏ အဓိက အမျိုးအစားများ](#sql-၏-အဓိက-အမျိုးအစားများ)
- [SQL Data Types](#sql-data-types)
- [SQL: Querying Data With SELECT ](#SQL-Querying-Data-With-SELECT)
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

## SQL Data Types

SQL တွင် Column တစ်ခုချင်းဆီတွင် မည်သည့် Data မျိုးကို သိမ်းဆည်းမည်ဆိုသည်ကို **Data Type** ဖြင့် သတ်မှတ်သည်။

---

### 1. Numeric Types (ဂဏန်းဆိုင်ရာ)

| Data Type | ရှင်းလင်းချက် | ဥပမာ |
|---|---|---|
| `INT` | ကိန်းဂဏန်း (−2B မှ 2B) | `age INT` |
| `TINYINT` | သေးငယ်သော ကိန်းဂဏန်း (0−255) | `is_active TINYINT` |
| `BIGINT` | ကြီးမားသော ကိန်းဂဏန်း | `population BIGINT` |
| `FLOAT` | ကိုက်ကိန်း (သတ်မှတ်ချက်မဲ့) | `height FLOAT` |
| `DOUBLE` | ကိုက်ကိန်း (ပိုမှန်ကန်) | `price DOUBLE` |
| `DECIMAL(p,s)` | တိကျသော ကိုက်ကိန်း | `salary DECIMAL(10,2)` |

```sql
CREATE TABLE products (
    id       INT PRIMARY KEY AUTO_INCREMENT,
    quantity INT,
    price    DECIMAL(10, 2),   -- Decimal(p,s)
    weight   FLOAT
);
```

---

### 2. String Types (စာသားဆိုင်ရာ)

| Data Type | ရှင်းလင်းချက် | ဥပမာ |
|---|---|---|
| `CHAR(n)` | ပုံသေ အရှည် စာကြောင်း | `gender CHAR(1)` |
| `VARCHAR(n)` | အပြောင်းအလဲ အရှည် စာကြောင်း | `name VARCHAR(100)` |
| `TEXT` | ရှည်သော စာသား (64KB) | `description TEXT` |
| `MEDIUMTEXT` | အလတ်စား စာသား (16MB) | `article MEDIUMTEXT` |
| `LONGTEXT` | ကြီးမားသော စာသား (4GB) | `content LONGTEXT` |
| `ENUM` | သတ်မှတ်ထားသော တန်ဖိုးများ | `status ENUM(...)` |

```sql
CREATE TABLE users (
    id       INT PRIMARY KEY AUTO_INCREMENT,
    name     VARCHAR(100),              -- အများဆုံး 100 လုံး
    gender   CHAR(1),                  -- 'M' သို့ 'F'
    bio      TEXT,                     -- ရှည်သော ကိုယ်ရေးအကျဉ်း
    status   ENUM('active', 'inactive', 'banned')
);
```

> **CHAR vs VARCHAR**
> - `CHAR(10)` — "Hi" သိမ်းလျှင် 10 bytes အမြဲသုံးသည်
> - `VARCHAR(10)` — "Hi" သိမ်းလျှင် 2 bytes သာ သုံးသည် (သက်သာသည်)

---

### 3. Date & Time Types (ရက်စွဲနှင့် အချိန်)

| Data Type | ပုံစံ | ဥပမာတန်ဖိုး |
|---|---|---|
| `DATE` | `YYYY-MM-DD` | `2025-04-21` |
| `TIME` | `HH:MM:SS` | `10:30:00` |
| `DATETIME` | `YYYY-MM-DD HH:MM:SS` | `2025-04-21 10:30:00` |
| `TIMESTAMP` | `YYYY-MM-DD HH:MM:SS` | Auto-update လုပ်နိုင် |
| `YEAR` | `YYYY` | `2025` |

```sql
CREATE TABLE orders (
    id           INT PRIMARY KEY AUTO_INCREMENT,
    order_date   DATE,
    order_time   TIME,
    created_at   DATETIME DEFAULT CURRENT_TIMESTAMP,
    updated_at   TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

---

### 4. Boolean Type

MySQL တွင် `BOOLEAN` သည် `TINYINT(1)` ဖြင့် သိမ်းဆည်းသည်။

```sql
CREATE TABLE tasks (
    id         INT PRIMARY KEY AUTO_INCREMENT,
    title      VARCHAR(200),
    is_done    BOOLEAN DEFAULT FALSE   -- 0 = false, 1 = true
);

-- Insert example
INSERT INTO tasks (title, is_done) VALUES ('Learn SQL', TRUE);
INSERT INTO tasks (title, is_done) VALUES ('Learn Python', FALSE);
```

---

### 5. Data Type ရွေးချယ်ရန် လမ်းညွှန်

| သိမ်းဆည်းမည့် Data | အသုံးပြုသင့်သော Type |
|---|---|
| ID, ဦးရေ, သက်တမ်း | `INT` |
| ငွေကြေး, ဈေးနှုန်း | `DECIMAL(10,2)` |
| အမည်, ခေါင်းစဉ် | `VARCHAR(100-255)` |
| ရှည်သော ဖော်ပြချက် | `TEXT` |
| ရက်စွဲသာ | `DATE` |
| ရက်စွဲ + အချိန် | `DATETIME` |
| မှန်/မှားသာ | `BOOLEAN` |
| သတ်မှတ်ထားသော ရွေးချယ်မှု | `ENUM` |

[Back to Top](#sql-structured-query-language)


## SQL Querying Data With SELECT

`SELECT` သည် Database မှ Data ကို ဖတ်ရှုရာတွင် အသုံးပြုသော အခြေခံဆုံး Command ဖြစ်သည်။

---

### Basic Syntax

```sql
SELECT column1, column2, ...
FROM table_name;
```

```sql
-- Column တစ်ခုချင်းသာ ရွေး
SELECT name FROM students;

-- Column များစွာ ရွေး
SELECT name, age, grade FROM students;

-- Column အားလုံး ရွေး (* = wildcard)
SELECT * FROM students;
```

---

### WHERE — စစ်ထုတ်ခြင်း

```sql
SELECT * FROM students WHERE grade = 'A';
SELECT * FROM students WHERE age > 20;
SELECT * FROM students WHERE age >= 18 AND grade = 'A';
SELECT * FROM students WHERE grade = 'A' OR grade = 'B';
SELECT * FROM students WHERE age != 20;
```

---

### ORDER BY — စီစဉ်ခြင်း

```sql
SELECT * FROM students ORDER BY age ASC;    -- ငယ်မှ ကြီး
SELECT * FROM students ORDER BY age DESC;   -- ကြီးမှ ငယ်

-- Column နှစ်ခုဖြင့် စီ
SELECT * FROM students ORDER BY grade ASC, age DESC;
```

---

### LIMIT & OFFSET — အကန့်အသတ်ဖြင့် ယူခြင်း

```sql
SELECT * FROM students LIMIT 5;             -- ထိပ်ဆုံး 5 ကြောင်း
SELECT * FROM students LIMIT 5 OFFSET 10;  -- 11 မှ 15 ကြောင်း (pagination)
```

---

### DISTINCT — ထပ်တူများ ဖယ်ရှားခြင်း

```sql
SELECT DISTINCT grade FROM students;
-- ရလဒ် : A, B, C  (ထပ်နေသောတန်ဖိုး ဖယ်သည်)
```

---

### ALIAS (AS) — ခေါင်းစဉ် ပြောင်းလဲခြင်း

```sql
SELECT name AS student_name, age AS student_age
FROM students;

-- Table alias (JOIN တွင် အသုံးဝင်)
SELECT s.name, s.grade
FROM students AS s;
```

---

### LIKE — Pattern ရှာဖွေခြင်း

| Pattern | အဓိပ္ပာယ် |
|---|---|
| `'Mg%'` | Mg ဖြင့် စသော |
| `'%Ko'` | Ko ဖြင့် ဆုံးသော |
| `'%u%'` | u ပါသော မည်သည့်နေရာမဆို |
| `'M_'` | M ပြီး တစ်လုံးမျှ |

```sql
SELECT * FROM students WHERE name LIKE 'Mg%';
SELECT * FROM students WHERE email LIKE '%@gmail.com';
```

---

### IN — တန်ဖိုး အစုပြ စစ်ခြင်း

```sql
SELECT * FROM students WHERE grade IN ('A', 'B');

-- NOT IN
SELECT * FROM students WHERE grade NOT IN ('C', 'F');
```

---

### BETWEEN — Range စစ်ခြင်း

```sql
SELECT * FROM students WHERE age BETWEEN 18 AND 22;

-- Date range
SELECT * FROM orders WHERE order_date BETWEEN '2025-01-01' AND '2025-12-31';
```

---

### NULL စစ်ဆေးခြင်း

```sql
SELECT * FROM students WHERE email IS NULL;      -- email မဖြည့်ထားသည်
SELECT * FROM students WHERE email IS NOT NULL;  -- email ရှိသည်
```

---

### ပြည့်စုံသော ဥပမာ

```sql
-- Grade A သို့မဟုတ် B ရသော၊ အသက် 18-25 ကြား၊
-- name ဖြင့် Z-A စီ၊ ထိပ်ဆုံး 10 ကြောင်းသာ ယူ
SELECT
    id,
    name        AS student_name,
    age,
    grade,
    email
FROM students
WHERE grade IN ('A', 'B')
  AND age BETWEEN 18 AND 25
  AND email IS NOT NULL
ORDER BY name DESC
LIMIT 10;
```

[Back to Top](#sql-structured-query-language)

## နောက်ထပ် လေ့လာရန် အကြံပြုချက်

1. **SQLZoo** — [sqlzoo.net](https://sqlzoo.net) တွင် Interactive လေ့ကျင့်ပါ
2. **LeetCode** — SQL Interview questions များ ဖြေဆိုလေ့ကျင့်ပါ
3. **Mode Analytics** — Real-world SQL practice ပြုလုပ်ပါ
4. **PostgreSQL Docs** — [postgresql.org/docs](https://www.postgresql.org/docs/) တွင် reference ကြည့်ပါ

[Back to Top](#sql-structured-query-language)

---

*ဤ document ကို SQL Exercises Folder တွင် reference အဖြစ်သုံးနိုင်သည်။*
