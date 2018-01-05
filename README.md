# ADS04 Android

## 수업 내용

- 안드로이드의 전체적인 그림 학습
- Layout 및 간단한 view들 실습 및 학습 

## Code Review

- 생략

## 보충설명

- 안드로이드 실행환경

![안드로이드 실행환경](https://kairo96.gitbooks.io/android/content/pic1/pic2.png)

- 안드로이드 주요 컴포넌트
![안드로이드컴포넌트](https://kairo96.gitbooks.io/android/content/pic1/pic3.png)

### 안드로이드 주요 컴포넌트

```Java
애플리케이션(APPLICATIONS): 자바로 개발된 애플리케이션이 위치하는 영역이며, 이메일 클라이언트, SMS 프로그램, 달력, 지도, 브라우저, 주소록 등의 애플리케이션이 탑재되어 있다. 또한 우리가 자바로 개발한 애플리케이션이 탑재되는 영역이 바로 여기이다. 애플리케이션 프레임워크(APPLICATION FRAMEWORK): 애플리케이션 프레임워크는 애플리케이션을 개발하기 위해 필요한 각종 API를 제공하는 영역이다. 이 영역에 있는 각종 API를 사용하면 화면에 버튼이나 텍스트 등을 표현하거나 주소록 같은 다른 애플리케이션의 데이터를 사용할 수도 있다. 또한 이미지, 문자열 등의 여러 데이터를 접근하거나 애플리케이션의 생명주기(lifecycle)를 관리하는 API도 이 영역에서 제공한다.
라이브러리(LIBRARIES): 안드로이드에서 사용할 수 있는 다양한 C/C++ 라이브러리를 제공하는 영역이다. 이 영역의 라이브러리는 모두 애플리케이션 프레임워크를 통해 개발자가 사용할 수 있게 하고 있다. BSD(버클리 소프트웨어 배포판)를 기반으로 한 표준 C 시스템 라이브러리가 임베디드 리눅스 기반의 디바이스에 맞게 수정되어 있으며, PacketVideo의 OpenCore를 기반으로 한 미디어 라이브러리는 MPEG4, H.264, MP3, AAC, AMR, JPG, PNG 등의 파일들을 지원한다. 서피스 매니저(surface manager)는 2D, 3D 그래픽를 지원하며, WebKit은 브라우저 기능을 지원한다. 그리고 임베디드용으로 개발된 데이터베이스 엔진인 SQLite(에스큐엘라이트)를 제공하고 있다.
안드로이드 런타임(ANDROID RUNTIME): 안드로이드는 자바 기반으로 동작하지만 JVM(자바 가상 머신, Java Virtual Machine)을 그대로 사용하지 않고 DVM(달빅 가상 머신, Dalvik Virtual Machine)을 사용하고 있다. 그래서 작성된 소스 코드(.java)는 자바 컴파일러에 의해 클래스 파일(.class)로 컴파일되며, 클래스 파일은 DX 컴파일러에 달빅 바이트 코드로 변환되며 달빅 실행파일(.dex, Dalvik Executable)과 최적화된 달빅 실행파일(.odex, Optimized Dalvik Executable)로 저장된다. 이 파일들은 안드로이드 기기에서 실행되기 그리고 달빅은 메모리가 작은 소형 기기에서도 효율적으로 동작할 수 있도록 최적화되어 있다. 참고로 안드로이드 4.4(킷캣) 이전에는 Dalvik 기반이었지만 4.4에서는 ART가 새롭게 도입되었으며 안드로이드 5.0(롤리팝)부터는 ART 기반으로 변경되었다.
리눅스 커널(LINUX KERNEL): 안드로이드는 리눅스 커널 3.0.1(안드로이드 4.0)을 기반으로 하며, 이를 통해 보안, 메모리 관리, 프로세스 관리, 네트워크 스택과 각종 드라이버를 제공한다.
```

### 안드로이드 manifest

모든 애플리케이션에는 루트 디렉터리에 AndroidManifest.xml 파일(정확히 이 이름이어야 함)이 있어야 합니다. 매니페스트 파일에서는 Android 시스템이 앱의 코드를 실행하기 전에 확보해야 하는 앱에 대한 필수 정보를 시스템에 제공합니다.

이외에도 매니페스트 파일은 다음 작업을 수행합니다.

```Java
애플리케이션에 대한 Java 패키지의 이름을 지정합니다. 이 패키지 이름은 애플리케이션에 대한 고유한 식별자 역할을 합니다.
액티비티, 서비스, 브로드캐스트 수신기 및 콘텐츠 제공자 등 애플리케이션을 이루는 구성 요소를 설명합니다. 또한, 각 구성 요소를 구현하는 클래스의 이름을 지정하고 클래스가 처리할 수 있는 해당 기능(예: Intent 메시지)을 게시합니다. 이러한 선언은 Android 시스템에 구성 요소와 구성 요소가 실행될 수 있는 조건을 알립니다.
애플리케이션 구성 요소를 호스팅하는 프로세스를 결정합니다.
애플리케이션이 API의 보호된 부분에 액세스하여 다른 애플리케이션과 상호 작용하는 데 보유해야 하는 권한을 선언합니다. 또한, 다른 애플리케이션이 이 애플리케이션의 구성 요소와 상호작용하기 위해 보유해야 하는 권한도 선언합니다.
애플리케이션이 실행 중일 때 프로파일링과 기타 정보를 제공하는 Instrumentation 클래스를 나열합니다. 이러한 선언은 애플리케이션이 개발 중인 동안에만 매니페스트에 존재하고, 애플리케이션이 게시되기 전에 삭제됩니다.
애플리케이션이 필요로 하는 Android API의 최소 레벨을 선언합니다.
애플리케이션이 연결되어야 하는 라이브러리를 나열합니다.
```

### Context
- 역할
```Java
안드로이드 시스템 서비스에서 제공하는 API 를 호출 할 수 있는 기능
어플리케이션에 관하여 시스템이 관리하고 있는 정보에 접근하기
자신이 어떤 어플리케이션을 나타내고 있는지 알려주는 id 역
ActivityManagerService 에 접근할 수 있도록 하는 통로 역할 
```

### ViewGroup&Layout

![ViewGroup](http://cfile1.uf.tistory.com/image/27212739579842F60C807B)

- 뷰 그룹 아래 SubClass로 Layout클래스가 있음.

- TODO 다양한 레이아웃 찾아서 ▽ 에 정리하기

#### LinearLayout

![LinearLayout](http://cfile8.uf.tistory.com/image/231D1039579842EA1167A1)

- 가장 기본적인 레이아웃
- orientation이라는 속성을 가지고 있어 가로,세로를 설정 가능
- weight 같은 가중치를 주는 속성을 유용하게 사용할 수 있음.
- __TODO 레이아웃별 고유한 기능 넣기__

#### RelativeLayout

![RelativeLayout](http://cfile22.uf.tistory.com/image/26172D39579842F517DF63)

- 상대적인 기준에 따라 배치하는 레이아웃
- __TODO 레이아웃별 고유한 기능 넣기__

#### FrameLayout

![FrameLayout](http://cfile5.uf.tistory.com/image/24147B39579842E9191D80)

- 위젯들을 포개는 방식으로 배치하는 레이아웃
- __TODO 레이아웃별 고유한 기능 넣기__

#### TableLayout

![TabLayout](http://cfile1.uf.tistory.com/image/240C6E39579842F522DEBD)

- 표 형태의 레이아웃
- __TODO 레이아웃별 고유한 기능 넣기__

#### ConstraintLayout

![ConstraintLayout](http://leaks.wanari.com/wp-content/uploads/2016/05/editor-1.png)

- 보이는 대로, 직관적으로 배치할 수 있는 형태의 레이아웃
- __TODO 레이아웃별 고유한 기능 넣기__

### 안드로이드 4대 컴포넌트

![4대 컴포넌트](https://4.bp.blogspot.com/-_1qHjQ5Ltu0/WM0Kw0kVnpI/AAAAAAAABW4/d1uCwYFPHOUThan80Gd5_6cj9yjamaziACEw/s640/components.png)

- 액티비티(Activity) : 화면을 구성하는 가장 기본적인 컴포넌트
- 서비스(Service) : 백그라운드에서 동작하는 컴포넌트
- 컨텐츠 프로바이더(Contents Provider) : 응용 프로그램 간의(앱과 앱) 데이터를 상호 공유하기 위한 컴포넌트
- 브로드캐스트 리시버(Broadcast Receiver) : 단말기에서 발생하는 이벤트 수신을 위한 컴포넌트 (네트워크 상태, 배터리 상태, SMS수신, 스크린 꺼짐.. 등)



#### 출처: http://arabiannight.tistory.com/entry/272 [아라비안나이트]
#### 출처: AndroidDeveloper Site
#### 출처: https://kairo96.gitbooks.io/android/content/ch2.1.html
#### 출처: http://darrenkwon.blogspot.kr/2017/03/4-activity.html

## TODO

- 안드로이드라는 플랫폼의 큰 개념들을 익힌다.
- context라는 개념 확실히 하기
- Layout 많이 다뤄보기
- 안드로이드 4대 컴포넌트 
- manifest가 하는 일 정리

## Retrospect

- 플랫폼 특성상 너무나 많은 내용이 있는 관계로 틈틈히 공식사이트에 가서 문서를 읽어본다.

## Output
![kakaotalk_20170912_230217117](https://user-images.githubusercontent.com/31605792/30330290-a7c92768-980f-11e7-8494-3c870c661c73.jpg)
