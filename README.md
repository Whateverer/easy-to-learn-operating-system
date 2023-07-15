# easy-to-learn-operating-system
인프런 그림으로 쉽게 배우는 운영체제 정리

# 운영체제 들어가기
## 운영체제 개요
컴퓨터에 운영체제가 없어도 동작하는가?
- 동작한다. 하지만 처음 설계한 기능대로만 동작할 뿐 기능을 더 추가할 수 없다.
### 운영체제가 하는 일
1. 프로세스 관리 
2. 메모리 관리 -
모든 프로그램은 메모리 위에서 동작
3. 하드웨어 관리 - 
운영체제는 사용자의 하드웨어에 대한 직접적인 접근을 막는다.
4. 파일 시스템 관리 -
하드디스크에 많은 파일들의 효율적인 저장과 관리를 한다.

## 운영체제의 역사
### 운영체제 역사
- 1940년대 - 애니악 발명, 어떻게하면 CPU를 최대한 효율적으로 사용할 수 있을까?
- 1950년대 초 - 진공관과 전선으로 만들어진 논리회로를 아주 작은 크기로 만든 직접 회로(IC) 개발
- 1950년대 중후반 - 컴퓨터가 여러 개의 요청을 한 번에 해결 (싱글스트림 배치시스템) -> CPU 사용성 높아짐
- 1960년도 - 싱글스트림 배치시스템의 한계 극복 -> 프로그램을 순서대로 하나씩 실행하는 것이 아니라 메모리에 여러 프로그램을 올려놓고 시간을 나누어서 빠르게 돌아가면서 실행 (시분할 시스템), UNIX(멀티 프로그래밍, 다중 사용자, 파일시스템 구현)
- 1960년도의 문제 - 1. 메모리 침범 이슈 2. 어느 메모리 위치에서 실행되는지 모름
- 1970년도 이후 - 개인용 컴퓨터의 시대

## 운영체제의 구조
### 운영체제의 구조
운영체제의 핵심은 커널
### 커널
- 프로세스와 메모리, 저장장치를 관리하는 핵심적인 기능 담당.
- 사용자는 운영체제의 커널에 직접 접근할 수 없고 인터페이스를 통해 접근 가능
- 어플리케이션은 시스템 콜을 통해 커널에 접근 가능
- 커널은 사용자로부터 자신을 보호하기 위한 시스템 콜이라는 인터페이스를 가지고 있다.
- 하드웨어와 커널의 인터페이스는 드라이버를 사용 (하드웨어 제조사에서 드라이브를 만들어 제공)
### 인터페이스
- GUI(Graphic User Interface): 그래픽으로 된 인터페이스   
- CLI(Command-line Interface): 텍스트를 이용해 커널과 상호작용

## 컴퓨터 하드웨어와 구조
### 컴퓨터 하드웨어와 구조
#### 폰 노이만 구조
- 오늘날 대부분의 컴퓨터는 프로그램 내장 방식의 폰 노이만 구조를 하고 있다.
- 예전에는 에니악과 같이 하드웨어로 프로그램을 만들어서 프로그램이 달라질 때마다 매번 스위치와 배선을 다시 조정해야 했음
- 이를 해결하기 위해 폰 노이만은 CPU와 메모리를 두고 이들 사이를 버스(데이터를 전달하는 통로)로 연결
### 컴퓨터 하드웨어
메인보드 - 다른 하드웨어를 연결하는 장치, 장치 간에 데이터를 전송하는 건 메인보드의 버스가 담당한다. 폰 노이만 구조라 CPU와 메모리가 필수
### CPU 구조
CPU(Central Processing Unit) 중앙처리장치 
- 산술논리 연산장치: 실제로 데이터 연산 담당
- 제어 장치: 모든 장치들의 동작을 지시하고 제어하는 장치
- 레지스터: CPU내에서 계산을 위해 임시로 보관하는 장치(변수라고 생각하면 됨)
### 메모리 종류
- RAM(Random Access Memory): 랜덤으로 데이터를 읽어도 저장된 위치와 상관없이 읽는 속도가 같다. 전력이 끊기면 데이터를 잃어버리기 때문에 메인 메모리로 사용됨
- ROM(Read Only Memory): 전력이 끊겨도 데이터를 계속 보관할 수 있지만 데이터를 한 번 쓰면 수정이 불가능, 컴퓨터의 부팅과 관련된 바이오스를 저장하는 데에 주로 쓰임

## 컴퓨터의 부팅과정
### 부팅과정
1. 컴퓨터의 전원을 누르면 ROM에 저장된 바이오스가 실행됨
2. 바이오스는 전원, CPU, 메모리, 키보드, 마우스, 하드디스크 등 주요 하드웨어에 이상이 없는지를 체크
3. 만약 주요장치에 이상이 있다면 오류음을 내면서 부팅이 이뤄지지 않고 이상이 없다면 하드디스크에 있는 마스터 부트 레코드에 저장된 부트로더를 메모리로 가져와서 실행한다.
4. 운영체제를 불러온다. (만약 운영체제가 여러개라면 어느 것을 실행할지 선택하는 화면이 나옴)
5. 이제부터 실행되는 모든 응용 프로그램은 메모리에 올라가서 운영체제가 관리한다.

## 인터럽트
### 인터럽트
CPU가 입출력장치에 데이터를 읽거나 쓰는 상황
CPU는 입출력 작업이 들어오면 입출력 관리자에게 입출력 명령을 내린다.
CPU입장에서는 입출력 작업이 언제 끝날지 알 수 없기 때문에 주기적으로 확인해준다. 
- 이러한 방식을 폴링(Polling) 방식이라고 한다.
폴링 방식의 단점은 주기적으로 CPU가 확인해줘야 하니 성능이 좋지 않다.
#### 인터럽트
- 인터럽트는 폴링 방식의 단점을 해결한 방식이다.
- CPU가 입출력 관리자에게 입출력 명령을 내리고 자기는 다른 작업을 계속한다. 입출력 관리자는 입출력이 완료됐을 때 CPU에게 신호를 주고 CPU는 그 신호를 받아 인터럽트 서비스 루틴(ISR)을 실행시켜 작업을 완료한다.
- 인터럽트 서비스 루틴: 특정 인터럽트가 들어오면 그 인터럽트를 처리하는 함수
- 인터럽트는 비동기적으로 동작하기 때문에 성능에 이점이 있다.
- 인터럽트는 하드웨어 방식과 소프트웨어 방식 두 가지가 있다.
  - 하드웨어 방식: 입출력 등과 같은 인터럽트가 있다.
  - 소프트웨어 방식: 사용자 프로그램에서 발생한 인터럽트 ex) 유효하지 않은 메모리에 접근, 0으로 나누는 명령어

## 프로그램과 프로세스
### 프로그램과 프로세스
#### 프로그램
- 하드디스크 등과 같은 저장장치에 저장된 명령문의 집합체. 
- 애플리케이션, Windows 운영체제에서는 .exe의 모습을 하고 있다.
- 프로그램은 컴퓨터 입장에서 하드디스크(저장 장치)만 사용하는 수동적인 존재.
#### 프로세스
- 프로세스 == 실행중인 프로그램. 
- 실행중인 프로그램은 하드디스크에 저장된 프로그램이 메모리에 올라갔을 때 (RAM) 실행중인 프로그램, 즉 프로세스라고 부른다.
- 프로세스는 메모리도 사용, 운영체제의 CPU 스케줄링 알고리즘에 따라 CPU도 사용, 필요에 따라 입출력을 하기 때문에 능동적인 존재.
#### 프로세스의 구성요소
- Code 영역: 자신을 실행하는 코드가 저장되어 있음
- Data 영역: 전역 변수와 static 변수가 저장되어 있음
- Heap 영역: 프로그래머가 동적으로 메모리를 할당하는 데 쓰임, C언어에서 malloc() - 힙 영역에 메모리 공간을 할당, free() - 할당된 메모리 공간 해제
- Stack 영역: 지역 변수와 함수 호출을 했을 때 필요한 정보들이 저장됨
#### 우리가 만든 코드가 메모리에 올라가 프로세스가 되는 과정
예제는 C언어로 진행된다.
1. C언어는 컴파일 언어이기 때문에 먼저 컴파일을 한다.
- 컴파일 과정
  - 전처리기를 거쳐 매크로로 정읳나 숫자를 치환하고 필요한 파일을 불러온다.
  - 전처리기를 거치면 파일의 확장자는 .i가 된다.
  - 컴파일러가 컴파일을 해준다.
  - 컴파일을 마치면 고수준인 C언어를 저수준인 어셈블리어로 바꿔준다.
  - 컴파일러를 거치면 파일의 확장자는 .s가 된다.
  - 어셈블러가 어셈블리어를 기계어로 바꿔진다.
  - 이제 파일은 0과 1로 이루어진 기계어로 구성되고 파일의 확장자는 .o가 된다.
  - 마지막으로 링커가 링킹을 한다. 여러가지 라이브러리나 다른 소스코드를 링킹한다.
  - 링킹을 거치면 우리의 파일의 확장자는 .exe로 변환이 된다.
2. .exe 파일을 더블클릭 하게되면 하드디스크에 있는 우리의 파일이 메모리에 올라가게 되고 이렇게 올라간 프로그램은 프로세스라는 새로운 이름으로 불리게 된다.
3. 이 프로세스는 이제부터 운영체제에 의해 관리된다.
4. CPU 관점에서 코드를 실행한다.
- CPU 관점
  - CPU내의 제어장치가 C언어의 변수를 메모리에 저장시킨다.
  - 이 메모리에 저장된 값을 edx, eax 레지스터로 가져온다.
  - 제어 장치가 레지스터에 저장된 변수의 값을 더하라는 명령을 한다.
  - 산술논리 연산장치가 변수를 더하고 그 결과를 eax 레지스터에 저장한다.
  - 다시 제어장치가 eax에 저장된 결과 값을 가져와서 메모리에 저장시킨다.

## 멀티 프로그래밍과 멀티 프로세싱
### 유니프로그래밍, 멀티 프로그래밍, 멀티 프로세싱
#### 유니프로그래밍
메모리에 오직 하나의 프로세스가 올라온 것을 말한다.
#### 멀티프로그래밍
메모리에 여러 개의 프로세스가 올라온 것을 말한다.
#### 멀티프로세싱
유니프로그래밍과 멀티프로그래밍은 메모리의 관점으로 정의했다면, 멀티프로세싱은 CPU 관점으로 정의한 것이다.
멀티프로세싱은 CPU가 여러 개의 프로세스를 처리하는 것을 말한다. 

- 오늘 날의 OS는 멀티프로그래밍과 멀티프로세싱 두 개가 공존한다.
- 메모리에는 여러 개의 프로그램이 올라오는 멀티프로그래밍이 있고 시분할 처리로 CPU가 각각의 프로세스를 짧은 시간 동안 교대로 실행하는 멀티 프로세싱이 있다.
- 과거에는 메모리의 크기가 작아서 멀티프로그래밍이 불가능했다. 
  - 이 때는 유니프로그래밍을 하면서 멀티프로세싱을 했다.

#### 스와핑
메모리에 있는 데이터를 다른 저장장치로 보내고 다른 저장장치에서 메모리로 올리는 것

## PCB
### PCB(Process Control Block)
프로그램이 메모리에 올라가서 실행중인 상태를 프로세스라고 한다.
프로세스가 만들어지면 운영체제는 해당 프로세스의 정보를 가지고 있는 PCB를 만들고 저장한다.
PCB들은 연결리스트라는 자료구조로 저장된다. 
운영체제는 프로세스가 종료되면 연결리스트에서 해당 PCB를 제거한다.
#### 연결리스트
연결리스트는 각각의 데이터가 다음 데이터를 연결하는 구조로 되어있는 자료구조
#### PCB의 구조
- 포인터: 부모와 자식 프로세스에 대한 포인터, 할당된 자원에 대한 포인터, 프로세스의 한 상태에서 다른 상태로 전환될 때 저장하는 포인터를 가지고 있다.
- 프로세스 상태: 현재 프로세스의 5가지 상태(생성, 준비, 실행, 대기, 완료)를 나타냄
- 프로세스 ID: 프로세스를 식별하기 위한 숫자
- 프로그램 카운터: 다음에 실행될 명령어의 주소를 포함하는 프로그램 카운터를 저장, CPU가 시분할로 처리되어 중간에 다른 프로세스가 실행될 수 있어 어디까지 진행했는지를 기억해야 함.
- 레지스터 정보: 프로세스가 실행될 때 사용했던 레지스터가 저장, 프로그램 카운터와 마찬가지로 CPU를 뺏기고 다시 시작할 때 이전에 사용하던 값을 복구하기 위한 용도
- 메모리 관련 정보: 프로세스가 메모리에 있는 위치 정보, 메모리 침범을 막기 위한 경계 레지스터값 등이 저장
- CPU 스케줄링 정보: CPU 스케줄링에 필요한 우선순위, 최종 실행시간, CPU 점유시간 등이 저장

## 프로세스 상태
사용자가 프로그램을 실행시키면 메모리에 올라가면서 프로세스가 실행된다.
운영체제에는 동시에 수많은 프로세스가 실행중이다.
시분할 시스템을 사용하는 운영체제는 여러 개의 프로세스를 돌아가면서 실행한다.
CPU가 여러 개의 프로세스를 동시에 실행하는 것이 아니라 한 순간에는 한 프로세스만 실행 가능하지만, 속도가 너무 빨라 동시에 실행되는 것 처럼 보인다.
### 프로세스 상태
프로세스는 시분할 처리를 위한 다섯가지 상태를 가지고 있다.
- 생성(New): PCB를 생성하고 메모리에 프로그램 적재를 요청한 상태. 메모리에 프로그램 적재를 승인받으면 준비상태로 넘어감.
- 준비(Ready): CPU를 사용하기 위해 기다리는 상태. CPU스케줄러에 의해 CPU가 할당된다.
- 대기(Waiting): 프로세스가 입출력 요청을 하면 입출력이 완료될 때까지 기다리는 상태. 입출력 요청을 한 프로세스는 대기상태로 두고 다른 프로세스에게 CPU를 할당한다.
- 실행(Running): 준비상태에 있는 프로세스가 CPU스케줄러에 의해 CPU를 할당받아 실행되는 상태. 실행상태에 있는 프로세스의 수는 CPU의 개수만큼이다. CPU스케줄러가 CPU할당을 뺏으면 다시 준비상태로 돌아간다.
- 완료(Terminated): 프로세스가 종료된 상태. 프로세스가 사용했던 데이터를 메모리에서 제거하고 생성된 PCB도 제거한다.

## 컨텍스트 스위칭
### 컨텍스트 스위칭
- 프로세스를 실행하는 중에 다른 프로세스를 실행하기 위해 실행중인 프로세스의 상태를 저장하고 다른 프로세스의 상태값으로 교체하는 작업
- 컨텍스트 스위칭이 일어날 때 PCB의 내용이 변경된다.
- 실행중인 프로세스의 작업 내용을 PCB에 저장하고 실행될 기존 프로세스의 PCB의 내용대로 CPU가 다시 세팅된다.
- 컨텍스트 스위칭이 일어날 때 PCB에 변경하는 값들로는 프로세스 상태, 다음 실행할 명령어의 주소를 담고있는 프로그램 카운터, 각종 레지스터 값 등이 있다.
#### 프로세스 두 개가 컨텍스트 스위칭을 하는 상황
1. 프로세스 A가 실행을 하는데 CPU 점유 시간을 초과함.
2. 운영체제는 프로세스 A가 CPU를 너무 오래 사용했다고 판단하고 인터럽트를 발생시킴.
3. 프로세스 A는 하던 일을 멈추고 현재 CPU의 레지스터 값을 PCB에 저장한다.
4. 프로세스 B의 PCB에 있는 프로세스 정보로 CPU의 레지스터 값을 설정한다.
5. 프로세스 B의 명령어를 실행
6. 점유 시간이 다 되면 다시 인터럽트를 발생시켜 프로세스 B의 상태를 PCB B에 저장
7. 다시 프로세스 A를 실행
#### 컨텍스트 스위칭이 발생하는 이유
- CPU 점유 시간이 다 되었을 때
- I/O 요청이 있을 때
- 다른 종류의 인터럽트가 있을 때

## 프로세스 생성과 종료
### 프로세스 생성과 종료
#### 일반적인 프로세스 생성 과정
1. .exe 파일을 더블클릭으로 실행
2. 운영체제는 해당 프로그램의 코드 영역과 데이터 영역을 메모리에 로드하고 빈 스택과 빈 힙을 만들어 공간을 확보
3. 이 프로세스를 관리하기 위한 PCB를 만들어서 값을 초기화한다.

위의 프로세스 생성은 운영체제가 부팅되고 0번 프로세스가 생성될 때 딱 한번만 실행된다. 나머지 모든 프로세스는 새로 생성하지 않고 0번 프로세스를 복사해서 사용한다.
복사는 fork() 함수를 이용한다.  
=> 이유: 새로 생성하는 것보다 복사를 하는게 더 빠르기 때문

- 0번 프로세스를 복사하여 생성된 프로세스를 자식 프로세스라고 한다.
- 자식 프로세스 입장에서 0번 프로세스는 부모 프로세스가 된다.
- 자식 프로세스는 부모 프로세스의 코드영역, 데이터영역, 힙영역, 스택영역을 모두 복사한다.

자신이 원하는 프로세스는 exec() 함수를 이용하여 부모를 복사한 자식 프로세스의 코드와 데이터 영역을 원하는 값으로 덮어쓰게 된다.
이 때부터 자식 프로세스는 부모 프로세스와 완전히 다르게 동작한다.
exit() 함수는 자식 프로세스가 부모 프로세스에게 작업의 종료를 알리는 역할을 한다.

## 쓰레드
운영체제가 작업을 처리하는 단위는 프로세스이다.
사용자가 운영체제에게 작업을 맡기면 그만큼 프로세스가 늘어난다.
프로세스가 생성되면 PCB가 생성되고 메모리에 코드, 데이터, 스택, 힙영역을 만들어줘야 한다.
프로세스의 수가 많아지면 프로세스의 수만큼 PCB, 코드, 데이터, 스택, 힙 영역도 만들어줘야하기 때문에 너무 무거워진다.
그래서 개발자들은 쓰레드를 고안해냈다.
### 쓰레드
- 쓰레드는 프로세스 내에 존재하는 것으로 하나의 프로세스 내에 한 개 이상 있을 수 있다.
- 한 프로세스 내에 쓰레드들은 그 프로세스의 PCB, 코드, 데이터, 힙영역을 공유한다.
- 스택은 공유하지 않고 쓰레드마다 하나씩 가지고 있다.
- 쓰레드를 관리하기 위해 ID도 부여하고, Thread Control Block(TCB)도 생긴다.
- 운영체제 관점에서 쓰레드도 구분이 가능.
- 운영체제가 작업을 처리하는 단위는 프로세스 내의 쓰레드이다.

구글의 Chrome은 각 탭마다 프로세스가 생성된다.
Firefox는 4개의 프로세스만 생성되고 그 이후는 쓰레드로 만든다.
#### 프로세스와 쓰레드의 장단점
- 안정성 
  - 프로세스는 서로 독립적이기 때문에 하나의 프로세스가 문제가 있어도 다른 프로세스가 영향받지 않는다.
  - 반면 쓰레드는 하나의 프로세스 내에 존재하기 때문에 해당 프로세스에 문제가 생기면 그 안의 모든 쓰레드에 문제가 생긴다.
  - 안정성은 프로세스 방식 > 쓰레드 방식
- 속도와 자원
  - 각각의 프로세스는 서로 고유한 자원을 가진다. 프로세스 간 통신을 하려면 IPC 통신을 이용해야 해서 오버헤드가 크고 속도가 느리다.
  - 반면 쓰레드는 한 프로세스 내에서 스택 영역을 제외한 영역을 모두 공유하기 때문에 오버헤드가 굉장히 작다. 쓰레드 간의 통신은 데이터를 공유할 수 있으니 쉽지만 공유되는 공간에서 문제 발생 가능성 있다.

# CPU 스케줄링
## CPU 스케줄링 개요
### CPU 스케줄링 개요
#### 컴퓨터의 자원
- 필수장치 : CPU, 메모리
- 주변장치 : 하드디스크, 키보드 마우스 등

프로그램을 실행시키면 메모리에 프로세스가 생성되고 각 프로세스에는 1개 이상의 스레드가 있다.
프로세스는 CPU를 차지하기 위해 운영체제의 명령을 기다린다.
#### CPU 스케줄링
운영체제가 모든 프로세스에게 CPU를 할당, 해제하는 것

CPU 스케줄링에서 스케줄러(운영체제)가 고려해야 할 것은 두 가지
1. 어떤 프로세스에게 CPU 리소스를 줘야 하는가?
2. CPU를 할당받은 프로세스가 얼마의 시간동안 CPU를 사용해야 하는가?
오늘날은 시분할처리 방식으로 프로세스마다 돌아가면서 CPU를 차지한다.
- CPU Burst : CPU를 할당받아 실행하는 작업
- I/O Burst : 입출력 작업

## 다중큐
### 다중큐
#### 프로세스의 상태
생성, 준비, 실행, 대기, 완료
여기서 프로세스가 대기하는 준비상태와 대기상태는 큐라는 자료구조로 관리된다.
#### 큐
마트 계산대에 줄을 서는 것 같이 먼저 온 사람이 먼저 처리를 받고 나중에 온 사람은 나중에 처리는 받는 구조
#### 준비,대기 상태의 프로세스 과정
- 프로세스가 실행상태에서 준비상태로 돌아갈 때 운영체제는 해당 프로세스의 우선순위를 보고 그에 맞는 준비 큐에 넣는다.
- CPU 스케줄러는 "준비상태의 다중큐"에 들어있는 프로세스들 중에 적당한 프로세스를 선택해서 실행상태로 전환시킨다.
- 프로세스가 실행상태에서 I/O 작업 요청을받아 대기상태로 오면 I/O 작업 종류에 따라 분리된 큐에 들어가게 된다.
- 큐에는 프로세스의 정보를 가지고 있는 PCB가 들어간다.
#### 정리
- 프로세스 정보를 담고있는 PCB는 준비상태의 다중큐에 들어가서 실행되기를 기다린다.
- CPU 스케줄러에 의해 실행상태로 전환된다.
- 이때 CPU 스케줄러는 준비상태의 다중큐를 참조해서 어떤 프로세스를 실행시킬지 결정한다.

## 스케줄링 목표
### 스케줄링 목표
1. 리소스 사용률 : CPU 또는 I/O 디바이스의 사용률을 높이는 것
2. 오버헤드 최소화 : 스케줄링을 하기 위한 계산이 너무 복잡하거나 컨텍스트 스위칭을 너무 자주하면 오버헤드 발생
3. 공평성 : 모든 프로세스에게 공평하게 CPU가 할당되어야 한다. (공평의 의미는 시스템에 따라 달라질 수 있다.)
4. 처리량 : 같은 시간 내에 더 많이 처리할 수 있는 것을 목표로 함
5. 대기시간 : 작업을 요청하고 실제 작업이 이루어지기 전까지의 대기시간이 짧은 것을 목표로 함.
6. 응답시간 : 사용자의 요청에 얼마나 빨리 응답하는지가 중요

이 모든 목표들을 모두 최선으로 유지하기는 힘들다.
처리량을 높이기 위해서는 하나의 프로세스에 CPU를 오래 할당해야 한다. 반면 응답시간을 줄이기 위해서는 여러 프로세스에 골고루 CPU를 할당해야 한다.
위 목표의 밸런스를 맞추는 것이 중요하다.

## FIFO
### FIFO(First In First Out)
- 먼저 들어온 작업이 먼저 나간다.
- 스케줄링 큐에 들어온 순서대로 CPU를 할당받는 방식으로 먼저 들어온 프로세스가 완전히 끝나야만 다음 프로세스가 실행될 수 있다.
- ex) 마트의 계산대
- 장점 : 단순하고 직관적
- 단점 : 
  - 실행시간이 짧고 늦게 도착한 프로세스가 실행시간이 길고 빨리 도착한 프로세스의 작업을 기다려야 한다.
  - I/O 작업이 있다면 CPU는 I/O 작업을 기다려야 하기 때문에 CPU 사용률이 떨어진다.
#### 스케줄링의 성능은 평균 대기시간으로 평가한다.
#### 평균 대기 시간
평균 대기 시간은 프로세스 여러 개가 실행될 때 프로세스들 모두가 실행되기까지의 대기시간의 평균을 말한다.

FIFO 알고리즘은 프로세스의 Burst Time에 따라 성능의 차이가 심하게 나기 때문에 현대 운영체제에서 잘 쓰이지 않고 일괄처리 시스템에 쓰인다.

## SJF
### SJF(Shortest Job First)
짧은 프로세스 먼저
#### Fisrt In First Out (FIFO)
- Burst Time이 짦은게 먼저 실행되면 평균 대기 시간이 짧아 진다.
- Burst Time이 긴게 먼저 실행되면 평균 대기 시간이 길어 진다!
#### SJF(Shortest Job First)의 문제
1. 어떤 프로세스가 얼마나 실행될지 예측하기 힘들다.
2. Burst Time이 긴 프로세스는 아주 오랫동안 실행되지 않을수도 있다.

=> 이러한 문제점 때문에 SJF는 사용되지 않는다.

## RR
### RR(Round Robin)
FIFO - 일괄처리 시스템에 적합해서 시분할 처리 시스템에서 사용하기 힘들다.

SJF - 프로세스의 종료시간을 예측하기 힘들다.

- FIFO 알고리즘을 보완
- 일정 시간동안 한 프로세스에게 CPU를 할당하고 그 시간이 지나면 강제로 다른 프로세스에게 일정시간만큼 CPU를 할당
강제로 CPU를 뺏긴 프로세스는 큐의 가장 뒷부분으로 밀려난다.
- 이 알고리즘을 RR이라고 부른다.
#### 타임 슬라이스
프로세스에게 할당하는 일정 시간
#### RR의 성능
FIFO와 RR의 평균 대기 시간이 비슷하다면 RR 알고리즘이 더 비효율적인 방식이다. 컨텍스트 스위칭이 있어 그 시간이 추가되기 때문.
#### 최적의 타임 슬라이스를 결정하는 방법
- 사용자가 느끼기에 여러 프로세스가 버벅이지 않고 동시에 실행되는 것처럼 느껴지면서 오버헤드가 너무 크지 않는 값을 찾는 것
- windows는 타임 슬라이스가 20ms, Unix는 100ms로 굉장히 짧다.

## MLFQ
### MLFQ(Multi Level Feedback Queue)
- 가장 일반적으로 쓰이는 CPU 스케줄링 기법
- Round Robin의 업그레이드 된 버전
#### 프로세스 P1, P2로 나누는 예제
- 프로세스 P1 - CPU Bound Process(대부분의 시간을 CPU 연산을 함) - CPU 사용률, 처리량을 중요시
- 프로세스 P2 - I/O Bound Process(대부분의 시간을 I/O 작업으로 보내고 CPU 연산은 조금) - 응답속도를 중요시
- 타임 슬라이스를 적게 잡을 때 P2가 I/O 작업을 기다리는 경우가 없다. => 타임 슬라이스가 작은 경우가 더 좋다.
#### MLFQ의 동작방식
- MLFQ는 기본적으로는 CPU 사용률가 I/O 사용률이 좋게 나오는 작은 크기의 타임 슬라이스를 선택한다.
- 그리고 P1과 같은 CPU Bound Process들에게는 타임 슬라이스를 크게 준다.
- CPU Bound Process인지, I/O Bound Process인지 구분하는 방법
  - CPU를 사용하는 프로세스가 CPU를 사용하다가 스스로 CPU를 반납하면 CPU 사용이 적은거니 I/O Bound Process일 확률이 높다.
  - 반면 CPU를 사용하는 프로세스가 타임 슬라이스 크기를 오버해서 CPU 스케줄러에 의해 강제로 CPU를 뺏기는 상황이면 CPU 사용이 많은 것이니 CPU Bound Process일 확률이 높다.
- 우선순위가 높을수록 타임 슬라이스 크기가 작아지고 우선순위가 낮을수록 타임 슬라이스 크기가 커진다.

# 프로세스 동기화
## 프로세스 간 통신
### 프로세스 간 통신
프로세스는 독립적으로 실행되기도 하지만 프로세스 간에 데이터를 주고받으며 통신을 하는 경우도 있다.
통신은 한 컴퓨터 내의 프로세스와 할 수 있고, 네트워크와 연결되어 있는 다른 프로세스와 할 수도 있다.
1. 한 컴퓨터 내에서 통신하는 방법
- 파일 : 통신을 하려는 프로세스들이 하나의 파일을 이용해 읽고 쓰는 방법 
- 파이프 : 운영체제가 생성한 파이프를 이용해 데이터를 읽고 쓰는 방법
2. 쓰레드를 이용한 방법
- 한 프로세스 내에서 쓰레드 간 통신을 하는 방법
- 쓰레드는 코드, 데이터, 힙 영역을 공유하고 스택만 자기것을 가지고 있음
- 데이터와 힙 영역을 이용하면 프로세스 내에서 쓰레드 간 통신이 가능하다.
3. 네트워크를 이용하는 방법
- 소켓 : 운영체제가 제공
- RPC : 다른 컴퓨터에 있는 함수를 호출하는 RPC(원격 프로시저 호출)를 이용해 통신하는 방법

## 공유자원과 임계구역
### 공유자원과 임계구역
#### 공유자원
- 프로세스가 통신을 할 때 공동으로 이용하는 변수나 파일들이 있는데 이런 것들을 공유자원이라 한다.
- 공유자원은 여러 프로세스들이 공유하고 있기 때문에 각 프로세스의 접근에 따라 결과가 달라질 수 있다.
- 또한 컨텍스트 스위칭으로 시분할 처리를 하기 때문에 어떤 프로세스가 먼저 시작되고 나중에 시작되는지 알 수 없다.
#### 동기화 문제
- 공유하는 자원을 여러 프로세스가 동시에 사용할 때 데이터에 발생하는 문제
#### 임계구역
- 동기화 문제로 여러 프로세스가 동시에 사용하면 안되는 구역을 정의했는데, 이를 임계구역이라고 한다.
- 공유자원을 서로 사용하기 위해 경쟁하는 것은 경쟁조건이라고 한다.
### 상호배제
임계구역 문제를 해결하기 위해서는 상호배제의 매커니즘이 필요하다.
#### 상호 배제의 요구사항
1. 임계영역에는 동시에 하나의 프로세스만 접근한다.
2. 여러 요청에도 하나의 프로세스의 접근만 허용한다.
3. 임계구역에 들어간 프로세스는 빠르게 나와야 한다.

## 세마포어
### 세마포어
#### 상호배제 매커니즘 (동기화에서 가장 중요한 개념)
직원(프로세스)들이 프린터(공유자원)를 쓰기 위해 대기한다.
열쇠관리자(운영체제)는 프린터(공유자원)를 관리하기 위해 열쇠(세마포어)를 이용한다.
 
- 세마포어는 정수형 변수
- 세마포어를 이용하면 공유자원에 동시에 접근하지 못하기 때문에 동기화 문제가 발생하지 않는다.
- 세마포어는 여러 개의 열쇠를 가질 수 있다.
- 단점 : wait 함수와 signal 함수의 순서를 이상하게 호출해 세마포어를 잘못 사용할 가능성이 있다.

## 모니터
### 모니터
- 모니터는 세마포어의 단점을 해결한 상호배제 매커니즘
- 따로 운영체제가 처리하는 것이 아니라 프로그래밍 언어에서 지원하는 방법
#### Java에서의 모니터 예시코드
```java
public class Health{
    private int health = 100;

  synchronized void increase(int amount) {
    health += amount;
  }

  synchronized void decrease(int amount) {
    health -= amount;
  }
}
```
- Java에서 "synchronized" 키워드가 붙으면 이 키워드가 붙은 함수들은 동시에 여러 곳에서 실행시킬 수 없다.
- 상호배제가 완벽하게 이루어진다.
- 만약 한 프로세스에서 increase() 함수가 실행되면 다른 프로세스에서는 increase()는 물론 "synchronized"가 붙은 decrease()도 실행할 수 없다.
- 모니터의 구현만 완벽하다면 프로그래머는 세마포어처럼 wait()이나 signal()을 임계영역에 감싸지 않아도 되어 편리하고 안전하게 코드를 작성할 수 있다.

# 데드락
## 데드락이란?(feat.식사하는 철학자)
### 교착상태(데드락)
여러 프로세스가 서로 다른 프로세스의 작업이 끝나기를 기다리다가 아무도 작업을 진행하지 못하는 상태
- 교착상태가 발생하는 이유는 공유자원 때문
- 만약 어떤 자원을 여러 개의 프로세스가 공유하지 않는다면 교착상태는 발생하지 않는다.
### 교착상태의 필요조건
이 중 한가지라도 충족하지 않는다면 교착상태는 발생하지 않는다.
1. 상호배제 - 어떤 프로세스가 한 리소스를 점유했다면 그 리소스는 다른 프로세스에게 공유되면 안된다.
2. 비선점 - 프로세스 A가 리소스를 점유하고 있는데 프로세스 B가 리소스를 빼앗을 수 없어야 한다.
3. 점유와 대기 - 어떤 프로세스가 리소스 A를 가지고 있는 상태에서 리소스 B를 원해야 한다.
4. 원형 대기 - 점유와 대기를 하는 프로세스들의 관계가 원형을 이루고 있는 것

## 데드락 해결(feat.은행원 알고리즘)
### 교착상태 해결
### 교착상태 회피
프로세스들에게 자원을 할당할 때 어느정도 자원을 할당해야 교착상태가 발생하는지 파악해서 교착상태가 발생하지 않는 수준의 자원 할당을 한다.
- 전체 자원의 수와 할당된 자원의 수를 기준으로 안정상태(Safe state)와 불안정상태(Unsafe state)로 나눈다.
- 운영체제는 최대한 안정상태를 유지하려고 자원을 할당한다.
- 불안정상태라고 해서 무조건 교착상태가 아니라 교착상태에 빠질 위험이 크다는 것을 의미한다.
#### 은행원 알고리즘
- 은행이 대출해준다는 상식적인 알고리즘
- 운영체제는 프로세스들에게 자원을 할당해주기 전에 자기가 가지고 있는 자원의 수를 알고있어야 함(시스템의 총 자원)
- 프로세스들은 각자 자기가 필요한 자원의 최대 숫자를 운영체제에게 알려줘야 한다.(최대 요구자원)
- 안정상태
  - 한 프로세스의 요청이 예상되는 자원이 현재 사용 가능한 자원보다 크다면 해당 프로세스의 요청을 거부하고 다른 프로세스부터 실행
- 불안정상태 
  - 현재 사용 가능한 자원이 모든 프로세스의 요청이 예상되는 자원보다 작을 때 발생
#### 교착상태를 검출
1. 가벼운 교착상태 검출 - 타이머를 이용하는 방식, 프로세스가 일정 시간동안 작업을 진행하지 않는다면 교착상태가 발생했다고 가정하고 교착상태를 해결
- 교착상태를 해결하는 방법 : 일정 시점마다 체크포인트를 만들어 작업을 저장하고 타임아웃으로 교착상태가 발생했다면 마지막으로 저장한 체크포인트로 롤백
2. 무거운 교착상태 검출 - 자원할당 그래프를 이용하는 방식, 현재 운영체제에서 프로세스가 어떤 자원을 사용하는지 지켜보고 교착상태가 발생했다면 해결한다.
- 순환구조의 그래프를 가지고 있을 때 교착상태 발생 - 교착상태를 일으킨 프로세스를 강제종료 시킨 후 다시 실행시킬 때 체크포인트로 롤백
- 운영체제가 지속적으로 자원할당 그래프를 유지하고 검사해야하기 때문에 오버헤드가 발생한다.

## 컴파일과 프로세스
### 컴파일과 프로세스
우리가 프로그래밍 언어로 만든 코드가 어떻게 프로세스가 되고 메모리에 할당되는지 알아보기

#### 컴파일 언어
- 개발자가 코드를 작성하고 컴파일이라는 과정을 거쳐서 0과 1로된 기계어로 실행파일을 만든다.
- 컴파일 과정에서 개발자가 문법 오류를 일으켰는지 검사하고 CPU가 처리가능한 기계어로 실행파일을 만들어놓기 떄문에 속도가 빠르다.
- C, C++, C# 등
#### 인터프리터 언어
- 개발자가 작성한 코드를 미리 기계어로 만들지 않고 실행 시 코드를 한 줄 씩 해석해 실행하는 언어
- 미리 검사를 하지 않기 때문에 실행 시 오류가 날 수 있고 속도도 컴파일 언어와 비교하면 느리다.
- JS, Python, Ruby 등, Javascript v8엔진이라는 구글 크롬에서 사용하는 인터프리터

프로세스는 코드영역, 데이터영역, 스택, 힙영역으로 나뉜다.
#### 컴파일 과정
1. 개발자가 코드 작성, test.c라는 파일로 저장
2. 전처리기가 test.c파일을 훑어보고 전처리 구문을 처리한다.
3. 컴파일러는 test.i 파일을 기계어에 가까운 어셈블리어로 바꾼다.
4. test.s 파일을 어셈블러를 통해 object파일로 변환
5. object파일은 링커를 통해 실행파일로 변환
6. 운영체제는 exe파일에 있는 코드영역과 데이터영역을 가져와 프로세스의 코드영역과 데이터영역에 넣어주고 빈 상태의 스택과 힙을 할당한다.
7. PCB를 만들어 관리가 가능하도록 만들고 프로그램 카운터(다음 실행할 명령어의 주소)를 생성한 프로세스의 코드영역의 첫번째 주소로 설정한다.
8. 그러면 운영체제의 CPU 스케줄링에 따라서 프로세스가 실행되다가 작업을 마친다.

## 중간정리
폰 노이만 구조의 필수장치는 CPU와 메모리
컴퓨터가 부팅되면 보조장치인 하드디스크에 저장되어있는 운영체제가 메모리에 올라오게 되고 모든 프로그램은 운영체제에 의해서 관리된다.

# 메모리
## 메모리 종류
### 메모리 종류
컴퓨터에는 여러 종류의 메모리가 있다.
아래로 갈수록 속도가 느려지고 용량이 커지고 가격이 싸진다.
- 레지스터: 가장 빠른 기억장소로 CPU내에 존재, 휘발성 메모리, 32bit, 64bit는 레지스터의 크기
- 캐시: 휘발성 메모리, 메인메모리에 있는 데이터를 레지스터로 옮기려면 한참 걸리기 때문에 필요한 데이터를 미리 가져온다. 이 미리 가져온 데이터를 저장하는 곳이 캐시다. L1캐시를 먼저 보고, L2캐시에도 없다면 메인메모리를 확인한다.
- 메인메모리(RAM): 실제 운영체제와 다른 프로세스들이 올라가는 공간, 전원이 공급되지 않으면 데이터가 지워지기 때문에 휘발성 메모리다. 데이터를 저장하기보다는 실행중인 프로세스만 올린다.
- 보조저장장치(HDD, SSD): 컴퓨터에는 작업한 파일을 저장할 필요가 있다. 전원이 공급되지 않아도 데이터가 지워지지 않는 비휘발성 메모리

CPU는 계산을 할 때 메인메모리에 있는 값을 레지스터로 가져와 계산한다. 계산 결과는 다시 메인 메모리에 저장시킨다.

## 메모리와 주소
### 메모리와 주소
운영체제는 메모리를 관리하기 위해서 1바이트 크기로 구역을 나누고 숫자를 매긴다. 이 숫자를 주소라고 부른다.
### 32bit CPU와 64bit CPU
- 32bit CPU는 레지스터 크기가 32bit이고 CPU가 처리하는 ALU(산술논리연산장치)도 데이터가 이동하는 버스도 32bit이다.
- 64bit CPU는 레지스터 크기가 64bit이고 CPU가 처리하는 ALU(산술논리연산장치)도 데이터가 이동하는 버스도 64bit이다.
### 물리주소와 논리주소
- 메모리를 컴퓨터에 연결하면 0x0번지부터 시작하는 주소가 있는데 이를 물리 주소 공간이라고 한다.
- 이와 다르게 사용자 관점에서 바라본 주소 공간은 논리 주소 공간이라고 한다.
- 메모리에는 운영체제와 수많은 프로세스가 올라온다. 운영체제는 특별하기 때문에 운영체제를 위한 공간을 따로 마련해둔다.
- 운영체제와 사용자 프로세스 공간을 나누는 경계 레지스터를 만들었다.
- 경계 레지스터는 CPU 내에 존재하는 레지스터로 메모리 관리자가 사용자 프로세스가 경계 레지스터의 값을 벗어났는지 검사하고 벗어났다면 그 프로세스를 종료시킨다.
### 절대주소와 상대주소
메모리에는 절대주소와 상대주소라는 개념이 있다.
- 개발자는 프로그램을 만들때 프로그램이 실행될 주소를 신경쓰지 않고 개발한다.
- 이는 컴파일러가 컴파일을 할 때 메모리 0x0번지에서 실행한다고 가정하기 때문이다.
- 컴파일러가 0x0번지라고 가정하고 프로그램을 만들었고 이는 상대 주소(논리 주소)이다.
- 실제 메모리에 올라간 주소는 0x4000번지인데 이는 메모리 관리자가 바라본 절대 주소(물리 주소)이다.

1. 사용자가 0x100번지(상대주소, 논리주소)에 있는 데이터를 요청한다.
2. CPU는 메모리 관리자에게 0x100번지에 있는 데이터를 가져오라고 한다. 
3. 메모리 관리자는 CPU가 요청한 0x100번지의 값과 재배치 레지스터에 있는 0x4100번지(절대주소, 물리주소)에 접근해서 데이터를 가져온다. 
4. 재배치 레지스터에는 프로그램의 시작 주소가 적혀있다. 
5. 메모리 관리자는 사용자가 메모리에 접근할 때마다 이렇게 계산한다.

메모리 관리자 덕분에 모든 사용자 프로세스는 0x0번지부터 시작한다는 가정으로 편리하게 프로그램을 만들 수 있다.

## 메모리 할당방식
### 메모리 할당방식
메모리 오버레이 - 큰 프로그램을 메모리 크기만큼 잘라서 올리고 나머지는 하드디스크의 스왑영역에 저장하는 방법
오늘날과 같이 멀티 프로그래밍 환경에서는 메모리 관리를 어떻게 할까?
1. 가변 분할 방식 -
프로세스의 크기에 따라 메모리를 나누는 방식
2. 고정 분할 방식 -
프로세스의 크기와 상관 없이 메모리를 할당하는 방식

#### 가변 분할 방식
- 프로세스의 크기에 따라 메모리를 나눈다. 
- 한 프로세스가 메모리의 연속된 공간에 할당되기 때문에 "연속 메모리 할당"이라고 한다.
- 장점
  - 메모리에 연속된 공간에 할당되기 때문에 더 크게 할당되어 낭비되는 공간인 "내부 단편화"가 없다.
- 단점
  - 외부단편화 발생
#### 고정 분할 방식
- 프로세스의 크기에 상관없이 메모리를 정해진 크기로 나눈다. ex) 2MB씩 분할시킨다. 
- 한 프로세스가 메모리에 분산되어 할당되기 때문에 "비연속 메모리 할당"이라고 한다.
- 장점
  - 구현이 간단하다.
  - 오버헤드가 적다.
- 단점
  - 작은 프로세스도 큰 영역에 할당되어 공간이 낭비되는 "내부 단편화"가 발생

#### 외부단편화
가변 분할 방식 == 세그멘테이션
- 프로세스의 크기만큼 메모리를 할당해주기 때문에 기존의 프로세스들이 사용했던 메모리 크기가 남아 연속된 공간에 프로세스를 할당할 수 없는 경우 발생
- 외부단편화가 발생한 부분을 조각모음하면 해결된다.
- 조각모음은 현재 프로세스를 중단하고 메모리를 이동시켜야 하기 때문에 오버헤드 발생
#### 내부단편화
고정 분할 방식 == 페이징
- 메모리에 서로 다른 크기를 가지고 있는 프로세스가 올라가 있을 때 20MB 단위로 분할 했을 때 그것보다 작은 메모리의 프로세스는 남는 공간을 가지게 된다. 이를 내부단편화라고 한다
- 이를 해결하는 방법은 없고 분할되는 크기를 조절해 내부단편화를 최소화한다.
#### 버디 시스템
- 가변 분할 방식과 고정 분할 방식을 혼합해 단점을 최소화 한 시스템
- 2의 승수로 메모리를 분할해 메모리를 할당하는 방식
- 메모리가 500Byte일 때, 2의 승수인 512바이트까지 분할해서 메모리에 올린다.
- 장점
  - 가변 분할 방식처럼 프로세스 크기에 따라 할당되는 메모리 크기가 달라지고 외부단편화를 방지하기 위해 메모리 공간을 확보하는 것이 간단하다.
  - 고정 분할 방식처럼 내부 단편화가 발생하기는 하지만 많은 공간의 낭비가 발생하지 않는다.

# 가상메모리 개요
## 가상메모리
### 가상메모리
컴퓨터마다 실제 메모리 크기는 다르다. 만약 운영체제나 프로세스가 4GB 메모리에서 동작하도록 만들어졌다면 이보다 작은 메모리를 가진 컴퓨터에서는 실행되지 않는다.
가상메모리는 이를 완벽히 해결했다.
- 프로세스는 메모리 관리자를 통해 메모리에 접근한다.
- 메모리 관리자는 프로세스의 요청이 있으면 그에 맞는 물리메모리로 연결시켜준다.
- 가상메모리의 크기는 이론적으로는 무한대이지만 실제로는 물리메모리와 CPU의 비트 수로 결정된다.
- 만약 32bit CPU인 경우 2^32 = 4GB의 메모리 용량을 가지고 있다.
- 4GB 메모리일 경우 그보다 큰 메모리의 프로세스를 올리려면 하드디스크 내 스왑영역에 저장 후, 물리메모리에 가져와 스왑해 실행시키는 방식으로 처리한다.
#### 동적 주소 변환
- 메모리 관리자는 물리메모리와 하드디스크 내 스왑영역을 합쳐서 프로세스가 사용하는 가상주소를 물리주소로 변환하는데 이것을 동적 주소 변환이라고 한다.
- 동적 주소 변환을 거치면 프로세스는 마음대로 사용자 데이터를 물리 메모리에 배치할 수 있다.

#### 가상메모리
가상메모리 시스템에서 가상주소는 메모리나 스왑영역 한 곳 중에 위치한다.
메모리 관리자는 가상주소와 물리주소를 일대일 매핑테이블로 관리한다.

## 세그멘테이션(배치정책)
### 세그멘테이션
가변 분할 방식을 이용하는 세그멘테이션
- 세그멘테이션에서 프로그램은 함수나 모듈 등으로 세그먼트를 구성한다.
- 프로그램(사용자) 입장에서 메모리를 살펴보면 메인 코드가 있는 세그먼트, 전역 데이터들이 있는 세그먼트, 힙 영역이 있는 세그먼트, 스택 영역이 있는 세그먼트 등이 있다.
- 프로세스 입장에서는 코드영역, 데이터 영역, 힙 영역, 스택 영역을 서로 인접한 것처럼 바라본다.
- 사용자, 프로세스, CPU가 바라보는 주소는 논리주소이다.
- 실제 물리주소로 변환은 중간에서 메모리 관리자가 해준다.
#### 세그멘테이션의 주소 변환
- 메모리 관리자는 세그멘테이션 테이블이라는 것을 가지고 있다.
- 세그멘테이션 테이블에는 Base Address와 Bound Address 정보가 저장되고 이걸 이용해 물리 메모리 주소를 계산한다.

#### 변환 과정
1. CPU에서 논리주소를 전달해준다.
2. 메모리 관리자는 이 논리주소가 몇 번 세그먼트인지 알아낸다.
3. 메모리 관리자 내에 Segment Table Base Register를 이용해서 물리 메모리 내에 있는 세그멘테이션 테이블을 찾고 세그먼트 번호를 인덱스로 Base Address와 Bound Address를 찾는다.
4. 운영체제는 컨텍스트 스위칭을 할 때마다 메모리 관리자 내에 Segment Table Base Register를 해당 프로세스의 것으로 값을 바꿔준다.
5. Bound Address는 세그먼트의 크기를 나타낸다. 메모리 관리자는 CPU에게서 받은 논리주소와 Bound Address의 크기를 비교한다.
6. 만약 논리주소가 Bound Address보다 작다면 논리주소와 Bound Address를 더해 물리주소를 구하고, 논리주소가 Bound Address보다 크다면 메모리를 침범했다고 가정하고 에러를 발생시킨다.

#### 세그멘테이션의 장단점
- 장점
  - 메모리를 가변적으로 분할할 수 있다.
  - 코드 영역, 데이터 영역, 스택 영역, 힙 영역을 모듈로 처리할 수 있어 공유와 각 영역에 대한 메모리 접근 보호가 편리하다.
- 단점
  - 가변 분할 방식의 단점인 "외부 단편화"가 발생한다.
 
## 페이징(배치정책)
### 페이징
고정 분할 방식을 이용하는 페이징
- 세그멘테이션은 외부단편화가 있기 때문에 이를 해결하기 위해 고안되었다.
- 페이징은 메모리를 할당할 때 정해진 크기의 페이지로 나눈다.
- 모든 페이지는 크기가 같기 때문에 관리가 쉬워진다.
- 논리주소공간 : 사용자와 프로세스가 바라보는 주소공간
- 물리주소공간 : 실제 메모리에서 사용되는 주소공간
- 논리주소공간(페이지), 물리주소공간(프레임) 모두 동일한 크기로 나누어진다.
#### 페이징의 주소 변환
- 메모리 관리자는 페이지 테이블을 가지고 있다.

#### 변환 과정
1. CPU에서 논리주소를 전달해준다.
2. 메모리관리자는 이 논리주소가 몇번 페이지인지, 오프셋은 얼마인지 알아낸다.
3. 메모리관리자 내의 Page Table Base Register를 이용해 물리메모리에 있는 페이지 테이블을 찾아 페이지 번호를 인덱스로 프레임 번호를 알아낸다.
4. 오프셋을 이용해 물리주소로 변환시킨다.
5. 페이지 테이블에 invalid로 표시되어 있으면 스왑영역, 즉 하드디스크에 저장되어있다는 의미.

- 세그멘테이션과 마찬가지로 Page Table Base Register는 운영체제가 컨텍스트 스위칭을 할 때마다 해당 프로세스의 것으로 업데이트 해준다.
- 메모리 관리자 내 페이지 테이블은 1차원 배열로 구성되어 있다. 페이지 번호가 배열의 인덱스가 된다. 해당 인덱스로 가면 프레임을 얻을 수 있다.
- 페이지 넘버 = 논리주소 / 페이지 크기
- 오프셋 = 논리주소 % 페이지 크기

#### 세그멘테이션과 페이징의 차이
여기까지 보면 세그멘테이션과 페이징이 매우 비슷해보인다. 차이는 뭘까?
- 바로 페이지 크기가 다르다.
- 세그멘테이션
  - 세그멘테이션은 프로세스마다 크기가 달라 Bound Address를 가지고 있다.
  - 세그멘테이션은 외부단편화가 발생한다.
  - 세그멘테이션은 논리적인 영역별로 세그먼트를 나눈다. 세그먼트마다 크기를 다르게 나눌 수 있어 코드, 데이터, 힙, 스택영역을 나눌 수 있다.
- 페이징
  - 페이징은 모든 페이지의 크기가 동일해서 크기를 표현하는 Bound Address가 불필요하다.
  - 페이징은 이러한 특징때문에 내부단편화가 발생하지만 외부단편화를 해결하는 것보다 내부단편화를 해결하는게 더 낫다.
  - 페이지의 크기가 고정되어 있어 논리적인 영역별로 나누는 것이 아니라 페이지로 나누기 때문에 논리적인 영역을 나눌 수 없다.
  - 그래서 특정 영역만 딱 떼어내서 공유하거나 권한을 부여하는게 더 어렵다.
  - 페이징에서 가장 신경써야 하는 것은 페이지 테이블의 크기다. 프로세스가 많아질 수록 페이지 테이블도 많아지기 때문에 프로세스가 실제로 사용할 수 있는 메모리 영역이 줄어든다.
  - 실제로 메모리 관리자가 참조하는 페이지 테이블도 물리 메모리의 운영체제 영역에 저장되어있어 페이지 테이블 크기가 너무 크면 사용자 영역이 부족하게 된다.

## 페이지드 세그멘테이션(배치정책)
### 페이지드 세그멘테이션
세그멘테이션과 페이징을 혼합해 장점을 취한 방식
- 세그멘테이션
  - 세그멘테이션은 가변 분할 방식이라서 코드 영역, 데이터 영역, 스택 영역, 힙 영역을 세그먼트로 나눠서 관리할 수 있다.
  - 그래서 다른 프로세스와 공유하기도 편하고 각 영역에 대한 메모리 접근 보호를 하기 쉽다.
- 페이징
  - 페이징은 고정 분할 방식으로 메모리를 효율적으로 관리할 수 있다.
#### 메모리 접근 권한
메모리 접근 권한은 메모리의 특정 번지에 부여된 권한으로 읽기(Read), 쓰기(Write) ,실행(Execute) 세 가지가 있다.
- 프로세스는 코드 영역, 데이터 영역, 스택 영역, 힙 영역 등이 있는데 각 영역마다 접근 권한이 있다.
- 코드 영역은 프로그램 그 자체이므로 수정되면 안되기 때문에 읽기와 실행 권한만 있다.
- 데이터 영역은 일반변수, 전역변수, 상수로 선언한 변수가 저장되기 때문에 읽기 권한이 있고 쓰기 권한인 있거나 없다. 실행권한은 없다.
- 스택과 힙 영역은 읽기, 쓰기 권한이 있고 실행 권한은 없다.
  - CODE : 읽기/실행 권한
  - DATA : 읽기/(쓰기) 권한
  - HEAP : 읽기/쓰기 권한
  - STACK : 읽기/쓰기 권한

메모리 접근 권한에 대한 검사는 가상주소에서 물리주소로 변환될 때마다 일어나는데 만약 권한을 위반하면 에러를 발생시킨다.

#### 페이지드 세그멘테이션
세그멘테이션 기법에서 세그멘테이션 테이블은 Base Address와 Bound Address로 구성된다.
페이징 기법에서 페이지 테이블은 프레임 번호로 구성되어있다.
- 페이지드 세그멘테이션 기법에선 세그멘테이션 테이블에 권한 비트를 추가한다. 그리고 Base Address는 페이지 넘버로 바뀌고 Bound Address는 이 세그먼트의 페이지 개수로 바뀐다.

#### 변환 과정
1. CPU가 0x12300번지 접근 요청
2. 메모리 관리자가 세그먼트 테이블을 보고 분석 후 해당 세그먼트가 메모리 접근 권한을 위반하는지 검사한다.
3. 접근 권한을 위반했으면 프로세스를 종료시키고 위반하지 않으면 페이지 넘버와 페이지 개수를 가져온다.
4. 페이지 넘버로 페이지 테이블에 접근해 프레임 번호를 가져온다.
5. 물리 메모리 내 해당 프레임에 접근해서 그 위치에서 페이지 개수를 더해 물리주소를 구한다.
6. 만약 물리 메모리에 해당 프레임이 없다면 스왑영역에서 물리메모리로 가져온다.

#### 페이지드 세그멘테이션의 장단점
- 물리메모리에 접근하기 위해서 메모리에 접근을 두 번 해야한다. 1) 세그멘테이션 테이블 참조 시 2) 페이지 테이블 참조 시

이런 단점 때문에 현대 운영체제는 페이징과 페이지드 세그멘테이션 기법을 적절히 섞어서 사용한다.

## 디맨드 페이징(가져오기 정책)
### 디맨드 페이징
- 프로세스가 실행될 때 코드 영역, 데이터 영역, 힙 영역, 스택 영역이 모두 메모리에 올라오는 것이 아니라, 필요한 모듈만 올라와서 실행된다.
- 프로그램이 실행될 때 90%의 시간이 10% 코드에서 실행된다.
### 지역성 이론
#### 공간의 지역성
현재 위치와 가까운 데이터에 접근할 확률이 높음
#### 시간의 지역성
최근 접근했던 데이터가 오래 전에 접근했던 데이터보다 접근할 확률이 높음

- goto문은 지역성 이론을 위배하기 때문에 꼭 필요한 상황에서만 사용하는 걸 권요
- 지역성 이론은 조만간 쓰일 데이터만 메모리에 올리고 당분간 필요하지 않을 것 같은 영역은 스왑 영역으로 보내 성능을 향상시킨다.
- 디맨드 페이징은 조만간 필요할 것 같은 데이터를 메모리로 가져오고 쓰이지 않을 것 같은 데이터는 스왑 영역으로 이동시키는 정책이다. (지역성 이론을 구현한 정책)
### 메모리 계층구조
- 메모리는 레지스터, 캐시, 메인 메모리, 보조저장장치로 나뉜다.
- 레지스터: CPU내에 존재하고 CPU의 한 사이클에 접근할 수 있어 굉장히 빠르다.
- 캐시(L1, L2): CPU의 수 사이클에서 수십 사이클에 접근할 수 있다.
- 메인 메모리: 수백 사이클이 걸린다.
- 보조저장장치: 수백만 사이클이 걸려 굉장히 오래 걸린다.

- 디맨드 페이징은 스왑영역을 보조저장장치에 저장하는데 성능향상을 위해선 스왑영역으로 데이터를 이동시키는 것을 최소화시켜야 한다.
- 가상메모리의 크기는 물리 메모리 크기에 스왑 영역을 합친 것이다.
- 스왑인: 스왑영역에서 물리 메모리로 데이터를 가져오는 것
- 스왑아웃: 물리 메모리에서 스왑영역으로 데이터를 보내는 것
#### 페이지 테이블 엔트리
- 페이지 테이블을 이루고있는 한 행을 페이지 테이블 엔트리(PTE)라고 한다.
- 접근비트: 페이지가 메모리에 올라온 후 데이터에 접근이 있었는지 알려주는 비트, 메모리에 읽기나 실행 작업을 했다면 1로 변경됨
- 변경비트: 페이지가 메모리에 올라온 후 데이터의 변경이 있었는지 알려주는 비트, 메모리에 쓰기 작업을 했으면 1로 변경됨
- 유효비트: 페이지가 물리 메모리에 있는지 알려주는 비트, 유효비트가 1이면 페이지가 스왑 영역에 있고, 0이라면 물리 메모리에 있다는 뜻
- 읽기/쓰기/실행 비트: 권한비트로 해당 메모리에 접근 권한이 있는지 검사하는 비트

#### 가상 메모리 주소가 물리 메모리와 스왑 영역에서 참조되는 과정
1. 프로세스가 가상 메모리에 접근 요청을 했을 때 메모리 관리자는 페이지 테이블을 보고 물리 메모리의 프레임을 찾아내는데 만약 물리 메모리에 없다면 Page Fault라는 인터럽트를 발생시킨다.
2. Page Fault가 발생하게 되면 보조저장장치의 스왑영역에 접근하게 되고 해당 프로세스는 대기 상태가 된다.
3. 스왑 영역에 있는 데이터가 메모리로 올라가는 작업을 시작하고 
4. 메모리로 올라갔다면 대기 상태에 있던 프로세스는 다시 실행하게 된다.

## 페이지 교체정책
### 페이지 교체정책
메모리가 꽉 찼을 때 어떤 페이지를 스왑영역으로 보낼지 결정하는 페이지 교체정책

- 프로세스는 데이터 접근을 위해 메모리를 참조하는데 해당 데이터가 메모리에 없으면 Page Fault가 발생한다.
- Page Fault가 발생하면 해당 페이지를 스왑영역에서 메모리로 불러들여야 하는데 메모리가 꽉 차서 공간이 없다면 메모리에 있는 페이지 중에 하나를 선택해서 스왑영역으로 옮겨야 한다.
- 메모리에 있는 페이지를 스왑영역으로 옮길 때 어떤 페이지를 선택할지 결정하는 정책을 페이지 교체정책이라고 한다.
- 페이지 교체정책에는 여러 가지가 있다.
1. Random: 무작위로 선택해서 교체하는 방법 - 거의 사용되지 않는다.
2. FIFO(First In First Out): 가장 먼저 들어온 페이지를 내보내는 것 - 자주 쓰이는 페이지가 가장 먼저 들어왔다는 이유로 스왑아웃될 수 있음
3. Optimum: 앞으로 가장 오랫동안 쓰이지 않을 페이지를 선택하는 방법 - 사실상 구현이 불가능한 이론적인 방법
4. LRU(Least Recent Used): 최근에 가장 사용이 적은 페이지를 선택하는 방법 - 프로그램이 지역성을 띄지 않을 떈 성능이 떨어진다.

#### 페이지 교제정책 알고리즘
- LRU가 성능은 좋지만 구현하려고 할때 시간을 기록해야 하기 때문에 어려움이 있음
- 이를 보완한 알고리즘을 Clock 알고리즘이라고 한다.
#### Clock Algorithm
- 일정 간격마다 모든 페이지의 접근 비트를 0으로 초기화한다.
- 접근 비트의 초기값은 0으로 설정되어 있고, 만약 페이지가 참조되었다면 1로 설정한다.
- 클락 알고리즘은 페이지를 원형으로 연결한다.
- 스왑영역으로 옮길 페이지를 포인터로 가리키는데 이 포인터를 클락 핸드라고 한다. 클락 핸드는 시계 방향으로 돈다.
- 만약 Page Fault가 발생해서 스왑영역으로 보내야 하는 상황이 나오면 클락 핸드는 현재 참조하고 있는 페이지의 접근비트를 본다.
- 만약 해당 접근비트가 1이라면 해당 접근 비트를 0으로 바꾸고 클락핸드가 다음 페이지를 가리킨다.
- 이렇게 반복하다가 접근비트가 0인 페이지를 발견하면 해당 페이지를 스왑영역으로 보낸다.
#### Enhanced Clock Algorithm
향상된 클락 알고리즘
- 이 알고리즘은 접근비트만 이용하는 것이 아니라 변경비트까지 본다.
- 스왑영역으로 보내질 확률이 가장 높은 페이지는 접근 비트가 0이고 변경 비트도 0인 페이지다.
- 그 다음으로 접근비트 0, 변경비트 1인 페이지고, 그 다음으로는 접근비트 1, 변경비트 0인 페이지다.

이렇게 보면 LRU만 이용하고 FIFO는 사용할 일이 없어보인다.
하지만 부득이하게 FIFO를 사용해야 할 수 있다.
LRU에서는 접근비트를 이용하는데 하드웨어적으로 접근비트를 지원하지 않는 시스템에선 FIFO를 이용할 수밖에 없다.
그래서 FIFO의 성능을 높이기 위한 방법을 고안했다.

#### FIFO 성능 개선
- FIFO의 장점은 구현이 간단하지만 단점은 자주 사용되는 페이지가 교체될 수 있다.
- 이를 위해 2차 기회 페이지 교체 알고리즘을 고안했다.
- FIFO 방식에서 자주 사용하는 페이지에게는 또 한번의 기회를 주는 것이다.
- FIFO 방식과 동일하게 동작하지만 만약 Page Fault 없이 페이지 접근에 성공했다면 해당 페이지를 큐의 맨 뒤로 이동시켜 수명을 연장시켜주는 방법이다.
- 이 알고리즘의 성능은 LRU > 2차 기회 페이지 교체 알고리즘 > FIFO 이다.

## 스레싱과 워킹셋
### 스레싱과 워킹셋
CPU 스케줄링의 목표는 CPU 사용률을 높이는 것이다. 
CPU 사용률을 높이기 위해서는 동시에 실행하는 프로세스의 수, 즉 멀티프로그래밍 정도를 올리는 것이다.
멀티프로그래밍 수를 높이게되면 어떤 프로세스가 I/O 작업으로 CPU를 사용할 수 없을 때 다른 프로세스로 컨텍스트 스위칭을 해서 CPU 사용률을 높일 수 있다.
CPU 사용률을 높이기 위해 멀티프로그래밍 정도를 늘렸으면 그 프로세스들이 필요로하는 공간이 있기 때문에 물리메모리에 프레임을 할당해야 한다.
하지만 모든 프로그램을 물리메모리에 올릴 수는 없어 일부는 스왑영역에 저장하게 되는데,
문제는 멀티프로그램밍의 정도가 높아질 때 제한된 물리 메모리에 모든 프로세스를 올려야 하고, 당장 실행되는 프레임을 제외한 나머지 프레임들은 스왑영역에 저장되고 Page Fault가 많이 발생하게 된다.
그러면 CPU가 작업하는 시간보다 스왑작업의 시간이 더 길어지고 CPU 사용률은 떨어지게 된다.
#### 스레싱
CPU 사용률을 높이기 위해 멀티프로그래밍 정도를 올렸지만 그 때문에 오히려 CPU 사용률이 낮아지는 결과를 스레싱이라고 한다.
- 스레싱의 근본적인 원인은 물리 메모리가 부족하기 때문
- 이를 하드웨어적으로 해결하려면 메모리 크기를 늘리면 된다.
- 현재 메모리가 프로세스들이 작업하는데 충분한 크기라서 스레싱이 발생하지 않는다면 물리메모리 크기를 늘려도 별 다른점이 없다.
#### 운영체제가 스레싱을 효과적으로 해결하기 위한 방법
- 한 프로세스가 실행될 때 너무 많은 페이지를 할당하면 다른 프로세스가 사용할 페이지가 줄어들어 효율이 떨어진다.
- 반면 너무 적은 페이지를 할당하면 빈번한 Page Fault가 발생해 스레싱이 발생하게 된다.
- 이를 해결하기 위해 프로세스가 실행되면 일정량의 페이지를 할당하고, 만약 Page Fault가 발생하면 더 많은 페이지를 할당한다.
- 반대로 Page Fault가 너무 적게 발생하면 페이지를 과하게 할당해 메모리가 낭비되는 것이라 판단하고 페이지를 회수한다.
- 이렇게하면 프로세스가 실행되는 동안 해당 프로세스에게 맞는 적절한 페이지 수가 결정된다.
#### 워킹셋
현재 메모리에 올라온 페이지는 다시 사용할 확률이 높기 때문에 하나의 세트로 묶어서 메모리에 올린다. 이를 워킹셋이라고 부른다.
- 워킹셋은 프로세스가 준비상태에서 실행상태가 되는 컨텍스트 스위칭을 할 때 사용된다.
