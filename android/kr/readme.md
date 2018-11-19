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

## What are "launch modes"?
TODO

## What is `AAPT2`?
AAPT2 (Android Asset Packaging Tool)는 Android Studio 및 Android Gradle Plugin이 앱 리소스를 컴파일하고 패키지하는 데 사용하는 빌드 도구입니다. AAPT2는 안드로이드 플랫폼에 최적화 된 바이너리 형식으로 리소스를 파싱, 색인화 및 컴파일합니다.
