# Citus 설치
 - https://github.com/citusdata/citus#install-citus-locally

## Centos
1. Citus 설치
    ```bash
    $ curl -fsSL https://install.citusdata.com/community/rpm.sh | sudo sh
    $ yum install -y citus100_13
    ```
2. `postgresql.conf`에 설정 추가
    ```conf
    shared_preload_libraries = 'citus'
    ```
3. PostgreSQL 재실행
4. citus 확장 SQL 실행
    ```sql
    CREATE EXTENSION citus;
    ```