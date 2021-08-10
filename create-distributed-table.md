# 분산테이블 생성하기

## 분산테이블 생성
데이터를 분산해서 저장하는 분산테이블

```sql
SELECT create_distributed_table('events', 'device_id');
```
`create_distributed_table`는 워커 노드로 분할되어 저장됩니다.

## 2. 레퍼런스 테이블 생성
데이터를 분산하지 않고 모든 워커 노드에 복제하는 테이블입니다.
데이터 타입 등 양이 많지 않고 속도를 위해 사용됩니다.

```sql
SELECT create_reference_table('table_name');
```

## 3. 컬럼지향 테이블 생성
`CREATE TABLE`문에 `USING columnar`을 붙여서 만들 수 있다.

```sql
CREATE TABLE events_columnar (
  device_id bigint,
  event_id bigserial,
  event_time timestamptz default now(),
  data jsonb not null
)
USING columnar;
```