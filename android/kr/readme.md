## Android application components
* Activity
* Service
* Content Provider
> 콘텐츠 제공자는 공유된 앱 데이터 집합을 관리합니다. 데이터는 파일 시스템이나 SQLite 데이터베이스 또는 웹이나 기타 영구적인 저장소 위치 중 앱이 액세스할 수 있는 곳이라면 어디에든 저장할 수 있습니다.
* BroadcastReceiver

## Structure of an Android Application
![](https://www.dev2qa.com/wp-content/uploads/2018/04/android-architecture-components.png)
[Link](https://www.dev2qa.com/android-architecture-components-introduction/)

## What is `Context`? 
Context 는 System의 핸들이다.

## What is `AndroidManifest.xml`?
Android 시스템이 앱의 코드를 실행하기 전에 확보해야 하는 앱에 대한 필수 정보를 시스템에 제공합니다.

## What is `Application.class`?
Android의 Application 클래스는 활동 및 서비스와 같은 다른 모든 구성 요소가 포함 된 Android 앱의 기본 클래스입니다. Application 클래스 또는 Application 클래스의 하위 클래스는 응용 프로그램 / 패키지의 프로세스가 만들어 질 때 다른 클래스보다 먼저 인스턴스화됩니다.

## LifeCycle Activity Fragment
![](https://github.com/xxv/android-lifecycle/raw/master/complete_android_fragment_lifecycle.png) 

## What is a `LocalBroadcastManager`?
현재 프로세스 안에만 유효한 Broadcast 이다.

## What is the function of an `IntentFilter`?
다른 앱이 자신의 액티비티를 시작할 수 있도록 허용.
<tag>
 

## Service vs IntentService
Service는 UI와 관련되지 않은 작업에 사용되며 수행시간이 길어선 안됩니다. 긴 작업을 수행할 필요가 있다면, 반드시 Service내에서 스레드를 사용해야됩니다.

IntentService는 보통 긴 작업에 사용되며 보통 메인 스레드와 상호작용하지 않습니다.


|    | Service            |		IntentService |
|--------------| ------------------|-----------------------------|
| 시작방법   | startService()              | onHandleIntent()          |
| 동작위치       | mainThread()	            | 각각의 작업 스레드    |
| 제한사항       | 메인 스레드를 막을 수 있습니다         | 평행하게 동작하지 않습니다. 그래서 연쇄적으로 묶여있는 Intent들은 작업 스레드의 메시지 큐로 들어가서 순차적으로 실행될 것입니다.          |
| 멈추는 시기      | stopSelf()나 stopService()        | 모든 요청이 처리된 후에 Service 중지시킵니다  |

## What is a `PendingIntent는`?
PendingIntent는 직접 행동을 하지 않고 다른 컴포넌트에 위임처리를 하는 기능이다

Activity, Broadcast, Service 3가지에 대해서 일반적으로 위젯에 클릭이나, Notification 클릭에 위임한다.

## What are "launch modes"?
TODO

## What is `AAPT2`?
AAPT2 (Android Asset Packaging Tool)는 Android Studio 및 Android Gradle Plugin이 앱 리소스를 컴파일하고 패키지하는 데 사용하는 빌드 도구입니다. AAPT2는 안드로이드 플랫폼에 최적화 된 바이너리 형식으로 리소스를 파싱, 색인화 및 컴파일합니다.

## ART와 가상머신
ART 또한 달빅과 같은 가상머신의 일종이다. 기존 안드로이드는 DEX 파일을 Dalvik 가상머신 위에 올려두고 필요에 따라 실시간으로 컴파일하는 방식이었다. ART를 사용하는 경우는 DEX 파일을 미리 컴파일하여 OAT 파일에 저장해두고 실행 돌리는 것으로 변했을 뿐이다.

## JIT vs AOT?
달빅은 JIT 컴파일러이고, ART는 AOT 컴파일러
JIT는 실행 디바이스에서 매번 번역해야 하므로 느리고, AOT는 미리 번역해서 저장해 두기 때문에 빠르다.
> 안드로이드 누가 이후의 ART VM에서는, JIT와 AOT를 모두 탑재함으로써 최초 설치시에는 무조건 JIT를 사용하도록 하여 설치시간과 용량을 적게 소모하도록 한 뒤, 차후 상황에 따라 각 방식을 유연하게 적용하도록 하였다.

## ContentProvider?
콘텐츠 제공자는 중앙 리포지토리로의 데이터 액세스를 관리합니다. 
이미 안드로이드에서는 음악, 주소록같은 기본적인 어플리케이션이 존재하고있습니다.
기본적인 앱안에는 정보들을 담은 데이터베이스를 구현하고 있습니다.  
기본적인 앱들은 대부분 다른 앱에서 자신의 앱의 데이터베이스에 접근할 수 있도록 도와주는
컨텐트 프로바이더(Content Provider)란 것을 제공해주고 있습니다.
 
## AIDL(Android Interface Definition Language)?
클라이언트와 서비스가 프로세스간 통신(IPC)을 사용하여 서로 소통하는 데 동의한 프로그래밍 인터페이스를 정의할 수 있습니다. 
Android에서는 한 프로세스가 다른 프로세스의 메모리에 정상적으로 액세스할 수 없습니다.
따라서 객체들을 운영 체제가 이해할 수 있는 원시 유형으로 해체하고 해당 경계에 걸쳐 __마샬링__해야 합니다.
이 마샬링을 위해 코드를 작성하는 일은 상당히 지루한 작업인데, 
**Android는 AIDL을 이용해 그 일을 대신 해줍니다.**


## ANR? (Application Not Responding)
UI 업데이트를 담당하는 Main Thread가 사용자 입력 이벤트를 처리할 수 없거나 그릴 수 없을 경우
ANR이 발생합니다. 

다음 조건 중 하나가 발생하면 앱에 대해 ANR이 실행됩니다.
1. 포그라운드 인 경우 키 누름 또는 화면 터치 이벤트를 5 초 이내에 응답하지 않음
2. 포그라운드가 아닌 경우 BroadcastReceiver는 많은 시간 내에 실행을 완료하지 못함.

## Espresso란? 화이트박스 적합
Espresso 테스트 프레임워크는 앱 내부의 사용자 흐름을 테스트하는 UI 테스트를 빌드하기 위한 API 세트를 제공합니다. 이런 API를 사용하면 간결하고 안정적으로 실행되는 자동화된 UI 테스트를 작성할 수 있습니다 

## UI-Automator? 블랙박스 적합
UI Automator 테스트 프레임워크는 사용자 앱과 시스템 앱에 대한 상호작용을 수행하는 UI 테스트를 빌드하기 위한 API 세트를 제공합니다. UI Automator API를 사용하면 테스트 기기에서 Settings 메뉴 또는 앱 런처 열기와 같은 작업을 수행할 수 있습니다. UI Automator 테스트 프레임워크는 블랙 박스 스타일의 자동화된 테스트를 작성하기에 매우 적합하며, 여기서는 테스트 코드가 대상 앱의 내부적 구현 세부정보에 의존하지 않습니다.

## Bitmap pool?
![](https://mindorks.files.wordpress.com/2018/01/7fa8a-1hzip5f1xjv039k-m1zmnza.png)
비트 맵 풀을 사용하여 응용 프로그램에서 메모리 할당 및 할당 취소를 방지하면 GC 오버 헤드가 줄어들어 응용 프로그램이 원활하게 실행됩니다.

> 이를 수행하는 한 가지 방법은 [inBitmap](https://developer.android.com/reference/android/graphics/BitmapFactory.Options#inBitmap) (비트 맵 메모리를 다시 사용)을 사용하는 것입니다.


## OOM ? 
메모리 부족 오류가 발생하는 데는 여러 가지 이유가 있습니다.
1. 지속적으로 많은 메모리를 요구하는 작업을하고 있으며 어느 시점에서 프로세스의 최대 힙 메모리 제한을 초과합니다.
2. 일부 메모리가 누출되었습니다. 즉, 할당 한 이전 오브젝트를 가비지 콜렉션 (GC)에 적합하게 만들지 않았습니다. 이를 메모리 누출이라고합니다.
3. 큰 비트 맵을 처리하고 런타임에 모두를 로드.

## 배터리 개선 팁
* 가능한 한 네트워크 호출을 줄이자. 
> 다음에 필요할 때 데이터를 캐시하고 캐시에서 검색하십시오.
* 화면을 깨우지 말자.
* AlarmManager를 신중하게 사용하자.
* 네트워크 호출 배치하기
 > 가능한 한 매초마다 장치가 깨지 않도록 네트워크 호출을 배치한다.
* 모바일 데이터와 Wifi의 로직 분리
* 모든 백그라운드 프로세스 확인
> 모든 백그라운드 프로세스를 확인
* 신중하게 GPS를 사용하자 
> 자주 사용하지 마십시오. 실제로 필요할 때만 사용하십시오.
* Use JobScheduler : 이것은 응용 프로그램의 자체 프로세스에서 실행될 프레임 워크에 대해 다양한 유형의 작업을 예약하기위한 API입니다. 이 프레임 워크는 콜백을 받고 가능한 일괄 처리 및 연기를 시도 할 때 지능적입니다.

## OverDraw? 
앱은 하나의 프레임 내에서 동일한 픽셀을 두 번 이상 그릴 수 있습니다.
이 이벤트는 오버 드로 (overdraw) 이벤트입니다. 
오버 드로우는 일반적으로 불필요하며 가장 잘 제거됩니다. 
GPU 시간을 낭비하여 성능상의 문제로 드러납니다.

## DEX?
dex 파일은 Dalvik VM에서 실행되는 파일입니다.
![](https://image.slidesharecdn.com/incognitoandroiddex-151003141208-lva1-app6891/95/inc0gnito-2015-android-dex-analysis-technique-7-638.jpg?cb=1443881619)

## HashMap VS ArrayMap

![](https://cdn-images-1.medium.com/max/800/1*v1_3ug_tpscGtYc7JxP2Og.png)
ArrayMap 은 int[] (mHashes)와 Object[] (mArray) 총 두 개의 array 를 사용하여 map 을 관리한다.
HashMap 은 O(1) 의 complexity 를 갖지만, ArrayMap 은 O(log n)의 binary search

HashMap 은 O(1) 의 성능을 가지지만, memory 는 더 사용하게 된다.
메모리를 더 사용하는 이유는, 사용하지 않는 공간을 allocate 해놓고, 불필요한 class 인 HashMap.Entry 사용 이슈 때문,
또 하나는 HashMap 이 축소되거나 확장될 때마다 bucket 이 rearrange 된다는 점이다.

## HashMap VS SparseArray
각 인덱스 사이에 공간을 만들 수 있다. 
index 1~10 번 Item, 11~20 은 비우고, 30~40 번은 아이템 

* 메모리 효율 
* No boxing

## View 호출 순서 
![](https://t1.daumcdn.net/cfile/tistory/211625375716700B04)
#### onMeasure
View의 크기를 결정할 때 불리는 함수이다.
> View.measure() -> View.onMeasure() -> View.setMeasuredDimesion()
#### onLayout
child view의 위치를 잡아주는 일을 한다. onMeasure 호출 후에 onLayout 이 호출 되므로 자신의 크기를 이미 인지하는 상태에서 위치를 잡아 줄 수 있다.

주의할 점은 이 위치가 장비 디스플레이의 절대적 위치이다. 부모를 기준으로한 상대적인 위치가 아니다.
> ViewGroup.layout()-> View.layout() -> View.onLayout()

#### onDraw
화면을 그리는 일을 한다.

## View 최적화
* 필요없는 invalidate() 는 제거해라
* requestLayout() 는 자주 사용하지 말아라
> requestLayout를 호출할때마다 모든 View를 탐색하며 크기를 알아야 한다.

## invalidate() vs requestLayout() 
invalidate는 화면이 유효하지 않으니 다시 그리도록 하라는 것

requestLayout()은 layout을 갱신하라는 것이다.
