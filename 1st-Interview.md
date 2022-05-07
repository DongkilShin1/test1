# Interview

#### = 3 tier 웹 어플리케이션의 정의와 구성방식?
https://velog.io/@parkdasol/3-tier-%EC%9B%B9-%EC%96%B4%ED%94%8C%EB%A6%AC%EC%BC%80%EC%9D%B4%EC%85%98
https://www.ibm.com/kr-ko/cloud/learn/three-tier-architecture#toc---3--RNTI-Ww5

##### - 정의, 구성 방식
- Presentation Layer (FrondEnd) - Web server: HTML, CSS, Javascript - Client service - Apache, Nginx, IIS
- Application Layer (MiddleWare or BackEnd) - WAS server: PHP, Python - DB관련 처리 or 동적 컨텐츠 처리 위한 것 - Tomcat, JBoss, WebLogic
- Data Layer (DataBase or BackEnd) - DB server: DataBase - MySql, Oracle, PostgreSql
- Web -> WAS -> DB or Web/WAS -> DB
- 미들웨어 기능: 트랜잭션 처리, 부하분산 기능

#### = 1픽셀은 몇 byte?
https://velog.io/@parkdasol/1%ED%94%BD%EC%85%80%EC%9D%80-%EB%AA%87%EB%B0%94%EC%9D%B4%ED%8A%B8%EC%9D%BC%EA%B9%8C
- 컬러 이미지: RGB - 각 색깔의 정보는 0~255사이의 값; 각 색깔별로 8bit의 용량이 필요; 3 x 8bit = 24bit, 즉 __3byte__ 필요
- 흑백 이미지: 흑백이미지의 픽셀은 0~255 사이 값. 이 값은 8bit, 즉 __1byte__ 필요.

#### = 리눅스 부팅과정
- https://yonlog.tistory.com/m/59
- Step 1 : Hardware - Power On, BIOS, MBR (ROM)
- Step 2 : BootLoader - GRUB (RAM)
- Step 3 : Kernel - Kernel (Disk)
- Step 4 : Init - Init Level, Login

#### = Distributed and Scalable systems 구성 시 고려할 요소
##### - Distributed and Scalable Systems 
- 분산 시스템은 단일 컴퓨터를 형성하기 위해 함께 작동하는 자율적인 컴퓨터들의 집합이고,
모든 분산 컴퓨터는 상호 의존적이며, 공유 네트워크에 연결되어 정보를 공유하고 소통한다.

##### - Distributed Scalable Systems 구성 시 고려사항
- Failure Handling(장애처리): 일부 구성요소 fail시에도 다른 요소들은 계속 작동한다. 이는 대규모 장애를 방지하지만, 문제 해결/디버깅시 복잡성이 더 커진다.
- Concurrency(동시성) : Client가 공유 자원에 동시 접근시 이슈가 발생할 수 있다. 모든 리소스가 동시 환경에서 안전 할 수 있도록 보장해야 한다.
- Security issues : 데이터 보안과 공유는 분산 컴퓨터 환경의 위험을 증가시킨다. 여러 위치에서 복제된 데이터에 안전하게 접근할 수 있어야 한다.
- Higher initial infrastructure costs : 분산 처리 환경의 deployment 초기 비용은 단일 시스템에 비해 높다. 기본적인 네트워크 설정 문제가 포함돼있다.

##### - Cloud vs Distributed system
- 클라우드 컴퓨팅과 분산 시스템은 다르지만 유사한 컨셉을 사용하고 있다.
- 분산 컴퓨팅은 여러 기기에 task를 분산함으로써 분산 시스템을 사용한다.
- 반면에 클라우드 컴퓨팅은 스토리지, 프로세스, 데이터 관리를 위해 네트워크 호스팅 서버를 사용한다.
- 분산 컴퓨팅은 협업적인 자원 공유를 만들고 __size__ 와 __geographical scalability__ 을 제공하는 것을 목표로 한다.
- 클라우드 컴퓨팅은 투명성, 모니터링 및 보안을 사용하여 On-demand 환경을 제공하는 것이다.

##### - Measurement of scalability
https://yeonduing.tistory.com/8

scalability는 세 가지 측면(size scalability, geographical scalability, administrative scalability)이 있다. 세 가지 모두에서 scalable한 시스템은 좋은 시스템이지만 그렇게 되기 쉽지 않다. 보통 세 가지 중 두 가지 정도에서 scalable한 시스템을 만든다.

1) __Size__ : 
여기서 규모는 사용자 수 즉 사용자 규모 측면과 분산 시스템 컴포넌트 측면에서의 규모에 대한 scalability를 말한다. 많은 수의 컴포넌트로 구성하면 규모있는 분산시스템이 된다. 결국 같은 이야기다. 많은 수의 사용자를 감당하려면 많은 수의 컴포넌트가 필요하다. 분산시스템의 구조를 고려할 때 __규모 측면의 확장성을 제공__ 하려면 중앙 집중식 구조보다 __분산화된 구조__ 를 사용하는 것이 확장성이 좋다.

2) __Geography__ : 
분산 시스템에서 각 서버가 지리적으로 서로 멀리 떨어져 있을 때에도 동일한 퀄리티를 제공할 수 있으면 좋다. 서비스를 요청하는 서버와 클라이언트간의 거리 뿐만 아니라 서비스를 제공하는 서버들 간의 거리도 중요하다. 거리가 멀어지면 멀어질수록 커뮤니케이션 딜레이 때문에 문제가 될 수 있다.

3) __Administration__ : 
Administ하게 스케일러블하다는 것은 기술적인 측면보다는 정책적인 측면이 강하다. 어떤 하나의 분산 시스템 서비스를 특정 조직에서 관리하는 것이 아니고 여러 조직에서 공동으로 관리하고 서비스해주면 더 좋다. 예를 들어 KT, SKT, LG에서 정책 합의를 통해 어떤 서비스를 공동으로 제공해주겠다고 하면 사용하는 통신사에 상관없이 공통된 서비스를 이용할 수 있고 통신사 변경했을 때 별도의 조치없이 계속 사용할 수 있으므로 사람들 입장에서는 훨씬 편해질 것이다. 하나의 분산 시스템 서비스를 여러 조직에서 관리하기 때문에 보안 측면이 강화되어야 한다.

##### Scaling techniques
Administration 측면을 제외하고 Size와 Geography 측면에서 Scalibility를 제공하기 위해 다음 세 가지의 기술적 기법이 있다.

1. Reduce Latency (Asynchronous)
사용자가 클라이언트 애플리케이션에 액션을 취해서 서비스를 요청했을 때 걸리는 시간을 줄이는 것이다.

2. Distribution
DNS는 replication도 사용하지만 주된 기능은 distribution (여러대)이다.

3. Replication
replication은 복제하는 것이다. distribution과 달리 replication만의 장점은 resource의 가용성(availability)이 올라가는 것이다. 같은 resource가 여러 곳에 있으므로 이용할 수 있는 확률이 올라간다. 그리고 인기 있는 자원에 대해 복제해서 여러곳에 두면 부하를 분산(load balancing)시킬 수 있다. Caching (복제), Consistency (리소스 내용 일치)

4. __정리__
Size 측면의 scalability가 상대적으로 가장 해결하기 쉽다. 실제로 쉬운건 아니지만 머신의 성능(capacity)을 높여주면 되기 때문에 상대적으로 쉽다고 볼 수 있다. distribution, replication, and caching을 결합한 형태는 실제로 많이 사용되는 테크닉이다. Administrative scalability는 기술적인 측면이 아니라서 세 가지 중에서 가장 해결하기 어려운 것이다.

#### - 컨테이너? (Container)
- 컨테이너는 __커널 공유하는 방법__ 으로 호스트 OS 하나에서 여러 OS를 __가상화__
- 애플리케이션을 구동하는 환경을 격리한 공간. 예) Docker (Container Runtime)
- Hypervisor vs Container
  - Hypervisor: Server - OS/Hypervisor - GuestOS- Bin/lib - App
  - Container: Server - OS - Container Engine - Bin/lib - App

![21](https://user-images.githubusercontent.com/94558947/167036130-980026f6-6254-49a5-9eaa-4abb78818a70.PNG)

#### - CI/CD? (Continuous Integration / Continuous Deployment, Delivery)
https://helloworld-88.tistory.com/50

The process begins after some changes are committed to a version control system (e.g. Git), the __CI/CD framework (e.g. Jenkins)__ would detect the changes and trigger the automated tests to begin. __If the changes pass the tests, the CI/CD framework would trigger__ the build automation tool (e.g. Docker); finally, the framework would trigger the deployment automation tool (e.g. Kubernetes) and send the new version to production.

##### - CI (Continuous Integration)
- 코드가 변경되어 GIT과 버전 관리 시스템에 업로드되면 commit된 소스코드를 주기적으로 검증 여부를 확인하고 통합하는 것.
  - 대표적인 CI 시스템: Jenkins

- 빌드 스크립트를 통한 CI 자동화 수행 절차
1. 소스코드를 __바이너리 파일로 컴파일__ 한다.
2. 바이너리 파일을 __배포 형태로 패키징__ 한다.
3. __단위 테스트 수행__ 한다.
4. 정적 __분석을 수행__ 한다.
5. __분석 결과를 리포팅__ 한다.
6. 패키징한 파일을 __테스트 서버에 배포__ 한다.

- 지속적 통합으로 __개발 프로세스 속도 높이고, 코드 품질 개선 효과__ 코드 충돌 해결

##### - CD (Continuous Deployment)
https://velog.io/@gkskaks1004/jenkins%EC%99%80-CICD%EC%97%90-%EB%8C%80%ED%95%B4%EC%84%9C
https://velog.io/@parkdasol/CICD

- CD(Contious Delivery) - 개발자들이 코드를 작성하면 레포지토리에 업로드하여 지속적으로 __배포 가능한 상태를 유지하는 것을 의미. 레포지토리에서 고객이 사용 가능한 서비스 환경까지 자동으로 릴리즈__ 할 수 있는 것이다.
- 코드 변경이 파이프라인의 이전 단계를 __모두 성공적으로 통과하면 수동 개입 없이 해당 변경 사항이 프로덕션에 자동으로 배포.__ 지속적 배포는 품질 저하 없이 사용자에게 기능을 빠르게 제공하기 위해 자동화 사용을 극대화한다.

#### - Micro services design 의 장단점?
- Micro Services: 대형 소프트웨어 프로젝트의 기능들을 작고 독립적이며 느슨하게 결합된 모듈로 분해하여 서비스를 제공하는 아키텍처이며, 각 개별 모듈은 개별적인 작업을 담당하며 API를 통해 다른 모듈과 통신합니다.
- https://giljae.medium.com/%EB%A7%88%EC%9D%B4%ED%81%AC%EB%A1%9C%EC%84%9C%EB%B9%84%EC%8A%A4-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98-microservices-architecture-%EC%9D%98-%EC%9E%A5%EC%A0%90%EA%B3%BC-%EB%8B%A8%EC%A0%90-7c45615cfe1a
##### 마이크로 서비스 장점
- 벤더사 중심의 SOA에 비해서 마이크로서비스는 Amazon, Netflix, eBay와 같은 글로벌 서비스 플레이어가 사용할 만큼 강력합니다.
- Improves fault isolation : __단일 모듈의 장애에 대해 전체 어플리케이션은 크게 영향을 받지 않습니다.__
- Eliminates long-term commitment to a single technology stack : 각 개별 서비스에서 __새로운 기술 스택을 시험하고자 한다면 바로 시작__ 할 수 있습니다. __의존 관계가 기존 Monolithic 아키텍처보다 적고 유연__ 합니다. 기능 단위로 서비스가 되기에 새로 조인한 개발자가 기능을 더 쉽게 이해 할 수 있습니다.
- 마이크로 서비스의 배포 및 가상화: __마이크로 서비스기반의 어플리케이션을 배포__ 하는 가장 좋은 방법은 __컨테이너 가상화를 이용__ 하는 것입니다 (Docker). AWS와 같은 IaaS업체의 VM을 이용하여 마이크로 서비스를 배포할 수 있지만 작은 단위의 마이크로 서비스는 VM의 리소스를 전부 활용 하지 못해 비용 효율성을 저하 시킬 수 있습니다. 따라서 컨테이너 기반으로 배포를 하는 것이 유리합니다.

##### 마이크로 서비스 약점
- 분산 시스템 개발은 일반 개발보다 복잡: 모든 것이 독립적인 서비스이기 때문에 __각 모듈간의 인터페이스를 신중하게 처리__ 해야 합니다. 서비스중 하나가 응답하지 않게 될 경우에 대한 방어코드도 작성해야 합니다. 호출 대기 시간이 발생하게 되면 복잡한 상황이 발생할 수 있습니다.
- Multiple Databases 및 트랜젝션 관리가 어려움: __마이크로 서비스 기반의 어플리케이션을 테스트하는 것은 번거로울 수__ 있습니다. 테스트를 시작하기 전에 의존성이 있는 서비스를 미리 확인해야 합니다.
- 마이크로 서비스의 __배포는 복잡__: 각 서비스 간의 조정이 필요 할 수 있습니다. __하지만, 이런 부분들은 자동화 도구__ 를 사용하면 해결 할 수 있습니다.
끝으로, 마이크로 서비스는 벤더사 중심이 아닌 서비스사 중심의 아키텍처이고 이미 글로벌 플레이어에 의해 검증이 되어 있습니다.

Monolithic 아키텍처: challenges
- 어플리케이션이 커질 수록 코드도 방대해지고 로드시에 IDE에 과부하가 걸릴 수 있습니다. 즉, 개발자의 생산성을 저하시키는 요인이 됩니다.
- 하나의 war or ear에 모든 것을 포함하였기에 어플리케이션의 기술 스택을 변경하는 것을 주저하게 됩니다. 예를 들어서 일부 컴포넌트는 JVM내에서 동작하는 Groovy나 Scala와 같은 다른 언어를 사용하여 처리하려고 할 경우 이런 종류의 아키텍처를 사용하면 어떤 side-effect가 발생 할지 예측이 어려우므로 리펙토링을 해야 하지만 코드가 너무 방대해서 리펙토링을 하기가 어렵습니다.
- 어플리케이션내의 특정 기능이 실패하면 전체 어플리케이션에 영향을 미칩니다. 그리고 퍼포먼스가 나쁜 특정 함수/메소드의 영향이 전체 어플리케이션에 고통을 주게 됩니다. 이런 아키텍처에서의 scaling은 서버마다 동일한 war or ear을 배포하여 수행해야 합니다. 각각 서버는 동일한 리소스를 사용하게 되므로 이 것은 효율적인 방법이 아닙니다.
- 어플리케이션이 커질수록 개발자는 작은 단위로 작업을 축소할 수 있어야 합니다. Monolithic은 모든 것이 하나로 묶여 있기 때문에 개발자가 독립적으로 모듈을 개발하고 배포 할 수 없습니다. 그리고 개발은 협업으로 진행되므로 다른 개발자에 의존성때문에 개발 시간이 길어지게 됩니다.

#### - Load Balancer란?
![image](https://user-images.githubusercontent.com/94558947/157914203-6ae42ac9-c84b-4567-a42a-2901a1b45475.png)

- 부하 분산, 기본 RoundRobin 방식
##### L4 로드밸런서
- Layer 4 정보(TCP/UDP port)를 바탕으로 패킷을 분류하고 원하는 서버나 장비로 전송(__포트 기반 필터링__ )
##### L7 로드밸런서
- 이메일의 제목이나 __문자열 파악 또는 HTTP의 URL 또는 FTP의 파일명, 쿠키 정보, 특정 바이러스의 패턴__ 등을 기준으로 트래픽을 분산하는 방법으로 보안에 더욱 유리하고 더욱 정교한 로드 밸런싱(__콘텐츠 기반 제어__ )

#### - TCP와 UDP의 차이는?
##### TCP 
- Connection-oriented protocol
- 속도는 느리나 유실데이터 재전송하여 신뢰성
- 메일 등 신뢰성 필요한 애플리케이션

##### UDP
- Connectionless protocol
- 속도 빠르고 효율적이나 저품질
- 음성전화, 동영상 등 빠른

#### OSI 7
- Application : 사용자가 __어플리케이션__ 을 이용해서 데이터를 입력하고 가공할 수 있다.
- Presentation : __데이터 표현방법인 인코딩, 암호화__ , 압축 등을 할 수 있다.
- Session : 연결을 관장함. 논리적인 __통신의 유지, 관리, 생성__ 를 담당.
- Transport : 받을 대상을 명시해야함. __포트번호__ 를 이용.
- Network : 데이터가 어느 __경로__ 를 통해 이동해야 하는지에 대한 정보를 담고 있다. 경로 설정 및 IP(데이터 도착지) 지정
- Data Link : MAC(__매체 접근 제어__ ) 주소를 이용해 .
- Physical : __디지털 신호를 전기 신호로__ 전송.

#### - RDBMS와 NoSQL의 차이는?
##### RDBMS
- 테이블이 __다른 테이블들과 관계를 맺고__ 모여있는 집합체. 
- 관계를 나타내기 위해 __외래 키(foreign key)__ 사용
- 외래 키를 이용한 __테이블 간 Join__ 이 가능.

__- 장점__
스키마가 있고 테이블간 관계를 맺고 있음. 
정해진 스키마에 따라 데이터를 저장하여야 하므로 명확한 데이터 구조 보장 

__- 단점__
테이블 간 관계를 맺고 있어 시스템이 커질 경우 __JOIN문이 많은 복잡한 쿼리__ 가 만들어짐.
성능 향상을 위해서는 서버의 성능을 향상 시켜야하는 __Scale-up만 지원.__ 비용이 기하급수적으로 늘어날 수 있음.
__스키마로 인해 데이터가 유연하지 못함__. 나중에 스키마가 변경 될 경우 번거롭고 어렵습니다.

##### NoSQL
- 정해진 스키마 없음, 자유로운 데이터 구조(유연성), 테이블간 관계 정의 없음

__장점__
NoSQL에서는 스키마가 없기 때문에 유연하며 자유로운 데이터 구조 가짐. __언제든__ 저장된 데이터 조정 및 새로운 필드 추가 가능
__데이터 분산이 용이__ 하며 __성능 향상을 위한 Saclue-up 뿐만이 아닌 Scale-out 또한 가능__ .

__단점__
데이터 중복이 발생할 수 있으며 중복된 데이터가 변경 될 경우 수정을 모든 컬렉션에서 수행을 해야 합니다.
스키마가 존재하지 않기에 __명확한 데이터 구조를 보장하지 않으며__ 데이터 구조 결정이 어려울 수 있습니다.
데이터 테이블은 그냥 하나의 테이블이며 테이블 간의 관계를 정의하지 않아 일반적으로 __테이블 간 Join도 불가능__ 합니다. 

__1. Key-Value Database__
Key-Value DB는 데이터가 __Key, Value 쌍__ 으로 저장. __Key는 Value에 접근 용도, 값(Value)은 어떠한 형태의 데이터도 가능 (이미지나 비디오도 가능)__.
간단한 API를 제공하는 만큼 __질의 및 반응 속도가 빠름__
대표적인 NoSQL Key-Value Model로는 __Redis, Dynamo DB(Amazon)__ . 

__2. Document Database__
Documnet Database 데이터는 __Key와Document 형태__ 로 저장. 
Key-Value 모델과 다른 점이라면 __Value가 계층적인 형태인 도큐먼트로 저장__.
객체지향에서의 객체와 유사하며, 이들은 하나의 단위로 취급되어 저장된다. 다시 말해 하나의 객체를 여러 개의 테이블에 나눠 저장할 필요가 없어진다는 뜻이다. 
주요한 특징으로는 객체-관계 매핑이 필요하지 않다. 객체를 Document의 형태로 바로 저장 가능하기 때문.
검색에 최적화되어 있는데, 이는 Ket-Value 모델의 특징과 동일하다. 
단점이라면 사용이 번거롭고 쿼리가 SQL과는 다르다는 점이다. 도큐먼트 모델에서는 __질의의 결과가 JSON이나 xml 형태로 출력되기 때문에__ 그 사용 방법이 RDBMS에서의 질의 결과를 사용하는 방법과 다르다. 
대표적인 NoSQL Document Model로는 __MongoDB__

##### RDBMS, NoSQL 언제 사용
- RDBMS 데이터 구조가 명확하며 변경 될 여지가 없으며 명확한 스키마가 중요한 경우 사용하는 것이 좋습니다. 또한 중복된 데이터가 없어(데이터 무결성) 변경이 용이하기 때문에 관계를 맺고 있는 __데이터가 자주 변경이 이루어지는 시스템에 적합__ . 

- NoSQL은 __정확한 데이터 구조를 알 수 없고 데이터가 확장이 될 수 있는 경우__ 에 사용하는 것이 좋습니다. 또한 단점에서도 명확하듯이 데이터 중복이 발생할 수 있으며 중복된 데이터가 변경될 시에는 모든 컬렉션에서 수정을 해야 합니다. 이러한 특징들을 기반으로 __Update가 많이 이루어지지 않는 시스템에 좋으며__ 또한 Scale-out이 가능하다는 장점을 활용해 __막대한 데이터를 저장해야 해서 Database__ 를 Scale-Out를 해야 되는 시스템에 적합합니다.

#### - 웹방화벽이 일반 방화벽과 어떻게 다른지?
- 웹방화벽(WAF)은 웹 애플리케이션에 대한 공격을 탐지/차단하는 보안 장비로서, HTTP, HTTPS를 통한 공격 방어 기술을 가진 웹서비스 전용 장비 (L7), 복호화 가능
- 일반 네트워크 방화벽은 약속된(Reserved) 포트의 차단/허용 방식 방어 (L3, L4)

#### HTTP / HTTPS / SSL
- CRUD(Create, Read, Update, Delete) 동작 - Post, Get, Put, Delete
- __GET__ 은 __주소줄__ 에 값이 ?뒤에 쌍으로 이어붙고 __POST__ 는 숨겨져서(__body안에__ ) 보내진다.
- __GET은 서버에서 어떤 데이터를 가져와서 보여준다거나 하는 용도__
- __POST는 서버의 값이나 상태를 바꾸기 위해서 사용__.

##### HTTP
- 웹 페이지 문서를 웹 서버에 전송요청하는 프로토콜
- HTTP는 암호화되지 않은 방법

##### HTTP2
- Single TCP/IP connection (한 커넥션에 여러개의 메세지를 동시에 주고 받을 수 있음) -  성능 향상
- Compressed binary header (Header 압축 전송) - much less space
- Push capability (server push - HTML문서상에 필요한 리소스를 클라이언트 요청없이 보내줄 수 있음)
즉, __much less latency, more speed than HTTP1__

##### HTTPS
- HTTP 프로토콜에 암호화 기능을 추가한 프로토콜
- 데이터를 보낼 때 인증작업(암호화작업, 암호화 키 이용)을 거친다.

##### SSL (Secure Sockets Layer)
- SSL은 웹사이트와 브라우저 사이에 전송된 데이터를 암호화하여 인터넷 연결의 보안을 유지하는 표준 기술
- TLS(IETF)는 SSL(Netscape)의 업그레이드 된 것

__SSL 인증서__
- 클라이언트와 서버간의 통신을 제3자가 보증해주는 전자화된 문서
- 클라이언트가 서버에 접속한 직후에 서버는 클라이언트에게 이 인증서 정보를 전달한다.
- 통신 내용이 공격자에게 노출되는 것을 막을 수 있다.
- 클라이언트가 접속하려는 서버가 신뢰 할 수 있는 서버인지를 판단할 수 있다.
- 통신 내용의 악의적인 변경을 방지할 수 있다.
- SSL 통신에 사용할 공개키를 클라이언트에게 제공한다.

__SSL에서 사용하는 암호화의 종류__
- 대칭키
대칭키는 동일한 키로 암호화와 복호화를 같이 할 수 있는 방식의 암호화 기법
동일한 키를 주고받기 때문에, 매우 빠르다는 장점이 있지만, 대칭키 전달과정에서 해킹 위험이 있다.
- 공개키
암호화와 복호화에 사용하는 암호키를 분리해서 한 개는 공개키, 한개는 비공개키로 지정
비공개키는 암호화에, 공개키는 복호화에 이용된다.
공개키로 복호화 할 수 있다는 것은 그 데이터가 공개키와 쌍을 이루는 비공개키에 의해서 암호화 되었다는 것을 의미하므로 데이터 제공자의 신원을 보장한다.(전자서명) ex) RSA

__SSL 동작원리__: 
실제 __데이터는 대칭키(비공개키) 방식__으로 암호화하고, __복호화하기 위한 대칭키는 공개키 방식__으로 클라이언트와 서버가 주고 받는다.

__CA(Certificate Authority)__: 
인증서의 역할은 클라이언트가 접속한 서버가 __클라이언트가 의도한 서버가 맞는지__ 를 보장하는 역할. 민간 기업도 가능

##### - CDN 서비스 설명: 사용자에게 콘텐츠 전송 요청(Delivery Request)을 받았을 때, 오리진 서버에서 배포된 가장 가까운 캐싱 서버에서 콘텐츠를 전송하는 서비스.
- CDN은 콘텐츠에 대한 요청이 발생하면 최적으로 배치된 CDN 서버에 엔드유저가 매핑되고, 해당 서버는 요청된 파일의 캐싱된(사전 저장된) 버전으로 응답합니다. 
- 서버가 파일을 찾는 데 실패하는 경우 CDN 플랫폼의 다른 서버에서 콘텐츠를 찾은 다음 엔드유저에게 응답을 전송합니다.
- 콘텐츠를 사용할 수 없거나 콘텐츠가 오래된 경우, CDN은 오리진 서버에 대한 요청 프록시로 작동하여 향후 요청에 대해 응답할 수 있도록 페칭된 콘텐츠를 저장합니다 (CDN이 오리진에 프록시로 작동하며 CDN이 오리진으로부터 전용네트워크로 다운받아 전송)
- https://www.akamai.com/ko/our-thinking/cdn/what-is-a-cdn
- https://goddaehee.tistory.com/173
- 
##### - Docker image 설명
- https://www.lainyzine.com/ko/article/understanding-docker-hub-and-docker-official-images/
- Docker Hub는 Docker 이미지 repository. Docker 이미지를 저장하는 원격 스토리지를 Image Registry라고 부르며, Docker Hub는 공식 Image Registry입니다
- 누구나 만들 수 있기 때문에 만들어진 이미지를 편리하게 사용할 수도 있습니다만, 공식 이미지(Offcial Images), 인증된 퍼블리셔(Verified Publisher)의 이미지나 자신이 직접 만든 이미지만 사용하는 것을 강력히 권장합니다.
- Docker File이란 Docker Image를 만들기 위한 설정 파일입니다. 여러가지 명령어를 토대로 Docker File을 작성하면 설정된 내용대로 Docker Image를 만들 수 있습니다.
- https://khj93.tistory.com/entry/Docker-Docker-File-%EC%9E%91%EC%84%B1%ED%95%98%EA%B8%B0-%EB%AA%85%EB%A0%B9%EC%96%B4

##### - WAF설명: HTTP, HTTPS를 통한 공격 방어 기술을 가진 웹서비스 전용 장비 (L7), 복호화 가능
##### - LB 설명: 부하 분산, 기본 RoundRobin 방식

#### Blcok / Object storage 차이
- DAS(Local 스토리지-직접): Instance storage
- NAS(File 스토리지-LAN네트워크-주차타워-데이타가 계층형 구조로 저장: 저장경로 따라 접근): EFS
- SAN(__Block스토리지__ -별도네트워크-주차장-데이타가 엄격히 정의된 블록에 저장: 블록위치 따라 접근): __EBS__ - 정형, RDB
- __Object 스토리지__ - (발렛파킹-평면 구조에 저장, 고유ID로 접근 ): __S3__ - 비정형, DynamoDB

- DAS, SAN은 디렉토리를 붙여 놓고, 사용자가 Copy 하거나 파일불러오기/읽기등이 가능.
- Object 스토리지는 그것이 불가능하다. 파일을 읽을려면 GET으로 내려 받아서, 읽고 변경 후에 다시 PUT으로 집어 넣어야 하는 것이다. 
- Object 스토리지를 CDN등에서 활용할 수 있는지도 이해가 되는 부분이다. 즉 URL 방식으로 접근이 가능하기도 하다.

__Object 스토리지 접근__
1. __URL 방식으로 접근__
2. AWS/Azure/Google 의 Object 스토리지를 보면 디렉토리 만들 수 있는데, 실제로 이건 디렉토리가 아니다.
오브젝트는 그 자체가 하나의 오브젝트이다. 즉, bucket/filename 이거 자체가 __URL로 표현된 오브젝트__ 이고, 
지금까지 우리가 Directory 에 익숙하기 때문에 Visual 상으로 그것을 표현해 주는 것일 뿐,

- File/Block 스토리지는 중복파일 복제 등을 할때에 "파일이 중복됩니다, 덮어쓰기 하겠습니까?" 이런 것들이 나타난다. 
그 이유는 파일 관리를 파일 이름 기반으로 하고 있다. 따라서 대용량의 파일 이전을 고민할 때에 중복제거등이 고민 될 수 있는 부분이 있다. 
- Object 스토리지는 그런 부분이 없다. 그 하나 하나가 개별 객체이다.               
(디렉토리 안의 파일 개념이 아니다) 따라서 중복이 아니라 그냥 다른 걸로 덮어 쓰기 해 버리는 것이다.
- 이런 차이는 스토리지 전체 차원에서 중요한 의미를 가진다. __파일 시스템들이 각 파일의 변경 정보, 메타 정보등을 가지고 있고 관리 가능_
하지만 오브젝트는 파일 시스템이 없기 때문에, __오브젝트와 함께 그것을 관리해야 하는 것__ 이다.
(파일스토리지와 다른 점은 File스토리지는 1개의 경로만 갖는데 반해, Block스토리지는 여러 개의 경로를 가질 수 있다.)

#### - RAID는?
- RAID 0: Stripe
- RAID 1: Mirroring
- RAID 5: Parity
- RAID 10: RAID 1과 RAID 0을 합친 개념. RAID 1로 각각의 디스크를 묶은 후에 다시 RAID 0으로 묶는다.
 
![image](https://user-images.githubusercontent.com/94558947/167210392-c09849b9-46e9-48b8-a78d-a3bf9901f3a9.png)

#### - Hadoop? 대용량 비정형데이터(비디오,이미지 등)을 분산저장, 분산처리하는 것
  - HDFS (분산저장(NameNode-metadata, DataNode-Data)), MapReduce (분산처리(Map(추출)-Reduce(결과통합)))
  - MapReduce
    - Map: 흩어져 있는 데이터를 key, value 형태로 연관성 있는 데이터 분류로 묶는 작업
    - Reduce: filtering과 sorting을 거쳐 데이터를 추출; Map화한 작업 중 중복 데이터를 제거하고 원하는 데이터를 추출하는 작업
    - https://www.youtube.com/watch?v=3s_xafgRMIM
    - https://www.edureka.co/blog/mapreduce-tutorial/

![image](https://user-images.githubusercontent.com/94558947/166263572-4c3cd784-9b6c-4267-830d-ca01602efa22.png)

![image](https://user-images.githubusercontent.com/94558947/166263766-6f126c6d-e4e2-4ec5-8224-63d3b9de3c81.png)

![image](https://user-images.githubusercontent.com/94558947/166263938-150637ca-f672-4d96-9687-9577498d725a.png)

![image](https://user-images.githubusercontent.com/94558947/166265921-9ee92c54-2d79-4680-821b-25d5fba2239c.png)



https://ciksiti.com/ko/chapters/5514-50-frequently-asked-aws-interview-questions-and-answers  - AWS 자주 묻는 질문
https://blog.naver.com/PostView.naver?blogId=supsuh&logNo=222298527370&parentCategoryNo=&categoryNo=&viewDate=&isShowPopularPosts=false&from=postView - 면접
