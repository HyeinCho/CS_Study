# 💛 SQL JOIN 연산의 종류와 그에 대한 설명

![image](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b245069f-2c68-4e53-a952-c29a091b9e7d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210625%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210625T182223Z&X-Amz-Expires=86400&X-Amz-Signature=842c0afe396365b3bf4c8f1e261848f62a972e1f2283e74b4e8f8ad2137aec62&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

> `JOIN` : 둘 이상의 테이블을 연결해서 데이터를 검색하는 방법. 연결하기 위해선 테이블들이 적어도 하나의 속성을 공유하고 있어야 한다.(외래키)

### 1. INNER JOIN

- 교집합
    - 두 테이블의 오직 공통적인 부분만 `SELECT` 됨.

        서로 연관된 내용만 검색.

        ```sql
        SELECT I.ANIMAL_ID, I.NAME
        FROM ANIMAL_INS I INNER JOIN ANIMAL_OUTS O
             ON I.ANIMAL_ID = O.ANIMAL_ID
        WHERE O.DATETIME < I.DATETIME
        ORDER BY I.DATETIME
        ```

### 2. LEFT OUTER JOIN

- OUTER JOIN : 조인하는 테이블들에서 한 쪽에는 데이터가 있고 다른 한쪽에는 데이터가 없는 경우, 데이터가 있는 쪽의 테이블의 내용을 모두 출력하는 것.
- 두 테이블 중 왼쪽에 놓은 테이블을 중심으로 하여 오른쪽 테이블을 매치시킨다.
    - 왼쪽은 무조건 표시하고 왼쪽에 매치되는 레코드가 오른쪽에 없다면 NULL 을 표시한다.

        ```sql
        SELECT O.ANIMAL_ID, O.NAME
        FROM ANIMAL_OUTS O LEFT JOIN ANIMAL_INS I
            ON I.ANIMAL_ID = O.ANIMAL_ID
        WHERE I.ANIMAL_ID IS NULL
        ORDER BY O.ANIMAL_ID
        ```

### 3. RIGHT OUTER JOIN

- 두 테이블 중 오른쪽에 놓은 테이블을 중심으로 하여 왼쪽 테이블을 매치시킨다.
    - 오른쪽은 무조건 표시하고 오른쪽에 매치되는 레코드가 왼쪽에 없다면 NULL 을 표시한다.

        ```sql
        SELECT O.ANIMAL_ID, O.NAME
        FROM ANIMAL_INS I RIGHT JOIN ANIMAL_OUTS O
            ON I.ANIMAL_ID = O.ANIMAL_ID
        WHERE I.ANIMAL_ID IS NULL
        ORDER BY O.ANIMAL_ID
        ```

### 4. FULL OUTER JOIN

- LEFT JOIN, RIGHT JOIN 합집합 한 결과.
- 두 테이블 다 상대에게 매치되지 않는 부분은 null 이 될 수 있다.

![image](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/426711b9-3855-4fc7-b43a-00ec06d329d1/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210625%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210625T182151Z&X-Amz-Expires=86400&X-Amz-Signature=ad90e8a736132324997c51f65acb103e880a8af95727fa0d059ab4373f7cc0f1&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

[https://stanleykou.tistory.com/entry/SQL-INNER-조인과-OUTER조인이-무엇인가요](https://stanleykou.tistory.com/entry/SQL-INNER-%EC%A1%B0%EC%9D%B8%EA%B3%BC-OUTER%EC%A1%B0%EC%9D%B8%EC%9D%B4-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80%EC%9A%94)