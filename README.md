## elk setting

1. docker-compose를 실행시킨다.
2. logstash는 logstash.conf파일을 읽어 실행시킨다.
3. 처음 실행시키면 생성된 db에 member라는 테이블이 없기 때문에 member라는 테이블을 만들어준다.
   ```agsl
   CREATE TABLE member (
    idx INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    age INT NOT NULL,
    modified_at TIMESTAMP NULL DEFAULT NULL ON UPDATE CURRENT_TIMESTAMP,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP);
    ```
   ```agsl
   INSERT INTO member (name, age) VALUES 
    ('Alice', 25),
    ('Bob', 30),
    ('Charlie', 35),
    ('Diana', 28),
    ('Edward', 45),
    ('Fiona', 32),
    ('George', 29),
    ('Hannah', 27),
    ('Ivan', 31),
    ('Julia', 40);
    ```
4. logstash 로그를 보면 설정한 시간(10초)마다 select쿼리가 날라가는 것을 확인