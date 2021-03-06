### 컴퓨터시스템개요

물리적인 장치인 하드웨어는 기능에 따라 중앙처리장치,기억장치,입력장치로 구성되어있다.

-- 중앙처리장치

cpu는 컴퓨터 시스템 전체를 제어하는 장치로써 입력장치에 입력받은 데이터를 처리한 후 출력장치와

기억장치로 보내는 일련의 과정을 수행한다.

-- 산술논리연산장치

-- 제어장치

-- 기억장치

기억장치는 내부 기억장치와 외부기억장치로 나눌 수 있다. cpu내의 레지스터와 캐시기억장치, 주기억장치는 내부기억장치에 속하고, 보조기억장치는 외부 기억장치에 해당한다.



-- 기억장치의 계층구조

용량										속도

low	cpu 내의 레지스터					    high

​	     캐시기억장치 - static RAM

​	     주기억장치 - Dynamic RAM

high      보조기억장치 - 하드디스크, 플로피 디스크	low



주기억장치(RAM) 중앙처리장치(CPU)

## cpu의 구조와 기능

##### cpu의 기본구조

cpu는 기본적으로 입력된 데이터와 명령어를 프로그램에서 저정한 순서에 따라 수행

이를 프로그램 내장방식이라 부르며, 이름 처음 제안한 **폰노이만**의 이름을따서 폰 노이만 컴퓨터 구조라고 부른다.

데이터와 명령어가 주기억장치인 RAM에 저장되어 있다가 데이터 버스를 통해 cpu로 전달되면, cpu는 전달된 명령어를 이용하여 데이터를 사용자가 원하는 형태로 처리한다. 그 결과는 다시 데이터 버스를 통해서 주기억장치로 보내진다.

######  머신사이클

명령어 인출 -> 명령어 해독 -> 명령어 실행 ->저장 

##### cpu의 내부구조

연산장치,레지스터,제어장치의 집합으로 구성되며, 이들은 내부 cpu버스로 연결되어 있다. 데이터들은 버스를 통해서 전송된다.

**연산장치** - 산술논리연산장치

**프로세서 레지스터와 스택** - 컴퓨터 cpu 내부의 대표적인 저장장치이다. 레지스터는 cpu의 설계에 따라 또는 사용하는 목적에 따라 종류가 다양하다. 이외에 스택이라는 저장장치가 있는데 일반적인 저장장치와 다르게 **주소**를 지정하는 방법과 읽고 쓰는 방법이 간편하다는 특징이 있다.

**스택저장장치**

스택은 cpu 내부의 레지스터 집합에 존재하는 저장장치이다. 데이터가 순차적으로 저장되며, 요소의 개수와 스택의 길이는 가변적이다. 그리고 한번에 하나의 요소에만 액세스 가능하다. 데이터접근 방식은 LIFO의 특징을 갖는다.

데이터가 입력되고 출력되는 액세스 부분을 스택의 TOP

새로운 요소를 추가 저장하는 동작을 PUSH

하나의 요소를 꺼내는 방식으 POP

**제어장치**

제어장치는 주기억장치에 저장된 명령을 순서에 맞게 하나씩 가져와서 해독하고 그 명령이 지시하는 연산이 실행되도록 해당되는 장치에 제어신호를 보낸다.

주기억장치에 자정되어 있는 명령어의 구조는 일반적으로 연산코드필드와 기억장치 주소 번지 필드 등 두개의 필드로 구성되어 있다.

##### cpu의 기능과 동작

명령어 인출 - 주기억장치에 저장되어 있는 명령어를 읽어오는 기능

명령어 해독 - 읽은 명령어에 대하여 수행해야 할 동작을 결정하기 위하여 인출된 명령어를 해독

**CPU의 동작**

CPU는 4단계의 기본구성

1).데이터는 주기억장치 RAM에서 인출되고 외부 시스템 버스를 통해서 레지스터 1번으로 전달

2) 제어장치는 새롭게 저장된 레지스터 1번 데이터와 이전부터 저장하고 있던 레지스터 2번의 데이터를 덧셈하라는 제어신로응 ALU로 전달

3)  ALU에서는 제어신호에 의해서 덧셈을 수행하고 그 결과를 누산기에 저장

4) 계산 결과는 외부 시스템 버스를 통해서 다시 주기억장치로 전달

** 누산기는 데이터 레지스터로 처리 결과를 임시로 보유하는 역할



### 캐시기억장치

캐쉬기억장치는 주기억장치에 저장되어 있는 명령어와 데이터 중의 일부를 임시적으로 복사해서 저장하는 장치로, 데이터를 저장하고 인출하는 속도가 주기억장치보다 빠르다. 그래서 중앙처리장치가 캐시기억장치에 저장된 명령어와 데이터를 처리할 경우, 주기억장치보다 더 빠르게 처리할 수 있다.

**캐쉬기억장치위 원리**

중앙처리장치가 데이터를 처리할 때, 저장장치는 필요한 데이터를 인출하여 제공하거나 처리된 데이터를 저장한다. 하지만 중앙처리장치는 저장장치에 비해서 고속이므로 저장장치가 읽기와 쓰기 동작을 하는 동안 기다려야 한다. 이런 문제를 극복하려면 중앙처리장치의 처리 속도만큼 빠른 저장장치가 필요하다. 이때 고속의 레지스터를 중앙처리장치 내의 저장장치로 사용하여 각종 처리 결과를 저장한다.

캐쉬 기억장치는 5~100ns 정도의 빠른 접근 시간을 제공하는 기억장치로 수행할 명령어나 피연산자를 주기억장장체에서 가져와 저장하고 있다가 빠른 속도로 중앙처리장치에 제공한다.

중앙처리장치 < --------------------- > 주기억장치

​			    캐쉬기억장치

캐쉬기억장치의 실패

중앙처리장치  <- 캐시기억장치 <- 주기억장치

캐쉬기억장치의 성공

중앙처리장치 <- 캐쉬기억장치

캐쉬기억장치는 중앙처리장치가 수행할 명령어와 필요한 정보를 저장하고 있다가 필요할 때 즉시 제공해 신속하게 처리되도록 한다. 이러한 동작은 프로그램 내장형 컴퓨터의 특성인 기억장치 참조의 지역성에 의해 가능하다.

** 참조의 지역성 - 주어진 시간동안 중앙처리장치의 주기억장치 참조는 제한된 영역에서만 이루어지는 현상이다. 장시간 동안에는 물론 주기억장치의 접근위치가 크게 변하지만 짧은 시간동안 중앙처리장치가 접근하는 범위는 지역적으로 제한되는 것을 의미한다.



시작 -> cpu 주소전달 -> 캐쉬 기억장치 내 명령어존재 -> 명령어를 cpu로 전송

​				       캐쉬기억장치 내 명령어 미존재 -> 명령어를 포함한 주기억장치에 접근 -> 주기억장치에서 명령어 블록을 인출 -> 주기억장치의 명령어블록을 캐쉬에 저장 and 명령어 단어를 cpu에 전송

** 적중률이 높을수록 처리속도가 우수하다.

**캐쉬기억장치의 설계**

주기억장치와 캐쉬기억장치는 동시에 동일한 명령이나 데이터를 저장하고 있으므로, 하나의 기억장치에 변경이 일어나면 다른 기억장치에 이를 반영해야만 통일설을 갖는다.

설계고려사항

1) 캐쉬기억장치의 크기

2) 인출 방식

3) 사상 함수

4) 교체 알고리즘

5) 쓰기 정책

6) 블록 크기

7)캐시기억장치의 수

**계층적 캐시기억장치**

온-칩 캐쉬기억장치를 1차캐쉬기억장치로 사용하고 외부에 더 큰 용량의 오프-칩 캐시기억장치를 2차 캐쉬기억장치로 사용한다 

**멀티 프로세서의 캐시기억장치 구조**

시스템 버스에 온-칩 캐시기억장치의 cpu가 여러대 연결된 것이다.



#### 시스템버스

컴퓨터 내부의 회로에서 중앙처리장치와 주기억장치 그리고 외부의 입출력장치 간에 정보를 전송하기 위해 공용으로 사용하는 전기적 통로를 버스라고 한다.

버스는 실질적인 정보 데이터를전달하는 데이터 버스, 각 장치의 주소나 기억장치의 위치를 나타내는 정보들을 위한 주소버스, 수행될 다양한 데이터 전송 동작을 구별하기 위한 제어 버스로 구성된다.



버스 선의 수는 버스가 데이터를 전송할 수 있는 능력으로 버스 폭이라고도 한다.

버스 폭은 한 번에 전송할 수 있는 데이터 비트의 수를 나타낸다.

버스의 대역폭은 버스의 속도를 나타내는 척도다. 단위 시간당 전송할 수 있는 데이터 양을 나타내며, 버스 클록의 주기에 의해 결정된다.



**다중 버스 계층 구조**

**단일 버스 구조**

하나의 시스템 버스에 컴퓨터 구성 장치들이 연결되는 가장 간단한 구조다. 단일버스에서는 장치가 버스에 연결될수록 버스의 사용을 조정하거나 중재하는 시간이 길어져, 전파 지연이 증가한다.

그리고 데이터 전송량이 많아지면 버스 용령을 초과한 병목현상이 나타난다.

**다중 버스 구조**

여러 서버를 사용하는 계층적 구조이다.

주기억장치만 시스템 버스에 단독으로 연결되고 중앙처리장치는 내부의 지역 버스를 이용해서 지역입출력 제어기, 캐시기억장치와 연결된다.또한 확장 버스 인터페이스를 통해서 시스템 버스와 연결된다.

중앙처리장치와 주기억장치간에 데이터를 송신하는 경우와 주변장치와 주기억장치가 직접적으로 데이터를 송신하는 경우에만 시스템 버스를 이용하기 때문에 단일 버스 구조에서 발생했던 주기억장치에 대한 전파지연과 병목현상을 피할 수 있다

 **3계층 다중버스이론**

연결된 주변장치들의 특징을 세분화하여, 시스템 버스와 확장 버스 이외에 고속 버스를 추가한 고성능 계층 버스 구조이다.



**버스중재**

시스템 버스에 연결된 컴퓨터의 기본 장치들을 버스 마스터라고하며, 여러 개의 버스 마스터들이 동시에 시스템 버스의 사용을 요구하는 경우, 버스 경합이 발생된다. 이때 각 버스마스터가 미리 정해진 기준에 따라 순서대로 버스를 사용할 수 있게 해주는 동작을 버스 중재하고 한다. 이러한 버스 중재를 수행하는 하드웨어 모듈을 버스 중재기라고 한다.

버스중재방식의 분류

버스중재기의 위치에 따른 분류

버스 중재에 사용되는 제어신호의 연결 구조에 따른 분류

우선수위 결정 박식에 따른 분류



1) 버스 중재기 위치에 따른 분류

버스 중재기는 버스의 사용요구를 효율적으로 수신할 수 있고, 버스 사용의 승인 신호를 적절하게 전달할 수 있는 곳에 위치해야한다.

중앙집중식 방식

시스템내 한개의 버스 중재기가 존재 여러 마스터들이 생성하는 버스 요구 신호들은 버스 중재기가 단독으로 수신한다.버스 중재기는 미리 정해진 중재 원칙에 따라 선택된 버스 마스터에게 버스를 사용할 수 있는 버스 신호를 전달한다.

분산식 중재 방식

여러 개의 버스 중재기가 존재하는 방식으로 버스 마스터에 각각 별도의 버스 중재기가 있다. 한 버스 중재기에 고장이 발생하여도 해당 버스 마스터에만 영향을 미치므로 신뢰도가 높다. 그러나 고장난 버스 중재기를 찾는 방법이 복잡하고 버스 중재기 하나가 고장나면 전체 시스템에 영향을 미친다.

중앙집중식 고정 우선순위 방식

버스 중재기에서 가장 먼 곳에 위치한 버스 중재기는 우선순위가 가장 낮다, 이 우선순위는 하두웨어적으로 설계되어 변경이 불가하다.

분산식 고정 우선순위 방식

버스에 연결된 버스 마스터가 독립적으로 버스 중재기를 보유하고 있는 구조, 버스 경합 상태에서 버스 사용요청이 발생하면 정해진 우선순위에 따라 버스를 사용하는 방식이다.

폴링방식

폴링방식은 버스 마스터가 버스 사용을 원하고 있는지를  버스 중재기가 주기적으로 검사하여 버스 사용 승인 여부를 결정한다. 이 방식은 버스 요구 신호 선 이외에 별도의 폴링을 위한 폴링 선이 필요하다.



##### 명령어 파이프라인

하나의 명령어가 실행되는 도중에 다른 명령어의 실행을 시작하는 방법으로 동시에 여러 개의 명령어를 실행한다.

이 방법은 이전 명령어를 끝내기 전에 새로운 명령어 수행을 시작하여 명령어 사이클이 같은 시간대에 중첩되어 처리된다.

**2단계 명령어 파이파라인**

명령어를 실행하는 하드웨어를 인출/실행 단계라는 두개의 독립적인 파이프라인 모듈로 분리하여 수행하는 방법이다.

각명령어의 인출/실행 단계의 처리 시간이 동일해야 파이프라인으로 인한 효율 향상을 얻을 수 있다. -> 단계수를 증가시켜 각 단계의 처리 시간을 같게 하는 방법으로 속도향상이 가능하다.



**4단계 명령어 파이프라인**

단계수가 4개로 명령어 인출-해독-오퍼랜드 인출 - 실행 순이다

명령어 인출단계 - 명령어를 기억장치에서 인출하는 과정 기억장치 주소에서 명령어를 인출하여 명령어 레지스터로 이동

명령어 해독단계 - 인출된 명령어를 해독

오퍼랜드 인출단계 - 오퍼랜드는 피연산자 부분으로 연산에 사용될 변수나 데이터가 된다.

실행 - 지정된 연산을 실행

최대 4단계 명령어 단계가 동시에 처리되어 더 많은 중첩처리로 속도가 향상된다.



**6단계 명령어 파이프 라인**

FI - 인출

DI- 해독

CO-오퍼랜드 계산

FO-오퍼랜드 인출

EI-명령어 실행

WO-연산되 결과, 즉 저장



파이프라인에 의한 속도향상

그러나

경우에 따라서 100% 효율적이지 않음

- 오퍼랜드 인출이 필요하지않을경우
- IF/OF 단계가 동시에 기억장치에 접근하는 경우 충돌이 일어나며 지연이 발생
- 조건 분기 명령어가 실행되면, 미리 인출하여 처리하던 명령어들이 무효화된다.

** 조건분기 명렁어는 순차적으로 명령어를 실행하는 것이 아니라 순서에 맞지 않게 다른 순서에 있는 명령어를 수행하게되는 명령어.



Q&A 

) 1. 캐시기억장치의 사상(mapping)에 대하여 정의하시오

-> 캐시기억장치에서의 인출이 실패하면 캐쉬기억장치의 일부분은 주기억장치로 옮기고 주기억장치에서 필요한 정보를 캐시기억장치로 옮기는 정보교환이 mapping이다.

)2. 요구인출 방식의 장단점은?

cpu가 현재 필요한 정보만을 주기억장치에서 블록단위로 인출해 오는 방식이다. 하지만 매번 주기억장치에서 인출을 수행하므로 실패율이 높아져셔 캐시기억장치의 효과를 얻지 못한다.

)3. 단일 버스 구조의 한계점은?

 단일버스에서는 장치가 버스에 연결될수록 버스의 사용을 조정하거나 중재하는 시간이 길어져, 전파 지연이 증가한다. 그리고 데이터 전송량이 많아지면 버스 용령을 초과한 병목현상이 나타난다.

)4. 버스중재의 폴링방식이란?

버스 마스터가 버스 사용을 원하고 있는지를  버스 중재기가 주기적으로 검사하여 버스 사용 승인 여부를 결정한다. 이 방식은 버스 요구 신호 선 이외에 별도의 폴링을 위한 폴링 선이 필요하다.

5) 4단걔 파이프라인의 처리 순서는?

IF->ID->OF->EX