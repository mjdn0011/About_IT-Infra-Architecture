# About_IT-Infra-Architecture

## 인프라란?
* 인프라 = '기반'
  인프라 구조 자체는 복잡하지만, 전문가에 의해 관리되고 있어서 사용자는 그 구조를 이해하지 않고도 간단히 이용할 수 있다는 특징이 있음
* 아키텍처 = '구조'

### 1. 집약형 아키텍처
IT 시스템의 여명기에는 **대형 컴퓨터**를 이용해서 **모든 업무를 처리**하는 형태가 대부분
이런 대형 컴퓨터는 '**범용 장비**', '**호스트**', '**메인 프레임**' 등으로 불림
시스템 아키텍처라는 관점에서는 하나의 컴퓨터로 모든 처리를 하기 때문에 '집약형'이라고 할 수 있음
  * 장점
    - 간단한 구성(한 대의 대형 컴퓨터만 있으면 되므로)
    - 높은 안정성(대형 컴퓨터의 리소스 관리)
    - 고성능(유한 리소스 관리)
  * 단점
    - 높은 도입/유지 비용
    - 확장성의 한계
### 2. 분할형 아키텍처
**여러 대의 컴퓨터**를 조합해서 **하나의 시스템**을 구축하는 구조
표준 OS나 개발 언어를 이용하기 때문에 '**오픈 시스템**'이라고도 불림
또, 여러 대의 컴퓨터를 연결해서 이용하기 때문에 '**분산 시스템**' 이라 부르는 경우도 있음
* 장점
  - 낮은 비용
  - 높은 확장성
* 단점
  - 대수가 늘어날수록 관리 구조가 복잡해짐
  - 한 대가 망가지면 영향 범위를 최소화하기 위해 서버별 역할을 세세하게 검토해야함

> **서버, Server**
<u>분할형 아키텍처에서 이용되는 컴퓨터</u>를 '서버'라고 함
'서버'라는 용어는
컴퓨터 자체(하드웨어)를 가리키는 경우도 있고(*물리 서버*),
컴퓨터에서 동작하고 잇는 소프트웨어를 가리키는 경우(*논리 서버*, 웹 서버/DB서버 등)도 있음
서버라는 용어는 원래 '특정 역할에 특화된 것'을 의미함
#### #서버를 분할하는 방식
분할형에서는 서버 분할 방식, 즉 **역할 분담**을 고려해야 함
각각의 서버가 전혀 다른 작업을 하는 것인지, 비슷한 작업을 하는 것인지에 대한 관점
##### (1) 수직 분햘형 아키텍처
서버별로 **다른 역할**을 담당
"수직" - 특정 서버 측면에서 봤을 때, 역할에 따라 '위' 또는 '아래' 계층으로 나뉘기 때문
###### 1) 클라이언트-서버형(C/S) 아키텍처
소프트웨어를 '물리 서버' 상에서 운영
이 소프트웨어에 '**클라이언트**' 또는 '단말'이라 불리는 소형 컴퓨터가 접속해서 이용하는 형태
클라이언트 측에 **전용 소프트웨어**를 설치해야 함
* 장점
  - 소수의 서버로 다수의 클라이언트 요청 처리 가능
  (클라이언트 측에서 많은 처리 가능, 서버측은 데이터 입출력만 하면 됨)
* 단점
  - 클라이언트 측의 소프트웨어 정기 업데이트 필요
  - 서버 확장성에 한계가 발생할 수 있음(서버에 처리가 집중될 경우)
###### 2) 3계층형 아키텍처
클라이언트-서버형 아키텍처의 단점을 개선하기 위한 아키텍처
3층 구조: `프레젠테이션 계층` / `애플리케이션 계층` / `데이터 계층`
* 프레젠테이션 계층
  - 사용자 입력 받음
  - 웹 브라우저 화면 표시
* 애플리케이션 계층
  - 사용자 요청(Request)에 따라 업무 처리
* 데이터 계층
  - 애플리케이션 계층의 요청에 따라 데이터 입출력

ex) 웹 서버(프레젠테이션 계층) <-> AP서버(애플리케이션 계층) <-> DB서버(데이터 계층)

사용자는 **웹 브라우저**를 통해 시스템에 접속
* 장점
  - 특정 서버 부하 집중 개선
  - 클라이언트 단말의 정기 업데이트 불필요(웹 브라우저를 통한 접속)
  - '처리 반환'에 의한 서버 부하 저감(이미지 파일만 읽으면 되는 경우 웹 서버만으로 처리)
* 단점
  - 구조가 클라이언트-서버 구성보다 복잡

##### (2) 수평 분햘형 아키텍처
더 높은 확장성 실현
용도가 같은 서버를 늘려나가는 방식
서버 대수가 늘어나면 한 대가 시스템에 주는 영향력이 낮아져서 안정성 향상
전체적인 성능 향상


