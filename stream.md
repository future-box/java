# 스트림으로 데이터 수집
- Collectors 클래스로 컬렉션을 만들고 사용하기
- 하나의 값으로 데이터 스트림 리듀스하기
- 특별한 리듀싱 요약 연산
- 데이텉 그룹화와 분할
- 자신만의 커스텀 컬렉터 개발

명령형 프로그래밍과 함수형 프로그래밍의 차이점...

6.1.1 고급 리듀싱 기능을 수행하는 컬렉터  
함수형 API 의 장점은 높은 수준의 조합성과 재사용성이다  
collect 로 결과 수집 과정을 간단하고 유연하게 정의할 수 있다  
다시 말해서 스트림에 collect 를 호출하면 스트림의 요소(컬렉터로 파라미터화된)에 리듀싱 연산이 수행된다  
보통 함수를 요소로 변환할 때는 컬렉터를 적용하며 최종 결과를 저장하는 자료구조에 값을 누적한다  
6.1.2 미리 정의된 컬렉터  
Collectors 에서 제공하는 메서드의 기능은 크게 세 가지로 구분할 수 있다  
- 스트림 요소를 하나의 값으로 리듀스하고 요약
- 요소 그룹화
- 요소 분할(partitioning)

## 6.2 리듀싱과 요약

## 6.5 Collector
- supplier: 새로운 컨테이너 결과 만들기
- accumulator: 결과 컨테이너에 요소 추가하기
- finisher: 최종 변환값을 결과 컨테이너로 적용하기
- combiner: 두 결과 컨네이너 결합 (병렬 리듀싱을 가능하게 해줌)
# Collectors 에서 제공하는 기능 세가지
1. 요약
```
counting
maxBy, minBy
summingInt, summingDouble, summingLong
averagingInt, averagingDouble, averagingLong  
joining
reducing
```
2. 그룹화
```java
groupingBy(Function function);
groupingBy(Function function, Collector collector);
groupingBy(Student::age, filtering(student -> student.level > 2, toList());
groupingBy(Student::age, mapping(Student::name, toList());
groupingBy(Student::age, flatMapi(Student::family, toList());
```
