## GraphQL
GraphQL의 핵심은, 리소스를 url이 아니라 Query를 통해 표현하는 것이다.

예시로 어떤 API 가 Community site 용 API 이며,
이 API 를 사용해 사용자들이 글을 작성/수정/삭제 할 수 있고,
각 글에 댓글을 작성/수정/삭제할 수 있다고 해보자.

### VS Rest API
1. 글 관련 API = /posts
    * 글 작성 = POST /posts
    * 글 수정 = PATCH /posts/[postid]
    * 글 삭제 = DELETE /posts/[postid]
2. 댓글 관련 API = /posts/[postid]/comments
    * 댓글 작성 = POST /posts/[postid]/comments
    * 댓글 수정 = PATCH /posts/[postid]/comments/[commentid]
    * 댓글 삭제 = DELETE /posts/[postid]/comments/[commentid]

GraphQL 을 통한 API 는 RESTful API 와는 다른 측면을 보인다.

GraphQL API 는 주로 하나의 Endpoint 를 사용한다.
GraphQL API 는 요청할 때 사용한 Query 문에 따라 응답의 구조가 달라진다.

### Why GraphQL
Facebook 의 GraphQL blog 에서는 다음과 같이 이유를 밝히고 있다.

RESTful API 로는 다양한 기종에서 필요한 정보들을 일일히 구현하는 것이 힘들었다.
예로, iOS 와 Android 에서 필요한 정보들이 조금씩 달랐고, 그 다른 부분마다 API 를 구현하는 것이 힘들었다.

이 때문에 정보를 사용하는 측에서 원하는 대로 정보를 가져올 수 있고,
보다 편하게 정보를 수정할 수 있도록 하는 표준화된 Query language 를 만들게 되었다.
이것이 GraphQL 이다.



### 예시
* [Github V3](https://developer.github.com/v3/) - RestFul 
* [Github V4](https://developer.github.com/v4/) - GraphQL

### GraphQL 단점
1. File 전송 등 Text 만으로 하기 힘든 내용들을 처리하기 복잡하다.
2. 고정된 요청과 응답만 필요할 경우에는 Query 로 인해 요청의 크기가 RESTful API 의 경우보다 더 커진다.
3. 재귀적인 Query 가 불가능하다. (결과에 따라 응답의 깊이가 얼마든지 깊어질 수 있는 API 를 만들 수 없다.)

참조 : 
* [holaxprogramming](https://www.holaxprogramming.com/2018/01/20/graphql-vs-restful-api/)
* [@han7096](https://medium.com/@han7096/graphql-%EA%B3%BC-apollo%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%B4%EB%B3%B4%EB%A9%B0-%EC%A4%91%EA%B0%84-%EC%A0%95%EB%A6%AC-42981522b188)


## ACID 란?
ACID(원자성, 일관성, 고립성, 지속성)

데이터베이스 트랜잭션이 안전하게 수행된다는 것을 보장하기 위한 성질을 가리키는 약어이다

* 원자성(Atomicity)은 트랜잭션과 관련된 작업들이 부분적으로 실행되다가 중단되지 않는 것을 보장하는 능력이다. 예를 들어, 자금 이체는 성공할 수도 실패할 수도 있지만 보내는 쪽에서 돈을 빼 오는 작업만 성공하고 받는 쪽에 돈을 넣는 작업을 실패해서는 안된다. 원자성은 이와 같이 중간 단계까지 실행되고 실패하는 일이 없도록 하는 것이다.
* 일관성(Consistency)은 트랜잭션이 실행을 성공적으로 완료하면 언제나 일관성 있는 데이터베이스 상태로 유지하는 것을 의미한다. 무결성 제약이 모든 계좌는 잔고가 있어야 한다면 이를 위반하는 트랜잭션은 중단된다.
* 고립성(Isolation)은 트랜잭션을 수행 시 다른 트랜잭션의 연산 작업이 끼어들지 못하도록 보장하는 것을 의미한다. 이것은 트랜잭션 밖에 있는 어떤 연산도 중간 단계의 데이터를 볼 수 없음을 의미한다. 은행 관리자는 이체 작업을 하는 도중에 쿼리를 실행하더라도 특정 계좌간 이체하는 양 쪽을 볼 수 없다. 공식적으로 고립성은 트랜잭션 실행내역은 연속적이어야 함을 의미한다. 성능관련 이유로 인해 이 특성은 가장 유연성 있는 제약 조건이다. 자세한 내용은 관련 문서를 참조해야 한다.
* 지속성(Durability)은 성공적으로 수행된 트랜잭션은 영원히 반영되어야 함을 의미한다. 시스템 문제, DB 일관성 체크 등을 하더라도 유지되어야 함을 의미한다. 전형적으로 모든 트랜잭션은 로그로 남고 시스템 장애 발생 전 상태로 되돌릴 수 있다. 트랜잭션은 로그에 모든 것이 저장된 후에만 commit 상태로 간주될 수 있다.

# SQL 
## DISTINCT
```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

  
## WHERE Clause
| Operator | Description                                                                                             |
|----------|---------------------------------------------------------------------------------------------------------|
| =        | Equal                                                                                                   |
| <>       | Not equal (!=)                                                                                          |
| >        | Greater than                                                                                            |
| <        | Less than                                                                                               |
| >=       | Greater than or equal                                                                                   |
| <=       | Less than or equal                                                                                      |
| BETWEEN  | Between a certain range                                                                                 |
| LIKE     | Search for a pattern                                                                                    |
| IN       | 특정값 여러개를 선택하는 SQL 연산자  SELECT * FROM customer   WHERE cust_country IN ('JP', 'KR', 'US'); |

## AND, OR and NOT Operators
AND
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2...;
```

OR
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2...;
```

NOT 
```sql
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;
```

## NULL
```sql
SELECT column_names
FROM table_name
WHERE column_name IS NULL;

SELECT column_names
FROM table_name
WHERE column_name IS NOT NULL;
```


# Join
## [Inner Join](http://www.sqlitetutorial.net/sqlite-inner-join/)
```sql
SELECT a1, a2, b1, b2
FROM A
INNER JOIN B on B.f = A.f;
```
![](http://www.sqlitetutorial.net/wp-content/uploads/2015/12/SQLite-Inner-Join-Example.png)

![](http://www.sqlitetutorial.net/wp-content/uploads/2015/12/SQLite-inner-join-venn-diagram.png)

## [Left Join](http://www.sqlitetutorial.net/sqlite-left-join/)
```sql
SELECT a, b
FROM A
LEFT JOIN B ON A.f = B.f
WHERE search_condition;
```
![](http://www.sqlitetutorial.net/wp-content/uploads/2015/12/SQLite-left-join-example.png)

![](http://www.sqlitetutorial.net/wp-content/uploads/2015/12/SQLite-Left-Join-Venn-Diagram.png)

## [Full Outer Join](http://www.sqlitetutorial.net/sqlite-left-join/)
거의 사용되지 않음
```sql
SELECT *
FROM dogs 
FULL OUTER JOIN cats
    ON dogs.color = cats.color;

```
![](http://www.sqlitetutorial.net/wp-content/uploads/2016/06/full-outer-join.png)

## [Cross Join]()
A 테이블에 N 개의 행이 있고 B 개의 테이블에 M 개의 행이 있다고 가정하면이 두 테이블의 CROSS JOIN은 NxM 행을 포함하는 결과 집합을 생성합니다.
```sql
CREATE TABLE ranks (
    rank TEXT NOT NULL
);
 
CREATE TABLE suits (
    suit TEXT NOT NULL
);
 
INSERT INTO ranks(rank) 
VALUES('2'),('3'),('4'),('5'),('6'),('7'),('8'),('9'),('10'),('J'),('Q'),('K'),('A');
 
INSERT INTO suits(suit) 
VALUES('Clubs'),('Diamonds'),('Hearts'),('Spades');
```

```sql
SELECT rank,
       suit
  FROM ranks
       CROSS JOIN
       suits
ORDER BY suit;
```

| rank  | suit |  
|----|-------|
| 2  | Clubs |
| 3  | Clubs |
| 4  | Clubs |
| 5  | Clubs |
| 6  | Clubs |
| 7  | Clubs |
| 8  | Clubs |
| 9  | Clubs |
| 10 | Clubs |
| J  | Clubs |
| Q  | Clubs |
| K  | Clubs |
| A  | Clubs |

| rank  | suit |
|----|-------|
| 2  | Diamonds |
| 3  | Diamonds |
| 4  | Diamonds |
| 5  | Diamonds |
| 6  | Diamonds |
| 7  | Diamonds |
| 8  | Diamonds |
| 9  | Diamonds |
| 10 | Diamonds |
| J  | Diamonds |
| Q  | Diamonds |
| K  | Diamonds |
| A  | Diamonds |

| rank  | suit |
|----|-------|
| 2  | Hearts |
| 3  | Hearts |
| 4  | Hearts |
| 5  | Hearts |
| 6  | Hearts |
| 7  | Hearts |
| 8  | Hearts |
| 9  | Hearts |
| 10 | Hearts |
| J  | Hearts |
| Q  | Hearts |
| K  | Hearts |
| A  | Hearts |

| rank  | suit |
|----|-------|
| 2  | Spades |
| 3  | Spades |
| 4  | Spades |
| 5  | Spades |
| 6  | Spades |
| 7  | Spades |
| 8  | Spades |
| 9  | Spades |
| 10 | Spades |
| J  | Spades |
| Q  | Spades |
| K  | Spades |
| A  | Spades |


## [Self Join](http://www.sqlitetutorial.net/sqlite-self-join/)
자체 조인은 **LEFT JOIN** 또는 **INNER JOIN** 절을 사용하여 테이블 자체에 조인 할 수있게 해주는 특별한 종류의 조인입니다. 
자체 조인을 사용하여 동일한 테이블 내의 다른 행과 행을 조인하는 결과 세트를 작성합니다.

![](http://www.sqlitetutorial.net/wp-content/uploads/2018/11/employees.png)

```sql
SELECT DISTINCT
 e1.city,
 e1.firstName || ' ' || e1.lastname AS fullname
FROM
 employees e1
INNER JOIN employees e2 ON e2.city = e1.city 
   AND (e1.firstname <> e2.firstname AND e1.lastname <> e2.lastname)
ORDER BY
 e1.city;
```

* `e1.city = e2.city`와 같은 도시에 있는 두 직원 이상
* `e1`과 `e2`가 동일한 이름과 성을 가진 직원이 없다는 가정하에 동일한 직원이 아닌지 확인하기 위해 `e.firstname <> e2.firstname AND e1.lastname <> e2.lastname`

![](http://www.sqlitetutorial.net/wp-content/uploads/2015/12/SQLite-self-join-employees-locate-in-the-same-city.jpg)

