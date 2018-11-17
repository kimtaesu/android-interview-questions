## State VS Strategy
![](designpattern/state+strategy.jpg)

State 와 Strategy의 UML은 상당히 닮아있다. 
그래서 더 혼란스럽다. 

Strategy 관련 알고리즘 세트를 캡슐화하고 클라이언트가 런타임시 구성 및 위임을 통해 교환 가능한 동작을 사용할 수있게합니다.
 
반면에 State 은 클래스가 다른 상태에서 다른 동작을 나타낼 수 있게 합니다.

즉, 행동을 일으키는 주체가 다르다는 의미다.

Strategy는 호출하는 Client 가 주체이며 State는 상태를 관리하는 State 가 주체이다.