# GC란 무엇인가? 
* [01. GC (Garbage Collection이란?) ](#gcgarbage-collection란)



## GC(Garbage Collection)란?
    메모리 관리 기법중 하나로 프로그램이 동적으로 할당했던 메모리영역중에서 필요없게된 영역을 해제하는 기능이다. 
    동적할당된 메모리영역 가운데 어떤변수도 가리키지않는 메모리영역을 탐지하여 자동으로 해제하는 기법이다.

### 장점 
* 프로그래머가 동적으로 할당한 메모리 영역 전체를 완벽하게 관리하지 않아도 된다.
  * 유효하지 않은 Call By Reference 객체 접근 
  * 이중 해제
  * 메모리 누수

### 단점
* 어떤 메모리를 해제해야 할 지 결정하고 사용하느 알고리즘에 의해 비용이 든다.
* 객체가 필요없어지는 시점을 알아도 GC 알고리즘이 언제 해제하는지 시점을 추적해야 하기때문에 비용이 든다.
* GC의 타이밍 및 점유 시간을 사전에 예측하기 어려워 실시간 시스템에는 적합하지 않다. 


## 파이썬 GC
    파이썬에선 기본적으로 garbage collection(가비지 컬렉션)과 reference counting(레퍼런스 카운팅)을 통해 할당 된 메모리를 관리한다. 
    기본적으로 참조 횟수가 0 이된 객체를 메모리에서 해제하는 레퍼런스 카운팅 방식을 사용하지만, 
    참조 횟수가 0 은 아니지만 도달할 수 없는 상태인 reference cycles(순환 참조)가 발생했을 때는 가비지 컬렉션으로 그 상황을 해결한다.

### garbage collection
    The process of freeing memory when it is not used anymore. 
    Python performs garbage collection via reference counting and a cyclic garbage collector that is able to detect 
    and break reference cycles. The garbage collector can be controlled using the gc module.

### reference count
    The number of references to an object. When the reference count of an object drops to zero, it is deallocated. 
    객체의 참조 횟수가 0으로 떨어지면 할당이 해제됩니다. 

    Reference counting is generally not visible to Python code, 
    일반적인 Python 코드에서는 볼 수 없으나 

    but it is a key element of the CPython implementation. The sys module defines a getrefcount() 
    function that programmers can call to return the reference count for a particular object.
    그러나 이것은 CPython 구현의 핵심 요소입니다. sys모듈은 프로그래머가 특정 객체에 대한 참조 카운트를 반환 하기 위해 호출 할 수 있는
    getrefcount() 함수를 정의 합니다.

[뒤로](../README.md) / [위로](#gc란-무엇인가?)