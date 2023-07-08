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