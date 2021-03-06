
## equal & hashCode
equal: 두 객체의 내용이 같은지, 동등성(equality) 를 비교하는 연산자 

hashCode: 두 객체가 같은 객체인지, 동일성(identity) 를 비교하는 연산자

### hashCode()는 결정되는걸까요?
hashCode()로 native call을 하여 Memory에서 가진 해쉬 주소값을 출력합니다.

### HashTable VS HashMap
|  | 동기화 지원| null 값 허용 |
|---|:---:|:-----:|
|HashTable|O|X| 
|HashMap|X|O|

HashMap 과 Hashtable 은 둘다 사용되는 동안 맵의 순서를 보장하지 않는다. 순서 보장을 원하면 LinkedHashMap 를 사용하라.

쓰레드를 사용하지 않는 애플리케이션들에 대해서는 HashMap 사용이 선호된다. 간단히 말해서 unsynchronized 이거나 단일 쓰레드 애플리케이션에서는 HashMap 일 사용해라.

최신 자바 Jdk 1.8 에서는 현재 Hashtable 클래스가 구식클래스로 되어 있으므로 사용을 안하는 것이 낫다. 오라클은 ConcurrentHashMap 라는 Hashtable 의 더 나은 대체제를 제공하고 있다. 멀티 쓰레드 애플리케이션에 대해서는 Hashtable 보다 ConcurrentHashMap 을 선호한다.

## Collections and Generics
Arrays vs ArrayLists.

HashSet vs TreeSet.

HashMap vs Set

Stack vs Queue


## Generic

클래스, 인터페이스 및 메서드를 정의 할 때 유형 (클래스 및 인터페이스)을 매개 변수로 사용할 수 있습니다. 
메서드 선언에 사용 된보다 익숙한 형식 매개 변수와 마찬가지로 형식 매개 변수는 다른 코드로 동일한 코드를 다시 사용할 수있는 방법을 제공합니다. 
차이점은 형식 매개 변수에 대한 입력은 값이고 입력 매개 변수에 대한 입력은 유형이라는 점입니다.

## JVM String

* new String("")
* literal

 
JVM에는 String을 저장해두는 String pool 이라는 공간이 있다. 
Java6 에서는 `Perm`이라는 곳에 존재했고
Java7 부터 `Heap` 영역으로 옮겨지게 됬다.
옮겨지게 된 배경은 OOM 문제가 있었기 때문.

`Heap` 으로 옮겨지게 되면서 참조하는 객체가 없을 경우 GC 가 발생한다. 

literal 은 내부적으로 String.intern() 함수를 호출하고 
intern()은 String을 String pool에 저장한다. 

[참조@joongwon](https://medium.com/@joongwon/string-%EC%9D%98-%EB%A9%94%EB%AA%A8%EB%A6%AC%EC%97%90-%EB%8C%80%ED%95%9C-%EA%B3%A0%EC%B0%B0-57af94cbb6bc)

## Auto Boxing / UnBoxing
int와 Integer는 Java 언어에서 서로 바꿔서 사용할 수 있습니다. void giveMeInt (int i) {...}는 Integer를 매개 변수로 취할 수 있습니다.

### String vs StringBuffer vs StringBuilder 

| 구분 | String    | StringBuffer | StringBuilder |
|------|-----------|--------------|---------------|
| 속성 | immutable | mutable      | mutable       |
| 성능 | 느림      | 중간         | 빠름          |

#### String vs StringBuffer, StringBuilder
String은 불변이기 때문에 String 조작을 할때마다 새로운 객체가 생성된다. GC 발생

그렇기 때문에 가장 느리다.

#### StringBuffer vs StringBuilder
StringBuffer thread-safe 하다. 
그렇기 때문에  StringBuilder 보다 느리다.

### Enumeration vs Iterator
![](https://javaconceptoftheday.com/wp-content/uploads/2016/01/EnumerationVsIterator.png?x70034)

### fail-fast vs fail-safe
`ConcurrentModificationException` Fail-Fast 시스템은 가능한 빨리 작업을 중단하고 즉시 오류를 표시하고 전체 작업을 중지합니다.

반면 Fail-Safe 시스템은 장애 발생시 작동을 중단하지 않습니다. 이러한 시스템은 가능한 한 실패를 높이 려하지 않습니다.

#### fail-safe 의 단점

Iterator가 실제 Collection 대신 **복제본**에서 작동하므로 Collection에서 업데이트 된 데이터를 반환하는 것이 보장되지 않는다는 것입니다.

또 다른 단점은 시간과 메모리 측면에서 Collection의 복사본을 만드는 오버 헤드입니다.

`ConcurrentHashMap`, `CopyOnWriteArrayList` 등의 `java.util.concurrent` 패키지로부터의 콜렉션의 `Iterator`는 사실상 Fail-Safe입니다.

