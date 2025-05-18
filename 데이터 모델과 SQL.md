데이터 모델과 SQL
-----------------

정규화(Normalizatino)
--------------------

### <제1정규형>
1) 모든 속성은 반드시 하나의 값만 가져야 한다. (아래 그림은 예시)
![image](https://github.com/user-attachments/assets/7ae7413f-bf8d-4868-bb1e-0a75109c12e6)
- - -
### <제2정규형>
1) 엔터티의 모든 일반속성은 반드시 모든 주식별자에 종속되어야 한다. (아래 그림은 예시)
![image](https://github.com/user-attachments/assets/8845b33b-6971-475d-8f51-748160763b4a)
- - -
### <제3정규형>
1) 주식별자가 아닌 모든 속성 간에는 서로 종속될 수 없다. (아래 그림은 예시)
![image](https://github.com/user-attachments/assets/44d26f5f-7dc0-4b61-bb1a-89742641ceb3)
- - -
### <주의사항>
- 지나친 정규화는 오히려 성능 저하를 일으킬 수 있다.
1) 회원의 배송상태를 조회하려면 여러 번의 JOIN을 해야 함

![image](https://github.com/user-attachments/assets/1b271969-8bb1-4d34-a86a-c489da2db130)

위와 같은경우 회원의 배송상태를 조회하기 위해서는 여러 번의 JOIN이 불가피하다. 이럴 때는 오히려 반정규화를 통해 성능을 개선해야 하는데 이것은 어떤 측면의 성능을 우선으로 할 것이냐의 딜레마일 수 있다.

4) 회원 엔터티와 배송 엔터티 간의 관계를 생성하여 성능 개선

![image](https://github.com/user-attachments/assets/40c5cf88-aa9e-48d9-bf79-11f2e6a33794)
- - -

반정규화(De-Normalizatino)
-------------------------

### <반정규화>
1) 데이터 조회 성능을 향상시키기 위해 데이터의 중복을 허용하거나 데이터를 그룹핑하는 과정이다. 여기서 주의해야 할 점은 조회 성능은 향상될 수 있으나 입력, 수정, 제거 성능은 저하될 수 있으며 데이터 정합성 이슈가 발생할 수 있다. 반정규화의 과정은 정규화가 끝난 후 거치게 되며 정규화와 마찬가지로 일정한 룰이 존재한다.
- - -
### <테이블 반정규화>	
![image](https://github.com/user-attachments/assets/ac35b15c-fa29-4f0c-89d5-a25fabe7a742)
1) 테이블 병합 : 업무 프로세스상 JOIN이 필요한 경우가 많아 테이블을 통합하는 것이 성능 측면에서 유리할 경우 고려한다. 1 : M 관계 테이블 병합의 경우 1쪽에 해당하는 엔터티의 속성 개수가 많으면 병합했을 경우 중복 데이터가 많아지므로 테이블 병합에 적절하지 못하다.
- 1 : 1 관계 테이블 병합

![image](https://github.com/user-attachments/assets/ecfedce2-a971-41e3-9138-6cb4f1fcd5b4)

- 1 : M 관계 테이블 병합

![image](https://github.com/user-attachments/assets/71bb8421-298c-421f-abb5-ea7e0de664f5)

2) 테이블 분할
- 테이블 수직 분할 : 엔터티의 일부 속성을 별도의 엔터티로 분할(1 : 1 관계 성립)한다.
![image](https://github.com/user-attachments/assets/c387682e-e3ee-452e-a175-4595cbf354bb)
- 테이블 수평 분할 : 엔터티의 인스턴스를 특정 기준으로 별도의 엔터티로 분할(파티셔닝)한다.
![image](https://github.com/user-attachments/assets/bddf6909-d01f-4c0b-a40f-82a8f5deffbc)
3) 테이블 추가
- 중복 테이블 추가 : 데이터의 중복을 감안하더라도 성능상 반드시 필요하다고 판단되는 경우 별도의 엔터티를 추가한다.
- 통계 테이블 추가

![image](https://github.com/user-attachments/assets/4c0268e6-0b2a-4b8f-9167-89fdaf561373)

- 이력 테이블 추가

![image](https://github.com/user-attachments/assets/ad4b2441-bff4-43a8-a132-9ac40e752fe8)

- 부분 테이블 추가

![image](https://github.com/user-attachments/assets/453676d2-5be4-4710-9b56-bde92189e4d2)
- - -
### <컬럼 반정규화>
1) 중복 컬럼 추가 : 업무 프로세스상 JOIN이 필요한 경우가 많아 컬럼을 추가하는 것이 성능 측면에서 유리할 경우 고려한다.
2) 파생 컬럼 추가 : 프로세스 수행 시 부하가 염려되는 계산값을 미리 컬럼으로 추가하여 보관하는 방식으로 상품의 재고나 프로모션 적용 할인가 등이 이에 해당할 수 있다.
3) 이력 테이블 컬럼 추가 : 대량의 이력 테이블을 조회할 때 속도가 느려질 것을 대비하여 조회 기준이 될 것으로 판단되는 컬럼을 미리 추가해 놓는 방식이다. 최신 데이터 여부 등이 이에 해당하 수 있다.
- - -
### <관계 반정규화(중복 관계 추가)>
1) 업무 프로세스상 JOIN이 필요한 경우가 많아 중복 관계를 추가하는 것이 성능 측면에서 유리할 경우 고려한다.
- - -

트랜잭션(Transaction)
--------------------

### <트랜잭션>
1) 데이터를 조작하기 위한 하나의 논리적인 작업 단위이다.
- - -

NULL
----

### <NULL이란?>
- NULL은 존재하지 않음, 즉 값이 없을 의미한다.

![image](https://github.com/user-attachments/assets/901a9d2e-664c-4758-baba-4ddd07c1fe1a)

위 데이터에서 대학생 강산의 수입은 0원이지만 프리랜서 이로운의 수입은 NULL이다. 두 개의 데이터가 갖는 의미는 엄연히 다르다. 결론적으로 이로운의 수입은 0원일 수도 있고 수천만 원일 수도 있다. 어떠한 사유로 데이터가 입력되지 않아 NULL값이 된 것이다.
1) SELECT 수입 - 지출 FROM 테이블

![image](https://github.com/user-attachments/assets/5535ab2e-d853-42e6-babe-b1cb6f6a066f)

-> 가로 연산 : NULL이 포함되어 있으면 결과값은 NULL이 된다.
3) SELECT SUM(수입) FROM 테이블

![image](https://github.com/user-attachments/assets/b0923348-e935-4de3-96a4-9c4894787145)

-> 세로 연산 : 다른 인스턴스의 데이터와 연산할 때는 NULL값을 제외한다.

