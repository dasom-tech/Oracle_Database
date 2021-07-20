# 🤓 SQL 레벨업!!
<details>
  <summary>🔔 쿼리 연습</summary>
<details>
  <summary>SELECT</summary>  
  
  📄 테이블  
  ![image](https://user-images.githubusercontent.com/73812196/124098265-5c656d80-da97-11eb-9ff1-465d9cb857f3.png)
  
- 동물 보호소에 들어온 모든 동물의 정보를 ANIMAL_ID순으로 조회하는 SQL문을 작성해주세요. SQL을 실행하면 다음과 같이 출력되어야 합니다.  
  
  SELECT *  
  FROM ANIMAL_INS  
  ORDER BY ANIMAL_ID ASC;    
  
  📄 결과
  ![image](https://user-images.githubusercontent.com/73812196/124098315-68512f80-da97-11eb-8b3a-0eb25b5103a2.png)  
  
- 동물 보호소에 들어온 모든 동물의 이름과 보호 시작일을 조회하는 SQL문을 작성해주세요. 이때 결과는 ANIMAL_ID 역순으로 보여주세요. SQL을 실행하면 다음과 같이 출력되어야 합니다.  
  
  SELECT NAME  
     , DATETIME  
  FROM ANIMAL_INS  
  ORDER BY ANIMAL_ID DESC;    
  
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124099277-515f0d00-da98-11eb-9e1e-97c0bf135f63.png)  
  
- 동물 보호소에 들어온 동물 중 아픈 동물1의 아이디와 이름을 조회하는 SQL 문을 작성해주세요. 이때 결과는 아이디 순으로 조회해주세요.  
  
  SELECT ANIMAL_ID  
     , NAME  
  FROM ANIMAL_INS  
  WHERE INTAKE_CONDITION = 'Sick'  
  ORDER BY ANIMAL_ID ASC;    
  
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124099517-92572180-da98-11eb-98ef-2db44c947856.png)  
  
- 동물 보호소에 들어온 동물 중 젊은 동물1의 아이디와 이름을 조회하는 SQL 문을 작성해주세요. 이때 결과는 아이디 순으로 조회해주세요.  
  
  SELECT ANIMAL_ID  
       , NAME  
  FROM ANIMAL_INS  
  WHERE INTAKE_CONDITION NOT IN 'Aged'  
  ORDER BY ANIMAL_ID ASC;    
  
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124099654-b9155800-da98-11eb-97a6-3c220c2b227e.png)  
  
- 동물 보호소에 들어온 모든 동물의 아이디와 이름, 보호 시작일을 이름 순으로 조회하는 SQL문을 작성해주세요. 단, 이름이 같은 동물 중에서는 보호를 나중에 시작한 동물을 먼저 보여줘야 합니다.  
  
  SELECT ANIMAL_ID  
     , NAME  
     , DATETIME  
  FROM ANIMAL_INS  
  ORDER BY NAME ASC, DATETIME DESC;    
  
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124099909-ecf07d80-da98-11eb-8d4f-18f70489fc13.png)  
  
- 동물 보호소에 가장 먼저 들어온 동물의 이름을 조회하는 SQL 문을 작성해주세요.  
  
  SELECT NAME  
  FROM ANIMAL_INS  
  WHERE DATETIME = (SELECT MIN(DATETIME)  
                    FROM ANIMAL_INS);    
  
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124100042-13161d80-da99-11eb-915e-c0e0a0c2cbd7.png)  
</details>  
<details>
  <summary>SUM, MAX, MIN</summary>  
  
  📄 테이블    
  ![image](https://user-images.githubusercontent.com/73812196/124098265-5c656d80-da97-11eb-9ff1-465d9cb857f3.png)  
  
- 가장 최근에 들어온 동물은 언제 들어왔는지 조회하는 SQL 문을 작성해주세요.  
  
  SELECT MAX(DATETIME)  
  FROM ANIMAL_INS;  
  
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124201699-a0965380-db13-11eb-8269-f05c6365beda.png)  
  
- 동물 보호소에 가장 먼저 들어온 동물은 언제 들어왔는지 조회하는 SQL 문을 작성해주세요.  
  
  SELECT MIN(DATETIME)  
  FROM ANIMAL_INS;  
  
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124201762-c6235d00-db13-11eb-9456-23eec846f1c5.png)  
  
- 동물 보호소에 동물이 몇 마리 들어왔는지 조회하는 SQL 문을 작성해주세요.  
  
  SELECT COUNT(ANIMAL_ID)  
  FROM ANIMAL_INS;  
  
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124201803-e8b57600-db13-11eb-80c0-3cfe9c8defd6.png)  
  
- 동물 보호소에 들어온 동물의 이름은 몇 개인지 조회하는 SQL 문을 작성해주세요. 이때 이름이 NULL인 경우는 집계하지 않으며 중복되는 이름은 하나로 칩니다.
  
  SELECT COUNT(DISTINCT(NAME))  
  FROM ANIMAL_INS  
  WHERE NAME NOT IN('NULL'); 
  
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124201858-169aba80-db14-11eb-8f47-40a95c6dda4f.png)  
</details>  
<details>
  <summary>GROUP BY, HAVING</summary>  
  
  📄 테이블  
  ![image](https://user-images.githubusercontent.com/73812196/124098265-5c656d80-da97-11eb-9ff1-465d9cb857f3.png)  
  
- 동물 보호소에 들어온 동물 중 고양이와 개가 각각 몇 마리인지 조회하는 SQL문을 작성해주세요. 이때 고양이를 개보다 먼저 조회해주세요.  
  
  SELECT ANIMAL_TYPE  
     , COUNT(ANIMAL_ID) AS count  
  FROM ANIMAL_INS  
  GROUP BY ANIMAL_TYPE  
  ORDER BY ANIMAL_TYPE ASC;  
  
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124202093-9b85d400-db14-11eb-9391-bbf67116756c.png)  
  
- 동물 보호소에 들어온 동물 이름 중 두 번 이상 쓰인 이름과 해당 이름이 쓰인 횟수를 조회하는 SQL문을 작성해주세요. 이때 결과는 이름이 없는 동물은 집계에서 제외하며, 결과는 이름 순으로 조회해주세요.  
  
  SELECT NAME  
     , COUNT(NAME) AS count  
  FROM ANIMAL_INS  
  GROUP BY NAME HAVING COUNT(NAME) >= 2  
  ORDER BY NAME ASC; 
  
  📄 결과    
  ![image](https://user-images.githubusercontent.com/73812196/124202169-ccfe9f80-db14-11eb-804b-8a54b23d98e8.png)  
  
  📄 테이블  
  ![image](https://user-images.githubusercontent.com/73812196/124202316-0afbc380-db15-11eb-873b-bdbd14ca7e30.png)  
  
- 보호소에서는 몇 시에 입양이 가장 활발하게 일어나는지 알아보려 합니다. 09:00부터 19:59까지, 각 시간대별로 입양이 몇 건이나 발생했는지 조회하는 SQL문을 작성해주세요. 이때 결과는 시간대 순으로 정렬해야 합니다.  
  
  SELECT EXTRACT(HOUR FROM CAST(DATETIME AS TIMESTAMP)) AS HOUR  
     , COUNT(ANIMAL_ID) AS COUNT  
  FROM ANIMAL_OUTS A  
  WHERE EXTRACT(HOUR FROM CAST(DATETIME AS TIMESTAMP)) BETWEEN 9 AND 19  
  GROUP BY EXTRACT(HOUR FROM CAST(DATETIME AS TIMESTAMP))  
  ORDER BY HOUR;  
  
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124202400-39799e80-db15-11eb-8ac3-99b6adf990e2.png)  
  
- 보호소에서는 몇 시에 입양이 가장 활발하게 일어나는지 알아보려 합니다. 0시부터 23시까지, 각 시간대별로 입양이 몇 건이나 발생했는지 조회하는 SQL문을 작성해주세요. 이때 결과는 시간대 순으로 정렬해야 합니다.  
  
  SELECT HOUR, COUNT(B.DATETIME) AS COUNT  
  FROM  
     (SELECT LEVEL-1 AS HOUR --LEVEL은 기본으로 1부터 시작  
      FROM DUAL    
      CONNECT BY LEVEL<25) A   
  LEFT JOIN ANIMAL_OUTS B --데이터가 없어도 출력되어야 하므로 LEFT JOIN  
  ON A.HOUR = TO_CHAR(B.DATETIME,'HH24')  
  GROUP BY HOUR   
  ORDER BY HOUR;  
                           
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124205529-61203500-db1c-11eb-8c32-b00efec820bf.png)   
</details>
<details>
  <summary>IS NULL</summary>  
  
  📄 테이블  
  ![image](https://user-images.githubusercontent.com/73812196/124098265-5c656d80-da97-11eb-9ff1-465d9cb857f3.png)  
  
- 동물 보호소에 들어온 동물 중, 이름이 없는 채로 들어온 동물의 ID를 조회하는 SQL 문을 작성해주세요. 단, ID는 오름차순 정렬되어야 합니다.  
  
  SELECT ANIMAL_ID
  FROM ANIMAL_INS
  WHERE NAME IS NULL
  ORDER BY ANIMAL_ID;  
  
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124206008-6a5dd180-db1d-11eb-9d57-bd5054d82f91.png)  
  
- 동물 보호소에 들어온 동물 중, 이름이 있는 동물의 ID를 조회하는 SQL 문을 작성해주세요. 단, ID는 오름차순 정렬되어야 합니다.  
  
  SELECT ANIMAL_ID  
  FROM ANIMAL_INS  
  WHERE NAME IS NOT NULL  
  ORDER BY ANIMAL_ID;  
  
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124206192-d3dde000-db1d-11eb-84c1-238d06cab297.png)  
  
- 입양 게시판에 동물 정보를 게시하려 합니다. 동물의 생물 종, 이름, 성별 및 중성화 여부를 아이디 순으로 조회하는 SQL문을 작성해주세요. 이때 프로그래밍을 모르는 사람들은 NULL이라는 기호를 모르기 때문에, 이름이 없는 동물의 이름은 "No name"으로 표시해 주세요.  
  
  SELECT ANIMAL_TYPE  
       , NVL(NAME, 'No name')  
       , SEX_UPON_INTAKE  
  FROM ANIMAL_INS  
  ORDER BY ANIMAL_ID;  
  
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124207379-57003580-db20-11eb-99a9-14989eb3bfc7.png)  
  ![image](https://user-images.githubusercontent.com/73812196/124207410-6b443280-db20-11eb-9273-172e2053b80a.png)  
</details> 

<details>
  <summary>JOIN</summary>
  
  📄 테이블  
  ![image](https://user-images.githubusercontent.com/73812196/124098265-5c656d80-da97-11eb-9ff1-465d9cb857f3.png)  
  ![image](https://user-images.githubusercontent.com/73812196/124202316-0afbc380-db15-11eb-873b-bdbd14ca7e30.png)  
  
- ANIMAL_OUTS 테이블은 동물 보호소에서 입양 보낸 동물의 정보를 담은 테이블입니다. ANIMAL_OUTS 테이블의 ANIMAL_ID는 ANIMAL_INS의 ANIMAL_ID의 외래 키입니다. 천재지변으로 인해 일부 데이터가 유실되었습니다. 입양을 간 기록은 있는데, 보호소에 들어온 기록이 없는 동물의 ID와 이름을 ID 순으로 조회하는 SQL문을 작성해주세요.  
  
  SELECT A.ANIMAL_ID  
       , A.NAME  
  FROM ANIMAL_OUTS A  
  LEFT JOIN ANIMAL_INS B  
  ON A.ANIMAL_ID = B.ANIMAL_ID  
  WHERE B.ANIMAL_ID IS NULL  
  ORDER BY A.ANIMAL_ID;   
  
  📄 결과   
  ![image](https://user-images.githubusercontent.com/73812196/124208601-d3941380-db22-11eb-98fa-86fe80c7ca4d.png)  
  
- 관리자의 실수로 일부 동물의 입양일이 잘못 입력되었습니다. 보호 시작일보다 입양일이 더 빠른 동물의 아이디와 이름을 조회하는 SQL문을 작성해주세요. 이때 결과는 보호 시작일이 빠른 순으로 조회해야합니다.  
  
  SELECT A.ANIMAL_ID  
       , A.NAME  
  FROM ANIMAL_INS A  
  FULL OUTER JOIN ANIMAL_OUTS B  
  ON A.ANIMAL_ID = B.ANIMAL_ID  
  WHERE A.DATETIME > B.DATETIME  
  ORDER BY A.DATETIME;  
  
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124208980-b449b600-db23-11eb-9d8e-765e35c3b2cb.png)  
  
- 아직 입양을 못 간 동물 중, 가장 오래 보호소에 있었던 동물 3마리의 이름과 보호 시작일을 조회하는 SQL문을 작성해주세요. 이때 결과는 보호 시작일 순으로 조회해야 합니다.  
  
  SELECT * FROM (  
                SELECT A.NAME   
                     , A.DATETIME   
                FROM ANIMAL_INS A  
                LEFT JOIN ANIMAL_OUTS B  
                ON A.ANIMAL_ID = B.ANIMAL_ID  
                WHERE B.ANIMAL_ID IS NULL  
                ORDER BY A.DATETIME)  
  WHERE ROWNUM < 4;  
                   
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124210575-9fbaed00-db26-11eb-8b74-bfb4631885b3.png)  
                   
- 보호소에서 중성화 수술을 거친 동물 정보를 알아보려 합니다. 보호소에 들어올 당시에는 중성화1되지 않았지만, 보호소를 나갈 당시에는 중성화된 동물의 아이디와 생물 종, 이름을 조회하는 아이디 순으로 조회하는 SQL 문을 작성해주세요.    
                   
  SELECT A.ANIMAL_ID  
       , A.ANIMAL_TYPE  
       , A.NAME  
  FROM ANIMAL_OUTS A  
  LEFT JOIN ANIMAL_INS B  
  ON A.ANIMAL_ID = B.ANIMAL_ID  
  WHERE B.SEX_UPON_INTAKE LIKE 'Intact%'  
      AND A.SEX_UPON_OUTCOME NOT LIKE 'Intact%'  
  ORDER BY A.ANIMAL_ID;  
                   
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124211970-02ad8380-db29-11eb-9262-10fef971b16c.png)  
</details>
<details>
  <summary>String, Date</summary>  
      
  📄 테이블    
  ![image](https://user-images.githubusercontent.com/73812196/124098265-5c656d80-da97-11eb-9ff1-465d9cb857f3.png)  
  ![image](https://user-images.githubusercontent.com/73812196/124202316-0afbc380-db15-11eb-873b-bdbd14ca7e30.png)  
      
- 동물 보호소에 들어온 동물 중 이름이 Lucy, Ella, Pickle, Rogan, Sabrina, Mitty인 동물의 아이디와 이름, 성별 및 중성화 여부를 조회하는 SQL 문을 작성해주세요.  
      
  SELECT ANIMAL_ID  
       , NAME  
       , SEX_UPON_INTAKE  
  FROM ANIMAL_INS  
  WHERE NAME IN ('Lucy', 'Ella', 'Pickle', 'Rogan', 'Sabrina', 'Mitty')  
  ORDER BY ANIMAL_ID;  
      
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124216854-19a4a380-db32-11eb-8712-c5bcee8d6bd3.png)  
      
- 보호소에 돌아가신 할머니가 기르던 개를 찾는 사람이 찾아왔습니다. 이 사람이 말하길 할머니가 기르던 개는 이름에 'el'이 들어간다고 합니다. 동물 보호소에 들어온 동물 이름 중, 이름에 "EL"이 들어가는 개의 아이디와 이름을 조회하는 SQL문을 작성해주세요. 이때 결과는 이름 순으로 조회해주세요. 단, 이름의 대소문자는 구분하지 않습니다.  
      
  SELECT ANIMAL_ID  
       , NAME  
  FROM ANIMAL_INS  
  WHERE UPPER(NAME) LIKE '%EL%'  
      AND ANIMAL_TYPE = 'Dog'  
  ORDER BY NAME;  
   
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124218538-60e06380-db35-11eb-9a0c-906930f249f8.png) 
      
- 보호소의 동물이 중성화되었는지 아닌지 파악하려 합니다. 중성화된 동물은 SEX_UPON_INTAKE 컬럼에 'Neutered' 또는 'Spayed'라는 단어가 들어있습니다. 동물의 아이디와 이름, 중성화 여부를 아이디 순으로 조회하는 SQL문을 작성해주세요. 이때 중성화가 되어있다면 'O', 아니라면 'X'라고 표시해주세요.  
      
  SELECT ANIMAL_ID  
       , NAME  
       , CASE WHEN SEX_UPON_INTAKE LIKE 'Neutered%' THEN 'O'  
              WHEN SEX_UPON_INTAKE LIKE 'Spayed%' THEN 'O'  
              ELSE 'X' END  
  FROM ANIMAL_INS  
  ORDER BY ANIMAL_ID  
      
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124221835-735d9b80-db3b-11eb-8330-f0c525431460.png)  
      
- 입양을 간 동물 중, 보호 기간이 가장 길었던 동물 두 마리의 아이디와 이름을 조회하는 SQL문을 작성해주세요. 이때 결과는 보호 기간이 긴 순으로 조회해야 합니다.    
  
  SELECT ANIMAL_ID  
       , NAME  
  FROM (SELECT A.ANIMAL_ID  
             , A.NAME  
        FROM ANIMAL_INS A  
        JOIN ANIMAL_OUTS B  
        ON A.ANIMAL_ID = B.ANIMAL_ID  
        ORDER BY B.DATETIME - A.DATETIME DESC  
       )  
  WHERE ROWNUM < 3;  
                   
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124223803-65aa1500-db3f-11eb-8a61-334f6af403a2.png)  
                   
- 테이블에 등록된 모든 레코드에 대해, 각 동물의 아이디와 이름, 들어온 날짜1를 조회하는 SQL문을 작성해주세요. 이때 결과는 아이디 순으로 조회해야 합니다.  
                   
  SELECT ANIMAL_ID  
       , NAME  
       , TO_CHAR(DATETIME, 'YYYY-MM-DD') AS 날짜  
  FROM ANIMAL_INS  
  ORDER BY ANIMAL_ID  
                   
  📄 결과  
  ![image](https://user-images.githubusercontent.com/73812196/124224411-90489d80-db40-11eb-9178-95c8dd038caa.png)   
</details>
</details>  
      
## 🔔 SELECT 쿼리문 실행시 순서   
      FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY  
      
## 🔔 NVL 함수는 값이 null인 경우 지정값을 출력, NVL2 함수는 null이 아닌경우 지정값1을 출력하고, null인 경우 지정값2를 출력 한다.    
      NVL(NAME, 'NO name')
      NVL2(NAME, NAME, 'NO name')  

## 🔔 데이터베이스 객체  
### 🚩 개요
 - 테이블 : 데이터를 담고 있는 개체
 - 뷰 : 하나 이상의 테이블을 연결해 마치 테이블인 것처럼 사용하는 객체
 - 인덱스 : 테이블에 있는 데이터를 빠르게 찾기 위한 객체
 - 시노님 : 데이터베이스 객체에 대한 별칭을 부여한 객체
 - 시퀀스 : 일련번호 채번을 할 때 사용되는 객체
 - 함수 : 특정 연산을 하고 값을 반환하는 객체
 - 프로시저 : 함수와 비슷하지만 값을 반환하지는 않는 객체
 - 패키지 : 용도에 맞게 함수나 프로시저를 하나로 묶어 놓은 객체  
 
### 🚩 테이블
 - 테이블 생성    
   CREATE TABLE 테이블명 (    
   컬럼1 데이터타입 [NULL, NOT NULL],    
   컬럼2 데이터타입 [NULL, NOT NULL],    
   ...      
   );    
   
 - 데이터 타입    
   1. CHAR : 고정길이, 최대 2000byte  
   2. VARCHAR2 : 가변길이, 최대 4000byte, 저장 공간을 위해 CHAR보다는 VARCHAR2를 사용할 것  
   3. NCHAR : 고정길이 유니코드 문자(다국어 입력 가능), 최대 2000vyte  
   4. NVARCHAR2 : 가변길이 유니코드 문자(다국어 입력 가능), 최대 4000byte, 영어 한 문자 : 1byte, 한글 : 2byte  
   5. NUMBER : 가변숫자, 최대 22byte
   6. FLOAT : NUMBER의 하위 타입, 최대 22byte, 이진수 기준
   7. BINARY_FLOAT : 32비트 부동소수점 수, 최대 4byte
   8. BINARY_DOUBLE : 64비트 부동소수점 수, 최대 8byte  
   9. DATE : 연,월,일,시,분,초까지 입력 가능  
   10. TIMESTAMP : 밀리초까지 입력 가능  
   11. CLOB :  문자형 대용량 객체, 고정길이와 가변길이 문자 집합 지원, 문자형 대용량 데이터 저장시    
   12. NCLOB : 유니코드를 포함한 문자형 대용량 객체, 문자형 대용량 데이터 저장시    
   13. BLOB : 이진형 대용량 객체, 그래픽, 이미지, 동영상 등  
   14. BFILE : 대용량 이진 파일에 대한 로케이터(위치, 이름) 저장
   
 - 제약조건  
   1. NOT NULL : NULL 허용하지 않음. 반드시 데이터를 입력해야 함
   2. UNIQUE : 중복 허용하지 않음. UNIQUE 비교 대상에서 NULL은 제외됨
   3. Primary key : 기본키(NOT NULL+UNIQUE), 테이블당 1개 생성 가능, 데이터 무결성을 실질적으로 구현한 것, 특수한 경우를 제외하고 기본키는 반드시 생성하는 것이 원칙
   4. Foreign key : 외래키, 여러 컬럼을 외래키로 만드려면 참조하는 컬럼과 외래키 컬럼의 순서와 개수는 같아야 함
   5. CHECK : 컬럼에 입력되는 데이터를 체크해 특정 조건에 맞는 데이터만 입력 받고 그렇지 않으면 오류를 뱉어 냄  
   6. DEFAULT : 제약조건은 아니나 컬럼 속성 중 하나로 컬럼 속성에 자동으로 디폴트 값이 들어감  
      ex) 테이블 생성시   
          컬럼명 DATE DEFAULT SYSDATE  
          INSERT INTO 테이블명(컬럼1, 컬럼2) VALUES ('AA', 'BB');  
          결과:    
          AA   BB   2021/07/05 10:12:10  
          
 - 테이블 삭제    
   DROP TABLE 테이블명 [CASCADE CONSTRAINTS] : CASCADE CONSTRAINTS를 붙이면 기본키, 제약조건 등도 자동 삭제됨  
   
 - 테이블 변경  
   ALTER TABLE 테이블명 RENAME COLUMN 변경전컬럼명 TO 변경후컬럼명;  
   ALTER TABLE 테이블명 MODIFY 컬럼명 데이터타입;
   ALTER TABLE 테이블명 ADD 컬럼명 데이터타입;
   ALTER TABLE 테이블명 DROP COLUMN 컬럼명;
   ALTER TABLE 테이블명 ADD CONSTRAINTS 제약조건명 PRIMARY KEY(컬럼명, ..);
   ALTER TABLE 테이블명 DROP CONSTRAINS 제약조건명;  
   
 - 테이블 복사  
   CREATE TABLE 테이블명 AS  
   SELECT 컬럼1, 컬럼2, ...  
   FROM 복사할 테이블명;  
   
### 🚩 뷰  
 - 뷰 생성  
   CREATE OR REPLACE VIEW 뷰명 AS
   SELECT 문장;  
   ex) CREATE OR REPLACE VIEW 뷰명 AS  
       SELECT a.employee_id, a.emp_name, a.department_id, b.department_name  
       FROM employee a, departments b  
       WHERE a.department_id = b.department_id;  
      
 - 뷰 삭제  
   DROP VIEW 뷰명;  
      
### 🚩 인덱스    
 - 인덱스 생성 : UNIQUE 제약조건을 만들면 자동으로 UNIQUE 인덱스를 생성해 줌  
   CREATE[UNIQUE] INDEX 인덱스명  
   ON 테이블명(컬럼1, 컬럼2, ...);  
      
 - 일반적으로 테이블 전체 row 수의 15% 이하의 데이터를 조회할 때 인덱스 생성
 - 테이블 건수가 적다면 굳이 만들 필요 없음
 - 데이터의 유일성 정도가 좋거나 범위가 넓은 값을 가진 컬럼을 인덱스로 만드는 것이 좋음
 - NULL이 많이 포함된 컬럼을 인덱스 컬럼으로 만들기 적당치 않음
 - 결합 인덱스를 만들 때는 자주 사용되는 컬럼을 순서상 앞에 두는 것이 좋음
 - 테이블에 만들 수 있는 인덱스 수의 제한은 없으나 너무 많이 만들면 부하가 발생함  
      
 - 인덱스 삭제  
   DROP INDEX 인덱스명;  
      
### 🚩 시퀀스  
 - 시퀀스 생성  
   CREATE SEQUENCE 시퀀스명  
   INCREMENT BY 증감숫자 : 0이 아닌 정수, 양수면 증가, 음수면 감소, 디폴트 1   
   START WITH 시작숫자 : 디폴트 값은 증가일 때는 MINVALUE, 감소일 경우 MAXVALUE    
   NOMINVALUE | MINVALUE 최소값 : 시작숫자보다 작거나 같아야 하고 MAXVALUE보다 작아야 함    
   NOMAXVALUE | MAXVALUE 최대값 : 시작숫자보다 크거나 같아야 하고 MINVALUE보다 커야 함    
   NOCYCLE | CYCLE : CYCLE: 증가는 퇴대값에 도달하면 다시 최소값부터 시작, 감소는 최소값에 도달하면 다시 최대 값에서 시작, NOCYCLE : 디폴트 값으로 최대나 최소값에 도달하면 생성 중지       
   NOCACHE | CACHE; : NOCACHE : 디폴트로 메모리에 시퀀스 값을 미리 할당해 놓지 않으며 디폴트 값은 20, CACHE : 메모리에 시퀀스 값을 미리 할당해 놓음   
      
   INSERT INTO 테이블명(컬럼명) VALUES (시퀀스명.NEXTVAL); : INSERT나 SELECT 할 때마다 시퀀스 증감숫자만큼 증감  
      
 - 시퀀스 삭제  
   DROP SEQUENCE 시퀀스명;  
      
### 🚩 파티션 테이블    
 - 테이블을 생성할 때 파티션으로 테이블을 만들 수 있다.  
 - 테이블에 있는 특정 컬럼 값을 기준으로 데이터를 분할해 저장해 놓는 것.  
 - 논리적으로 테이블은 1개지만, 물리적으로는 파티션별로 데이터가 저장된다.  
 - 대용량 테이블의 경우 데이터 조회 시 효율성과 성능을 높이기 위한 것.  
      
   ex) CREATE TABLE 테이블명 (    
         컬럼1 NUMBER(6,0) NOT NULL,  
         컬럼2 VARCHAR2(10),  
         컬럼3 DATE DEFAULT SYSDATE NOT NULL,  
         컬럼4 VARCHAR2(6 ),  
         ...  
       )  
       PARTITION BY RANGE(컬럼4) (    
         ...  
         PARTITION SALES_Q1_2021 VALUES LESS THAN ('202104') TABLESPACE MYTS, --1분기   
         PARTITION SALES_Q2_2021 VALUES LESS THAN ('202107') TABLESPACE MYTS, --2분기     
         PARTITION SALES_Q3_2021 VALUES LESS THAN ('202110') TABLESPACE MYTS, --3분기   
         PARTITION SALES_Q4_2021 VALUES LESS THAN ('202201') TABLESPACE MYTS, --4분기   
         ...  
       );  
      
## 🔔 SQL 문장    
### 🚩 SELECT문  
 - 테이블이나 뷰에 있는 데이터를 조회할 때 사용  
 - SELECT * OR 컬럼명  
   FROM 테이블명 OR 뷰명  
   WHERE 조건    
   ORDER BY 컬럼명; 

### 🚩 INSERT문  
 - 신규로 데이터 입력시 사용  
 - INSERT INTO 테이블명 (컬럼1, 컬럼2, ...)  
   VALUES (값1, 값2, ...)  
 - 사원 테이블에서 월급이 5000 이상인 사원의 사원번호와 사원명을 조회한 결과를 ex3 테이블에 넣기  
   INSERT INTO ex3 (emp_id, emp_name)  
   SELECT employee_id, employee_name  
   FROM employees  
   WHERE salary > 5000;  
      
### 🚩 UPDATE문  
 - UPDATE 테이블명  
   SET 컬럼1 = 변경값1,  
       컬럼2 = 변경값2,  
       ...  
   WHERE 조건;  
 
### 🚩 MERGE문  
 -  MERGE INTO 테이블명  
    USING (update나 insert될 데이터 원천) ON (update될 조건)  
    WHEN MATCHED THEN  
      SET 컬럼1 =  값1, 컬럼2 = 값2, ...  
    WHERE UPDATE 조건  
      DELETE WHERE update_delete 조건  
    WHEN NOT MATCHED THEN  
      INSERT(컬럼1, 컬럼2, ...) VALUES (값1, 값2, ...)  
      WHERE insert 조건;  
      
 - ex) MERGE INTO ex3 a  
       USING (SELECT employee_id, salary, manager_id   
              FROM employees   
              WHERE manager_id = 146) b   
       ON (a.employee_id = b.employee_id)  
       WHEN MATCHED THEN  
         UPDATE SET a.bonus_amt = b.bonus_amt + a.salary * 0.01  
         --DELETE WHERE (b.employee_id = 161) 추가해주면 161번 사원은 삭제됨  
       WHEN NOT MATCHED THEN  
         INSERT (a.employee_id, b.bonus_amt) VALUES (b.employee_id, b.salary*0.01)  
         WHERE (b.salary < 8000);  
      
### 🚩 DELETE문  
 - 테이블에 있는 데이터를 삭제할 때 사용, COMMIT, ROLLBACK 가능. TRUNCATE문은 복귀 불가, WHERE 조건 붙일 수 없음  
 - DELETE ex3;  
 - TRUNCATE TABLE ex3;  
                                 
### 🚩 의사컬럼  
 - 테이블의 컬럼처럼 동작하지만 실제로 테이블에 저장되지는 않는 컬럼  
 - SELECT문에서는 의사컬럼 사용 가능  
 - CONNECT_BY_ISCYCLE, CONNECT_BY_ISLEAF,LEVEL  
 - NEXTVAL, CURRVAL  
 - ROWNUM, ROWID  
 - SELECT ROWNUM, employee_id  
   FROM employees  
   WHERE ROWNUM < 5;  
      
### 🚩 연산자  
 - 수식 연산자 : +,-,*,/  
 - 문자 연산자 : ||  
 - 논리 연산자 : >,<,>=,<=,=,<>,!=,^=       
 - 집합 연산자 : UNION, UNION ALL, INTERSECT, MINUS  
 - 계층형 쿼리 연산자 : PRIOR, CONNECT_BY_ROOT      
      
### 🚩 표현식  
 - 한 개 이상의 값과 연산자, SQL 함수 등이 결합된 식  
 - CASE WHEN 조건1 THEN 값1  
        WHEN 조건2 THEN 값2  
        ...  
        ELSE 기타 값  
   END  
 - ex) SELECT employee_id, salary,  
              CASE WHEN salary <= 5000 THEN 'C등급'  
                   WHEN salary > 5000 AND salary <= 15000 THEN 'B등급' ELSE 'A등급' END AS salary_grade  
       FROM employees;  

### 🚩 조건식  
 - 비교 조건식(ANY, ALL, SOME)  
   SELECT employee_id, salary  
   FROM employees  
   WHERE salary = ANY (2000, 3000, 4000) --해당 값들중 하나만 만족해도.    
   ORDER BY employee_id;  
                                                        
   SLECT employee_id, salary  
   FROM employees  
   WHERE salary = ALL(2000, 3000, 4000) --동시에 모든 조건을 만족하면.  
   ORDER BY employee_id;  
                                                        
   SELECT employee_id, salary  
   FROM employees  
   WHERE salary = SOME (2000, 3000, 4000) --ANY와 동일하게 사용됨.  
   ORDER BY employee_id;  
 
 - 논리 조건식(AND, OR, NOT)  
   SELECT employee_id, salary  
   FROM employees  
   WHERE NOT (salary >= 2500) --거짓일 때 true 반환  
   ORDER BY employee_id;    
  
 - NULL 조건식  
   등호 연산자 사용하지 말고 salary IS NULL 혹은 salary IS NOT NULL로 비교해야 함  
 
 - BETWEEN AND 조건식  
   SELECT employee_id, salary  
   FROM employees  
   WHERE salary BETWEEN 2000 AND 2500 -- 급여가 2000 ~ 2500 사이    
   ORDER BY employee_id;  
  
 - IN 조건식  
   SELECT employee_id, salary  
   FROM employees  
   WHERE salary IN (2000, 3000, 4000) -- 급여가 2000, 3000, 4000에 포함되는 사원    
   ORDER BY employee_id;  
  
   SELECT employee_id, salary  
   FROM employees  
   WHERE salary NOT IN (2000, 3000, 4000) -- 급여가 2000, 3000, 4000에 포함되지 않는 사원 
   ORDER BY employee_id;  
  
 - EXISTS 조건식  
   SELECT department_id, department_name  
   FROM departments a
   WHERE EXISTS ( SELECT *  
                  FROM employees b  
                  WHERE a.department_id = b.department_id -- IN과 비슷하지만 후행 조건절로 값의 리스트가 아닌 서브쿼리만 올 수 있음. 서브쿼리 내에 조인 조건이 있어야 함.    
                  AND b.salary> 3000)  
   ORDER BY a.department_name; 
  
 - LIKE 조건식  
   SELECT emp_name  
   FROM employees  
   WHERE emp_name LIKE 'A%' -- A로 시작하되 나머지는 어떤 글자가 와도 상관없이 모두 조회, 대소문자 구분, %가 아닌 _은 나머지 글자 전체가 아닌 한 글자만 비교    
   ORDER BY emp_name;  
  
  
                                                        
                                                        



