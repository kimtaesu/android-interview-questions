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

## onDestroy 만 onPause () 및 onStop ()이없는 활동에 대해 호출되는 시나리오?
액티비티의 `OnCreate` 메소드에서 `finish()`가 호출되면 시스템은 `onDestroy()` 메소드를 직접 호출합니다

## Launch modes
![](https://t1.daumcdn.net/cfile/tistory/14183E484E8BA55228)

### Standard
A -> B -> C    start(B)
> A -> B -> C -> B.

### SingleTop
A -> B -> C.   start(C)
> A -> B -> C

### SingleTask
A -> B -> C -> D.  start(D)
> A -> B -> C -> D

A -> B -> C -> D. start(B)
> A -> B  (C, D destroyed)

### SingleInstance
 A -> B -> C -> D
 
 
 ### FLAG_ACTIVITY_NEW_TASK
 액티비티를 새 작업에서 시작합니다. 지금 시작하고 있는 액티비티에 대해 이미 실행 중인 작업이 있으면, 해당 작업의 마지막 상태를 복원하여 포그라운드로 불려나오고 액티비티는 새 인텐트를 `onNewIntent()`에서 수신합니다.
 이렇게 하면 `"singleTask"` launchMode 값과 동일한 동작이 발생하며, 이는 이전 섹션에서 논한 것과 동일합니다.
 
 ###  FLAG_ACTIVITY_SINGLE_TOP
 시작되고 있는 액티비티가 현재 액티비티인 경우(백 스택 맨 위에 있는), 해당 액티비티의 새 인스턴스를 생성하는 대신 기존 인스턴스가 `onNewIntent()`에 대한 호출을 받습니다.
 이렇게 하면 `"singleTop"` launchMode 값과 동일한 동작이 발생하며, 이는 이전 섹션에서 논한 것과 동일합니다.
 
 ### FLAG_ACTIVITY_CLEAR_TOP
> RootActivity는 남음

 시작되고 있는 액티비티가 이미 현재 작업에서 실행 중인 경우, 해당 액티비티의 새 인스턴스를 시작하는 대신 그 위에 있는 모든 다른 액티비티가 소멸되고 이 인텐트는 해당 액티비티(이제 맨 위로 올라옴)의 재개된 인스턴스로, onNewIntent()를 통해 전달됩니다.
 ![](https://t1.daumcdn.net/cfile/tistory/2435BA4150F15C812A)
 
 ### 스택에 쌓여있는 모든 Activity를 지우는 법
 FLAG_ACTIVITY_CLEAR_TASK | FLAG_ACTIVITY_NEW_TASK 
 
 FLAG_ACTIVITY_CLEAR_TASK : 호출 된 클래스의 기존 인스턴스를 포함하여 태스크에서 모든 활동을 지우는 데 사용됩니다.
 
 FLAG_ACTIVITY_NEW_TASK : 새로운 TASK를 생성한다. (Activity가 아닌 곳에서 Activity를 띄울 때, 종종 사용하는 플래그)
 
 ## 화면이 회전되면
 화면이 회전되면 현재 활동 인스턴스가 삭제되고 새로운 활동 인스턴스가 새 방향으로 작성됩니다. `onRestart()` 메서드는 화면이 회전 될 때 먼저 호출됩니다.
 
 ## ContentProvider 사용법
 `ContentResolver.query()`
 
 ## Service
 * Foreground Service: StartForeground() notification 이 보여줘야함
 * Background Service: Android API 레벨 26 이상에서는 백그라운드 서비스 사용에 제한이 있으며 이러한 경우 WorkManager를 사용하는 것이 좋습니다.
 * Bound Service: 바운드 서비스는 구성 요소가 서비스와 상호 작용하고 요청을 보내며 결과를 수신 할 수있게 해주는 클라이언트 - 서버 인터페이스를 제공합니다.
 
 ## Service vs IntentService
 Service는 UI와 관련되지 않은 작업에 사용되며 수행시간이 길어선 안됩니다. 긴 작업을 수행할 필요가 있다면, 반드시 Service내에서 스레드를 사용해야됩니다.
 
 IntentService는 보통 긴 작업에 사용되며 보통 메인 스레드와 상호작용하지 않습니다.
 
 
 |    | Service            |		IntentService |
 |--------------| ------------------|-----------------------------|
 | 시작방법   | startService()              | onHandleIntent()          |
 | 동작위치       | mainThread()	            | 각각의 작업 스레드    |
 | 제한사항       | 메인 스레드를 막을 수 있습니다         | 평행하게 동작하지 않습니다. 그래서 연쇄적으로 묶여있는 Intent들은 작업 스레드의 메시지 큐로 들어가서 순차적으로 실행될 것입니다.          |
 | 멈추는 시기      | stopSelf()나 stopService()        | 모든 요청이 처리된 후에 Service 중지시킵니다  |

## AsyncTask 
* `execute()` 명령어를 통해 `AsyncTask`을 실행합니다.
* `AsyncTask`로 백그라운드 작업을 실행하기 전에 `onPreExcuted()`실행됩니다.
* `doInBackground()` 실제 Background로 실행하는 함수 `publishProgress()` 를 호출하여 UI 업데이트를 할 수 있음
* `onProgressUpdate()` publishProgress( )가 호출 될 때  마다 자동으로 호출됩니다.
* `onPostExcuted()`  `doInBackground()` 메소드에서 작업이 끝나면 결과 파라미터를 리턴하면서 그 리턴값을 통해 스레드 작업이 끝났을 때의 동작을 구현합니다.

## AsyncTask와 Activity의 Lifecycle 관계?
사용자가 장치를 회전하면 `Activity`가 삭제되고 새로운 Activity 인스턴스가 만들어 지지만 `AsyncTask`는 종료되지 않고 완료 될 때까지 계속 살아갑니다.
* 메모리 누수 (AsyncTask가 Activity에 대한 참조를 유지)
* findViewById를 사용하여 Activity 내부의 뷰를 검색하는 경우 Crash 가 발생할 수 있습니다.
## Handler 
핸들러는 스레드를 관리하기위한 객체입니다. 메시지를 수신하고 메시지 처리 방법에 대한 코드를 작성합니다.
 
 ## ThreadPool
 ThreadPool은 작업 큐와 작업 스레드 그룹으로 구성되어 작업의 여러 병렬 인스턴스를 실행할 수 있습니다.
 
 ## 백그라운드 서비스에서 Activity의 UI를 어떻게 업데이트합니까?
 `Acivity`에 LocalBroadcastReceiver를 등록해야합니다.
 메모리 누수를 피하려면 활동의 `onStop()` 메소드에서 브로드 캐스트 리시버의 등록을 취소하십시오.
 
 ## Fragment LifeCycle
1. onAttach :  Activity에서 Fragment가 호출될 때 제일 처음으로 호출된다.
> 여기에서 Activity가 전달됩니다

![](/need/onAttach.png)
2. onCreate :  Fragment가 생성되는 시점.
3. onCreateView:  View 가 Inflate되는 시점에 호출된다.
4. onActivityCreated:  Activity가 `onCreate()` 가 호출 될 때 호출된다.
5. onStart: Fragment가 화면에 표시될때 호출된다.
6. onResume :  Fragment가 화면에 표시되고 포커스를 갖고 있을 때 호출된다. 
7. onPause :  Fragment가 포커스를 갖고 있지 않을 경우 호출된다.
> 현재 사용자 세션을 넘어서 지속되어야 하는 변경 사항을 커밋하려면 보통 이곳에서 해야 합니다(사용자가 돌아오지 않을 수 있기 때문입니다).
8. onStop :  Fragment가 화면에 사라질때 호출된다.
9. onDestroyView:  Fragment 의 view가 사라지는 시점
> 리소스들을 반환시켜야 한다면 여기서 반환하자

10. onDestory :  Fragment가 완전히 종료되는 시점.
11. onDetach : Activity와 연결이 끊어질 때 호출된다.

## Activity vs Fragment
`Activity`는 화면을 제공하는 애플리케이션 구성 요소입니다. 

`Fragment`는 `Activity`의 동작이나 사용자 인터페이스의 일부를 나타냅니다

## Fragment Add vs Replace
### Replace
replace는 기존 Fragment을 제거하고 새 Fragment을 추가합니다. 
즉, 다시 버튼을 누르면 대체 된 Fragment가 호출되고 onCreateView가 호출됩니다.

### Add  
기존 존재하는 Fragment 추가한다. `paused` 상태가 되지 않는다.

## Retained Fragments?
`setRetainInstance(true)`를 호출하면이 destroy-and-recreate 사이클을 우회하여 작업이 다시 생성 될 때 조각의 현재 인스턴스를 유지하도록 시스템에 신호를 보냅니다.

## FragmentPagerAdapter와 FragmentStatePagerAdapter의 차이점
`FragmentPagerAdapter` 메모리 상에 저장되어있는 Fragment를 사용
`FragmentStatePagerAdapter`는 이전 Fragment는 메모리 상에서 제거된다. 
 
## ANR? (Application Not Responding)
UI 업데이트를 담당하는 Main Thread가 사용자 입력 이벤트를 처리할 수 없거나 그릴 수 없을 경우
ANR이 발생합니다. 

다음 조건 중 하나가 발생하면 앱에 대해 ANR이 실행됩니다.
1. 포그라운드 인 경우 키 누름 또는 화면 터치 이벤트를 5 초 이내에 응답하지 않음
2. 포그라운드가 아닌 경우 BroadcastReceiver는 많은 시간 내에 실행을 완료하지 못함.
## Bitmap pooling in android?
## How to load bitmap to memory
[참조](https://android.jlelse.eu/loading-large-bitmaps-efficiently-in-android-66826cd4ad53)
## SharedPreference commit VS apply
`commit()`은 데이터를 동기적으로 기록하고 즉시 결과에 따라 부울 값의 성공 또는 실패를 반환합니다.

`apply()`는 비동기 적이며 return Boolean을 반환하지 않습니다.
## How does RecyclerView work?
100개의 아이템을 표시한다고 가정

10개 정도의 항목만 화면에 표시되고 

스크롤이 되면 새로운 행마다 새로운 View를 작성하는 대신 이전 View에 새로운 데이터를 바인딩하여 재활용되고 재사용됩니다.
## What are the permission protection levels in Android?
Normal 

Dangerous 

Signature 

SignatureOrSystem 

## Arraymap/SparseArray vs HashMap in Android?
[참조](https://android.jlelse.eu/app-optimization-with-arraymap-sparsearray-in-android-c0b7de22541a)
## APK Size 줄이기
* Proguard
* shrinkResources
* "resConfigs"
* Vector Drawable

## MVC VS MVP VS MVVM 


## 애자일
 
![](https://gscaltexmediahub.com/wp-content/uploads/2018/01/2018_Jan_officeIN_04_02-2.jpg)

**즉, 한 마디로 "협력과 피드백을 자주! 일찍! 더 잘하는 것!" 이다.**
### 애자일 선언문
* 공정과 도구보다 **개인과 상호작용**을
* 포괄적인 문서보다 **작동하는 소프트웨어**를
* 계약 협상보다 **고객과의 협력**을
* 계획을 따르기보다 **변화에 대응하기**를
 
왼쪽에 있는 것들도 가치가 있지만, 우리는 오른쪽에 있는 것들에 더 높은 가치를 둔다는 것이다.

### 애자일 개발 프로세스
![](https://cdn-images-1.medium.com/max/720/1*khv-SSIP1TEfmbpnjGwclA.png)
* 익스트림 프로그래밍(Extreme Programming, XP)
    - 테스트우선 개발(TDD)을 특징으로 하는 명시적인 기술과 방법을 가지고 있다. 
* 스크럼 
    - 프로젝트 관리 중심의 방법론이다.
    - 30일마다 동작 가능한 제품을 제공하는 스프린트(Sprint)를 중심으로 하고 있다. 매일 정해진 시간에 정해진 장소에서 짧은시간의 개발을 하는 팀을 위한, 
### 스크럼
1. 제품 백로그(Product Backlog) 
  - 개발할 제품에 대한 요구 사항 목록
2. 스프린트 계획 회의(Sprint Planning Meeting) 
 -  스프린트 목표와 스프린트 백로그를 계획하는 회의
5. 일일 스크럼 회의(Daily Scrum Meeting) 
 -  날마다 진행되는 미팅 (어제 한일, 오늘 할일, 장애 현상 등을 공유)
6. 실행 가능한 제품(shippable product) 개발 
-  스프린트의 결과로써 나오는 실행 가능한 제품
> 스프린트 백로그(Sprint Backlog) 
 -  각각의 스프린트 목표에 도달하기 위해 필요한 작업 목록
 
> 스프린트(Sprint) 
  - 반복적인 개발 주기 (회사에서 정하는 이터레이션이 개발 주기가 된다. 계획 회의 부터 제품 리뷰가 진행 되는 날짜 까지의 기간이 1스프린트 이다)
 
![](http://tryqa.com/wp-content/uploads/2014/12/scrum-methodology.gif)

