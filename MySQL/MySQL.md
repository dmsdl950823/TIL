# MySQL

## 🚪 Access
    $ mysql -u root - p
        Enter password : 
        
---------------------------

## 📋 Database
  #### See all databases
    > SHOW DATABASES;    
        +--------------------+
        | Database           |
        +--------------------+
        | information_schema |
        | front_end          |
        | mysql              |
        | performance_schema |
        | sys                |
        +--------------------+

  #### Create database
      > CREATE DATABASE <database name>;
          Query OK, 1 row affected (0.01 sec)

  #### Use database
      > USE <database name>;
          Database changed

  #### Remove database
  The DROP TABLE command deletes a table in the database.
      > DROP DATABASE <database name>;
          Query OK, 1 row affected (0.01 sec)
          
  

  #### See type of tables
      > DESCRIBE <table name>;
          +------------+-------------+------+-----+---------+----------------+
          | Field      | Type        | Null | Key | Default | Extra          |
          +------------+-------------+------+-----+---------+----------------+
          | _id        | int(11)     | NO   | PRI | NULL    | auto_increment |
          | name       | varchar(30) | NO   |     | NULL    |                |
          | department | varchar(30) | YES  |     | NULL    |                |
          | wage       | int(10)     | YES  |     | NULL    |                |
          | enter_dt   | datetime    | YES  |     | NULL    |                |
          +------------+-------------+------+-----+---------+----------------+

---------------------------------------------------------------
## 🧱 Manage Tables

  #### Create Table
    > CREATE TABLE <table_name> (
        column1 INT PRIMARY KEY AUTO_INCREMENT,
        column2 VARCHAR(32) NOT NULL,
        column3 VARCHAR(12) DEFAULT 'FOO',
        column4 VARCHAR(12)
      ) ENGINE=INNODB;
    

  #### Look inside the Table
    > DESCRIBE <table_name>;
        +---------+-------------+------+-----+---------+----------------+
        | Field   | Type        | Null | Key | Default | Extra          |
        +---------+-------------+------+-----+---------+----------------+
        | column1 | int(11)     | NO   | PRI | NULL    | auto_increment |
        | column2 | varchar(32) | NO   |     | NULL    |                |
        | column3 | varchar(12) | YES  |     | FOO     |                |
        | column4 | varchar(12) | YES  |     | NULL    |                |
        +---------+-------------+------+-----+---------+----------------+

  #### Empty table
  The TRUNCATE TABLE command deletes the data inside a table, but not the table itself.
  
      > TRUNCATE TABLE <table_name>;
          Query OK, 1 row affected (0.01 sec)

  #### Remove table
      > DROP TABLE <table_name>;

---------------------------------------------------------------

## 🔑 Give Grant before using databases / table
  You can give authority to other people before use the dbs.
  Otherwise MySQL blocks server which is not granted so that you can not use the db.
  
    > GRANT <authority> ON <database.table> TO '<id>'@'<hostname>' IDENTIFIED BY '<password>';
    
    # example - You can give authority to all user with => <id>@`%`
    > GRANT DELETE, INSERT, SELECT, UPDATE ON class.* TO `root`@`%` IDENTIFIED BY '1111';

##### ✔️ Types of Authorities
|controler|authorities|
|------|---|
|developer|DELETE, INSERT, SELECT, UPDATE|
|constructer|ALTER, CREATE, DELETE, DROP, INDEX, INSERT, SELECT, UPDATE, DELETE, INSERT, SELECT, UPDATE|
|DBA|ALL|


----------------------------------------------------------------


## ✏️ Qurey
Char => with '' | Int => without ''

  #### SELECT 

    SELECT * FROM <table name>;
    SELECT <column name 1>, <column name 2>, ... FROM <table name>;
    
  #### INSERT

    INSERT INTO <table name> (column1, column2, column3, column4) VALUE ('value1', 'value2', value3, 'value4');

  #### UPDATE

    UPDATE <table name> SET column1 = 'value1', column2 = 'value2'  WHERE column3 = 'value3' and column4 = 'value4';

  #### DELETE 
  
    DELETE FROM <table name> WHERE column1 = 'value1';
   
   
---------------------------------------------------------------------

## ⚽ Function

  #### 1. Number function
  
  |function | Eng | Kor |
  |------|---|---|
  | ABS(int) | Print absolute number | 절대값 출력 |
  | CEILING(int) |  | 값보다 큰 정수 중 가장 작은 수 |
  |FLOOR(int)|  |값보다 작은 정수 중 가장 큰 수 - 실수를 무조건 버림(음수일 경우는 제외)|
  |ROUND(int, index)||int를 소수점 이하 index(자릿수)에서 반올림 - (자릿수는 양수,0,음수를 가질 수 있음)|
  |TRUNCATE(int,index)||int를 소수점 이하 index(자릿수)에서 버림|
  |POW(X,Y) or POWER(X,Y)||X의 Y승|
  |MOD (numerator, denominator)||numerator(분자)를 denominator(분모)로 나눈 나머지를 구한다.(연산자 %와 같음)|
  |GREATEST(num1,num2,num3...)||주어진 수 중 제일 큰 수 리턴|
  |LEAST(num1,num2,num3...)||주어진 수 중 제일 작은 수 리턴.|
  |INTERVAL(a,b,c,d.....)||a(숫자)의 위치 반환|
 
 
  #### 2. String Function

  |function | Eng | Kor |
  |------|---|---|
  |ASCII(str)||문자의 아스키 코드값 리턴|
  |CONCAT('str1','str2','str3'...)||문자열들을 이어줌|
  |INSERT('str','from','length','new str')||문자열(str)의 시작위치(from)부터 길이(length)만큼 새로운 문자열(new str)로 대치|
  |REPLACE('str1','str2','str3')||str1 중 str2을 str3으로 변경|
  |INSTR('str1','str2')||str1 중 str2의 위치값을 출력|
  |LEFT('str', len)||str 중 왼쪽에서 len만큼을 추출|
  |RIGHT('str',len)||str 중 오른쪽에서 len만큼을 추출|
  |MID('str', num1, num2)||str 중 num1부터 num2개만큼 출력|
  |SUBSTRING('str', num1, num2)||str 중 num1부터 num2개만큼 출력|
  |LTRIM('str')||str 중 왼쪽의 공백 삭제|
  |RTRIM('str')||str 중 오른쪽의 공백 삭제|
  |TRIM('str')||양쪽 모두의 공백 삭제|
  |LCASE('str') or LOWER('str')||소문자로 변경|
  |UCASE('str') or UPPER('str')||대문자로 변경|
  |REVERSE('str')||문자열을 반대로 나열|

  #### 3. Logic Function
  |function | Eng | Kor |
  |------|---|---|
  |IF(logic, true_value , false_value)||논리식이 참이면 참일 때 값을 출력하고 논리식이 거짓이면 거짓일 때 출력한다.|
  |IFNULL(val1,val2)||val1이 NULL 이면 val2로 대치하고, 그렇지 않으면 val1을 출력|

  #### 4. Count Function
  |function | Eng | Kor |
  |------|---|---|
  |COUNT(field_name)||NULL 값이 아닌 레코드 수를 구함|
  |SUM(field_name)||field_name의 합계를 구함|
  |AVG(field_name)||각각의 그룹 안에서 field_name의 average를 구함|
  |MAX(field_name)||max 값을 구함|
  |MIN(필드명)||min 값을 구함|
  
  #### 5. Date Function
  |function | Eng | Kor |
  |------|---|---|
  |NOW() or SYSDATE() or CURRENT_TIMESTAMP()||현재 날짜와 시간 출력|
  |CURDATE() or CURRENT_DATE()||현재 날짜 출력|
  |CURTIME() or CURRENT_TIME()||현재 시간 출력|
  |DATE_ADD(date,INTERVAL <standard_value>)||날짜(date)에서 기준값(standard_value) 만큼 더하기 ※ 기준값 : YEAR, MONTH, DAY, HOUR, MINUTE, SECOND|
  |DATE_SUB(date,INTERVAL <standard_value>)||날짜(date)에서 기준값(standard_value) 만큼 빼기 ※ 기준값 : YEAR, MONTH, DAY, HOUR, MINUTE, SECOND|
  |YEAR(date)||날짜의 연도 출력|
  |MONTH(date)||날짜의 월 출력|
  |MONTHNAME(date)||날짜의 월을 영어로 출력|
  |DAYNAME(date)||날짜의 요일일 영어로 출력|
  |DAYOFMONTH(date)||날짜의 월별 일자 출력|
  |DAYOFWEEK(date)||날짜의 주별 일자 출력(월요일(0),화요일(1)...일요일(6))|
  |WEEKDAY(date)||날짜의 주별 일자 출력(월요일(0),화요일(1)...일요일(6))|
  |DAYOFYEAR(date)||일년을 기준으로 한 날짜까지의 날 수|
  |WEEK(date)||일년 중 몇 번째 주|
  |FROM_DAYS(day)||00년 00월 00일부터 날 수 만큼 경과한 날의 날짜 출력|
  |TO_DAYS(date)||00 년 00 월 00일 부터 날짜까지의 일자 수 출력|
  |DATE_FORMAT(date,'type')||날짜를 형식에 맞게 출력|
  
  **  date type  **
  ...
  
  
  #### 6. Other function
  |function | Eng | Kor |
  |------|---|---|
  |DATABASE()||현재의 데이터베이스 이름출력|
  |PASSWORD('str')||문자열을 암호화|
  |FORMAT(num, 0.00.. )||num을 #,###,###.## 형식으로 출력|