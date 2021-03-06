### CPU의 구조와 기능

1. CPU의 기능

   1) 명령어 인출 : 기억장치로부터 명령어 읽어옴

   2) 명령어 해독 : 수행해야 할 동작을 경정하기 위해 명령어 해독

   3) 데이터 인출 : 명령어 실행을 위해 데이터가 필요한 경우, 기억장치 혹은 I/O 장치로부터 데이터 읽어옴

   4) 데이터 처리 : 데이터에 대한 산술적 혹은 논리적 연산 수행

   5) 데이터 쓰기 : 수행 결과 저장

2. CPU의 기본 구조

   1) 산술논리연산장치(ALU)

   2) 레지스터 세트

   3) 제어 유닛

3. CPU의 내부 구성요소

   1)ALU

    - 각종 산술 연산들과 논리 연산들을 수행하는 회로들로 이루어진 하드웨어 모듈
    - 산술연산, 논리 연산

   2) 레지스터

    - 엑세스 속도가 가장 빠른 기억장치
    - CPU 내부에 포함할 수 있는 레지스터들의 수가 제한됨(특수 목적용 레지스터들과 적은 수의 일반 목적용)

   3) 제어 유닛

    - 프로그램 코드를 해석하고, 그것을 실행하기 위한 제어 신호들을 순차적으로 발생하는 하드웨어 모듈

   4) CPU 내부버스

    - ALU와 레지스터들 간의 데이터 이동을 위한 데이터 선들과 제어 유닛으로부터 발생되는 제어신호 선들로 구성된 내부 버스
    - 외부의 시스템버스들과는 직접 연결되지 않으며, 반드시 버퍼 레지스터들 혹은 시스템 버스 인터페이스 회로를 통하여 시스템 버스와 접속

#### 명령어 실행

1. 명령어 사이클

- 명령어 사이클 

  : CPU가 한개의 명령어를 실행하는 데 필요한 전체 처리과정으로서, CPU가 프로그램 실행을 시작한 순간부터 전원을 끄거나 회복 불가능한 오류가 발생하여 중단될 때까지 반복

- 인출 사이클

  : 인출 사이클의 마이크로 연산

  : 첫번째 주기 -> 현재의 PC 내용을 CPU 내부 버스를 통하여 MAR로 전송

  두번째 주기 -> 그 주소가 지정하는 기억장치 위치로부터 읽혀진 명령어가 데이터 버스를 통하여 MBR로 적재			되며, PC의 내용에 1을 더한다(1단위)

  세번째 주기 -> MBR에 있는 명령어 코드가 명령어 레지스터인 IR로 이동

  ex) CPU 클록 = 1GHz(10^9)(클럭 주기 = 1ns) -> 인출 사이클 : 1ns x 3 = 3ns(나노 세컨즈) 소요

- 실행 사이클

  : CPU는 실행 사이클 동안에 명령어 코드를 해독하고, 그 결과에 따라 필요한 연산들을 수행

  : CPU가 수행하는 연산들의 종류 -> 데이터 이동/처리/저장/프로그램 제어

- 인터럽트 사이클

  : 프로그램 실행 중에 CPU의 현재 처리 순서를 중단시키고 다른 동작을 수행하도록 하는 시스템 동작

  : 외부로부터 인터럽트 요구가 들어오면, CPU는 원래의 프로그램 수행을 중단하고, 요구된 인터럽트를 위한 서 비스 프로그램(ISR: Interrupt Service Routine)을 먼저 수행한다.

  ex) 프린터기 용지 부족

  : 인터럽트 처리과정

  ​	1) CPU는 어떤장치가 인터럽트를 요구했는지 확인하고, 해당 ISR을 호출

  ​	2) 서비스가 종료된 다음에는 중단되었던 원래 프로그램의 수행 계속

  : 세부 동작

  ​	1) 현재 명령어 실행을 끝낸 즉시, 다음에 실행할 명령어의 주소를 스택에 저장(일반적으로 스택은 주기억	장치의 특정 부분)

  ​	2) ISR을 호출하기 위해 그 루틴의 시작 주소를 PC에 적재. 이 때 시작 주소는 인터럽트느 ㄴ요구한 장치로	부터 전송되거나 미리 정해진 값으로 결정

- 다중 인터럽트

  : 인터럽트의 우선 순위를 정하고, 우선 순위가 낮은 인터럽트가 처리되고 있는 동안에 우선순위가 더 높은 인터럽트가 들어오면 현재의 인터럽트 서비스 루틴의 수행으 ㄹ중단하고 새로운 인터럽트 처리

- 간접 사이클

  : C언어에서의 pointer



#### 명령어 파이프라이닝

: CPU의 프로그램 처리 속도를 높이기 위하여 CPU 내부 하드웨어를 여러 단계로 나누어 동시에 처리하는 기술

1. 2단계 명령어 파이프라인

   : 인출단계와 실행단계라는 두 개의 독립적인 파이프라인 모듈로 분리

   : 두 단계들에 동일한 클록을 가하여 동작시간을 일치

    - 첫번째 클록 주기에서는 인출단계가 첫번째 명령어를 인출
    - 두번째 클록 주기에서는 인출된 첫번쨰 명령어가 실행단계로 보내져 실행되며, 그와 동시에 인출 단계는 두번째 명령어 인출

   : 명령어 처리속도가 두 배 향상

   : 두 단계의 처리시간이 동일하지 않으면 두 배의 속도 향상을 얻지 못함

   : 해결책 -> 파이프라인 단계수 늘리면 전체적으로 속도 향상

2. 파이프라인의 효율 저하 요인들

   1) IF 단계와 OF 단계가 동시에 기억장치를 액세스하는 경우에 기억장치 충돌이 일어나면 지연 발생

   2) 조건 분기 명령어가 실행되면, 미리 인출하여 처리하던 명령어들이 무효화됨



- 데이터 해저드

  : 데이터 해저드는 파이프라인의 서로 다른 단계에서 수정이 필요한 데이터들끼리 의존성이 존재할 때 발생한다. 잠재적인 데이터 해저드를 무시하게 되면 경쟁조건이 발생할 수 있다. 

  : 데이터 해저드가 발생할 가능성이 있는 상황

  ​	--> read after write(RAW) (참의존성. 발생할 가능성 높음), write after read(WAR), write after write(WAW)
  - RAW

    -두개의 명령 i1과 i2가 있을 때, 프로그램의 순서상 i1이 i2보다 앞에 있다고 가정

    -i1이 어떤 값을 저장하기 전에 i2가 그 값을 읽으려고 시도

    -이전 명령이 완전히 파이프라인을 통해서 처리되지 않았기 때문에 이후 명령이 그 값을 사용할 수 없는 경우에 발생

  - 데이터 헤저드 해결 방법

    1)  RAW : 참 종속

    ​	-참 종속성을 가지므로 원천적으로 해결하지 못함

    ​	-파이프라인에 NOP(no operation)을 끼워넣는 방법 사용

    ​	-명령어 재배치(컴파일러가 할 일)

    2) WAR, WAW

    ​	-Register renaming(레지스터 이름 바꿔줌)

    ​		: 하드웨어적 방법이나 컴파일러가 바꿔줌

    ​		: 여분의 레지스터가 있어야 함. 즉, 레지스터가 많이 필요

- 구조적 해저드

  : 구조적 해저드는 동시에 두 개 이상의 명령이 프로세서의 하드웨어 중 한 부분을 사용하려고 할 때 발생.

   일반적인 예는 단일 메모리 장치에 대해 하나는 명령을 인출하려고 시도하고, 다른 하나는 데이터를 인출(또는 저장)하려고 하는 두 가지 단계가 동시에 일어나는 경우에 발생

  - 해결 방법

    1) 명령어 인출과 데이터 인출 동시에 발생 	

    ​	: 메모리 장치 분리하거나 분리 캐시 사용(명령어 캐시와 데이터 캐시)

    ​	: 메모리 자체 분리(하버드 아키텍쳐)

    ​	: 파이프라인에 버블 끼워넣기

    2) CPU내의 장치에서 충돌이 생기는 경우

    ​	: 추가적으로 장치를 여러개 둠. 예를 들어, ALU를 2~3개 두는 방법

- 제어 해저드(분기 해저드)

  : 분기가 발생할 때 일어남. 많은 명령 파이프라인 마이크로구조에서 프로세서는 파이프라인에 새로운 명령이 들어갈 때 (일반적으로 명령 인출단계에서) 분기가 발생할지를 알 필요가 있지만 실제로는 분기의 결과 알 수 없음.



#### 슈퍼스칼라

​	: CPU의 처리 속도를 더욱 높이기 위해 내부에 두개 혹은 그 이상의 명령어 파이프라인들을 포함시킨 구조

​	: 매 클록주기마다 각 명령어 파이프라인이 별도의 명령어를 인출하여 동시에 실행할 수 있기 때문에, 이론적	으로는 프로그램 처리속도가 파이프라인의 수만큼 향상 가능

​	: 파이프라인의 수 = m : m-way 슈퍼스칼라



