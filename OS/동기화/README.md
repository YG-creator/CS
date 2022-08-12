# 동기 vs 비동기



## 동기

* 내가 빨래, 설거지 , 청소하기	- 언제끝나는지 바로앎

* 메소드 실행 -> 바로 값 반환 

  

## 비동기

* 업체에게 맡겨서 빨래,설거지, 청소하기 - 언제끝나는지 모름
* task를 위임해서 바로 반환값이 안나옴



# Critical Section



## 개념

동일한 자원을 동시에 접근하는 작업을 실행하는 코드 영역



## 조건

- Mutual Exclusion(상호 배제)
  프로세스 P1 이 Critical Section 에서 실행중이라면, 다른 프로세스들은 그들이 가진 Critical Section 에서 실행될 수 없다.

- Progress(진행)
  Critical Section 에서 실행중인 프로세스가 없고, 별도의 동작이 없는 프로세스들만 Critical Section 진입 후보로서 참여될 수 있다.

- Bounded Waiting(한정된 대기)
  P1 가 Critical Section 에 진입 신청 후 부터 받아들여질 때가지, 다른 프로세스들이 Critical Section 에 진입하는 횟수는 제한이 있어야 한다.

  

## 방법

### Mutex Lock

* 동시접근 방지위해서 

  사용 -> Lock 획득-> 빠져 나오기 -> Lock 방출

* 다중 처리기 환경에서는 비효율적



### Semaphores

- 소프트웨어상에서 Critical Section 문제를 해결하기 위한 동기화 도구

- 종류

  - Counting Semaphore

    **가용한 개수를 가진 자원** 에 대한 접근 제어용으로 사용되며, 세마포는 그 가용한 **자원의 개수** 로 초기화 된다. 자원을 사용하면 세마포가 감소, 방출하면 세마포가 증가 한다.

  - Binary Semaphore

    MUTEX 라고도 부르며, 상호배제의 (Mutual Exclusion)의 머릿글자를 따서 만들어졌다. 이름 그대로 0 과 1 사이의 값만 가능하며, 다중 프로세스들 사이의 Critical Section 문제를 해결하기 위해 사용한다.

- 문제점

  - Busy Waiting(바쁜 대기)
  
    Spin lock이라고 불리는 Semaphore 초기 버전에서 Critical Section 에 진입해야하는 프로세스는 진입 코드를 계속 반복 실행해야 하며, CPU 시간을 낭비했었다. 이를 Busy Waiting이라고 부르며 특수한 상황이 아니면 비효율적이다. 일반적으로는 Semaphore에서 Critical Section에 진입을 시도했지만 실패한 프로세스에 대해 Block시킨 뒤, Critical Section에 자리가 날 때 다시 깨우는 방식을 사용한다. 이 경우 Busy waiting으로 인한 시간낭비 문제가 해결된다.
  
  - Deadlock
  
    세마포가 Ready Queue 를 가지고 있고, 둘 이상의 프로세스가 Critical Section 진입을 무한정 기다리고 있고, Critical Section 에서 실행되는 프로세스는 진입 대기 중인 프로세스가 실행되야만 빠져나올 수 있는 상황을 지칭한다.
  

### 모니터

- 고급 언어의 설계 구조물로서, 개발자의 코드를 상호배제 하게끔 만든 추상화된 데이터 형태이다.
- 공유자원에 접근하기 위한 키 획득과 자원 사용 후 해제를 모두 처리한다. (세마포어는 직접 키 해제와 공유자원 접근 처리가 필요하다. )