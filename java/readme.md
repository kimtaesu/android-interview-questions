
#### equal
equal: 두 객체의 내용이 같은지, 동등성(equality) 를 비교하는 연산자 

#### hashCode
hashCode: 두 객체가 같은 객체인지, 동일성(identity) 를 비교하는 연산자

#### hashCode()는 결정되는걸까요?
hashCode()로 native call을 하여 Memory에서 가진 해쉬 주소값을 출력합니다.

### HashTable VS HashMap
|  | 동기화 지원| null 값 허용 |
|---|:---:|:-----:|
|HashTable|O|X| 
|HashMap|X|O|

HashMap 과 Hashtable 은 둘다 사용되는 동안 맵의 순서를 보장하지 않는다. 순서 보장을 원하면 LinkedHashMap 를 사용하라.

쓰레드를 사용하지 않는 애플리케이션들에 대해서는 HashMap 사용이 선호된다. 간단히 말해서 unsynchronized 이거나 단일 쓰레드 애플리케이션에서는 HashMap 일 사용해라.

최신 자바 Jdk 1.8 에서는 현재 Hashtable 클래스가 구식클래스로 되어 있으므로 사용을 안하는 것이 낫다. 오라클은 ConcurrentHashMap 라는 Hashtable 의 더 나은 대체제를 제공하고 있다. 멀티 쓰레드 애플리케이션에 대해서는 Hashtable 보다 ConcurrentHashMap 을 선호한다.