### 접속
    psql -U [유저명] [db명]

### 행 단위로 보기
    \x on

### 열 나눠서 보기
    \setenv PAGER 'less -S'

### sequence 초기화
    alter sequence [sequence명] restart with 1

### sql 파일실행
    psql -U [유저명] -d [db명] -a -f [sql파일명]

### table 목록
    select * from information_schema.tables

### sequence 목록
    select * from information_schema.sequences

### index 확인
    select * from pg_indexs where tablename not like 'pg%'

### empty column 확인
    where ([column] = '') is not false
