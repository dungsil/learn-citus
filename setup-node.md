# 노드 설정
 - https://github.com/citusdata/citus#install-citus-on-multiple-nodes

## 1. 코디네이션 노드 설정
워커 노드를 추가하기 전 코디네이션 노드를 설정해주어야 합니다.
코디네이션 노드는 사용자의 요청을 받아 워커 노드에게 요청을 분배하는 역할을 합니다.

```sql
SELECT citus_set_coordinator_host('coordination', 5500);
```

## 2. 워커노드 추가
```sql
SELECT citus_add_node('work1', 5432);
SELECT citus_add_node('work2', 5432);
SELECT citus_add_node('work3', 5432);
```

## 3. 샤드 재정렬
워커 노드 추가 후 새로운 워커에 샤드를 재정렬합니다.
```sql
SELECT rebalance_table_shards();
```