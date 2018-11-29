## interface VS abstract class 
![](http://3.bp.blogspot.com/-rhSXZG2NY_c/TdIrTbnc9TI/AAAAAAAAAHE/ym2nRMOMZqo/s1600/interfaces_vs_abstract.png)

* 자바에서는 다중상속이 되지 않음  `abstract class` 는 1개만 상속할 수 있음.
* `interface`는 여러개를 선언할 수 있음.

## 스레드란?
우선 `Process` 에 대해 설명 필요.

`Process` 란 운영체제로 부터 주소공간, 파일, 메모리의 자원을 할당받음(하나의 프로그램)

`Thread`란 한 프로세스가 내에서 동작되는 여러 실행의 흐름으로, 프로세스 내의 주소 공간이나 자원들을 대부분 공유하면서 실행된다.

## 동시에 하나의 스레드 쓰는 동안 여러 스레드가 동시에 읽습니다. 이때 발생하는 문제는?
 * DeadLock: 다수의 Thread가 서로의 Lock을 기다리는 상황 
 > [참조](http://icednut.github.io/2016/08/06/20160806-about_deadlock/)
 * Race Condition: 둘 이상의 입력이나 조작이 동시에 일어나 의도하지 않은 결과를 가져오는 경우
 
 * Readers-Writers problem: 하나의 쓰레드에서 쓰는 동시에 읽는 여러 쓰레드.

## DeadLock 발생 환경
교착 상태는 한 시스템 내에서 다음의 네 가지 조건이 동시에 성립 할 때 발생한다.

* 상호배제 (Mutual Exclusion) : 한 순간에 한 프로세스만이 자원을 사용할 수 있다. 즉, 한 프로세스에 의해 점유된 자원을 다른 프로세스들이 접근할 수 없다.
* 점유대기 (Hold and Wait) : 이미 자원을 보유한 프로세스가 다른 자원을 요청하며 기다리고 있다.
* 비선점 (No preemption) : 프로세스에 의해 점유된 자원을 다른 프로세스가 강제적으로 빼앗을 수 없다.
* 환형대기 (Circular Wait) : 프로세스간에 닫힌 연결이 존재할 경우입니다. 블록된 프로세스가 자원을 점유하고 있는데 이 자원을 다른 프로세스가 원하며 대기하고 있는 상태입니다.
### 자바에서 스레드를 생성하는 방식?

1. Runnable 인터페이스를 구현하는 방법
2. Thread 클래스를 상속받는 방법

## What is a `Loader`?

## Explain `Looper`, `Handler` and `HandlerThread`

## Activity에서 Thread를 종료하지 않고 Activity를 종료하면? 

## RxJava를 사용하지 않고 네트워크 통신하는법?