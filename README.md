# DB - STUDY

## Modeling

모델링은 보통 "요구사항 > 개념적 모델링 > 논리적 모델링 > 물리적 모델링" 순서로 진행 된다.

### 개념적 모델링

#### 구성 요소
- Entity = Table (□)
- Attribute = Column (○)
- Relation = PK, FK, JOIN (◇)
- Tuble = Row

#### 관계
엔티티간 연결할때는 Relation이 필요하다.

- Cardinality
  - 1:1
  - 1:N
  - N:M

- Optionality
  - Mandatory, Optional (필수 불가결 요소 체크 )

#### 키 종류
- Candidate key (식별자가 될 수 있는 후보키)
  - Primary key (기본키)
  - Alternate key (기본키가 아닌 키들) - 성능을 위해 Secondary index로 활용될 수 있음


### 논리적 모델링
- 관계에 따른 테이블 및 데이터 구성

#### 정규화
1. 1NF (Atomic columns)
  - 컬럼의 데이터가 원자성을 확보해야한다. 한 컬럼에 여러 값이 있으면 않됨 (조인 등에 있어 문제가 될 수 있음)
2. 2NF (No partial dependencies)
  - 부분 종속성이 없어야 하는데, 이는 테이블에 중복키가 있는지 확인해야 한다.
2. 3NF (No transitive dependencies)
  - 이행 종속성 제거

### 물리적 모델링
경험이 있다면 초기 단계에 모델링 하면 좋겠지만, 예측되지 않는 슬로우 쿼리들이 존재할 수 있으니 운영을 하면서 병목이 발생하는 부분들을 어떻게 개선하고 최적화 시킬지 설계하는 모델링

최후에까지 성능을 개선하지 못한다면 역정규화를 고려해 볼 수도 있겠지만, 데이터가 쌓여있는 상태에서는 이 공수는 너무나도 크다. 그렇기에 "index, application level에서의 cache, view, excution plane을 분석하여 query optimization"등을 우선적으로 고려해보는 것이 좋다.

## DB common sense

## PostgreSQL
데이터에 대한 조회나 추가에 대한 성능이 뛰어나다. 대용량 데이터 핸들링 모델에 적합함. (업데이트는 데이터를 삭제하고 추가시키는 방식이어서 비용이 더 들 수 있다.)

### 인덱스의 종류
(B-Tree, Hash, GIN, GiST, BRIN) / 리빌드 및 특징

### jsonb

### excution plan
