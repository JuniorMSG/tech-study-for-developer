# JVM 메모리 구조에 대하여 

## JVM(Java Virtual Machine) 이란 무엇인가?
    Java 는 OS에 종속적이지 않다는 특징을 가지고 있다. 
    OS에 종속받지 않고 실행되기 위해선 OS 위에서 Java 를 실행시킬 무언가가 필요하다. 그게 바로 JVM이다
    바 애플리케이션을 클래스 로더를 통해 읽어 자바 API와 함께 실행하는 것입니다. 메모리 관리(GC)을 수행하며 스택기반의 가상머신입니다.

## JVM 구조

### Class Loader
    JVM내로 클래스를 로드하고, 링크를 통해 배치하는 작업을 수행하는 모듈
### Exection engine
    인터프리터: 바이트 코드를 실행시키는 역할
    JIT 컴파일러: 인터피르터 효율을 높이기 위한 컴파일러로 인터프리터가 반복되는 코드를 발견하면 JIT 컴파일러가 반복되는 코드를 네이티브 코드로 바꿔줍니다. 그 다음부터 인터프리터는 네이티브 코드로 컴파일된 코드를 바로 사용합니다.
    GC(Garbage Collector): 가비지 컬렉터로 힙 영역에서 사용되지 않는 객체들을 제거하는 작업을 의미합니다.

### Runtime Data Area
    프로그램 실행 중에 사용되는 다양한 영역입니다.
* PC Register: Thread가 시작될 때 생성되며 현재 수행 중인 JVM 명령의 주소를 갖고 있습니다.  
* Stack Area: 지역 변수, 파라미터 등이 생성되는 영역. 실제 객체는 Heap에 할당되고 해당 레퍼런스만 Stack에 저장됩니다.  
* Method Area: 클래스 멤버 변수, 메소드 정보, Type 정보, Constant Pool, static, final 변수 등이 생성됩니다. 
  * 상수 풀(Constant Pool)은 모든 Symbolic Reference를 포함하고 있습니다.
* Heap Area: 동적으로 생성된 오브젝트와 배열이 저장되는 곳으로 GC의 대상 영역입니다..
  
### JNI
    자바 애플리케이션에서 C, C++, 어셈블리어로 작성된 함수를 사용할 수 있는 방법을 제공해줍니다. 
    Native 키워드를 사용하여 메서드를 호출합니다. 대표적인 메서드는 Thread의 currentThread()입니다.
### Native Method Library
    Native Method Library: C, C++로 작성된 라이브러리 입니다


## Java의 실행방식
    자바 컴파일러(javac)가 자바 소스코드(.java)를 읽어 자바 바이트코드(.class)로 변환시킵니다.
    Class Loader를 통해 class 파일들을 JVM으로 로딩합니다.
    로딩된 class파일들은 Execution engine을 통해 해석됩니다.
    해석된 바이트코드는 Runtime Data Areas 에 배치되어 실질적인 수행이 이루어집니다