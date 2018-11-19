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