# Interview

#### = 3 tier 웹 어플리케이션의 정의와 구성방식?
https://velog.io/@parkdasol/3-tier-%EC%9B%B9-%EC%96%B4%ED%94%8C%EB%A6%AC%EC%BC%80%EC%9D%B4%EC%85%98
https://www.ibm.com/kr-ko/cloud/learn/three-tier-architecture#toc---3--RNTI-Ww5
##### - 정의, 구성 방식
- Presentation Layer (FrondEnd) - Web server: HTML, CSS, Javascript - Client service - Apache, Nginx, IIS
- Application Layer (MiddleWare or BackEnd) - WAS server: PHP, Python - DB관련 처리 or 동적 컨텐츠 처리 위한 것 - Tomcat, JBoss, WebLogic
- Data Layer (DataBase or BackEnd) - DB server: DataBase - MySql, Oracle, PostgreSql
- Web -> WAS -> DB or Web/WAS -> DB

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

#### - 컨테이너?
- 애플리케이션을 구동하는 환경을 격리한 공간. 예) Docker (Container Runtime)
- Hypervisor vs Container
  - Hypervisor: Server - OS/Hypervisor - GuestOS- Bin/lib - App
  - Container: Server - OS - Container Engine - Bin/lib - App

![21](https://user-images.githubusercontent.com/94558947/167036130-980026f6-6254-49a5-9eaa-4abb78818a70.PNG)

#### - CI/CD?


#### - Micro services design 의 장단점?


#### - Load Balancer란?


#### - TCP와 UDP의 차이는?


#### - RDBMS와 NoSQL의 차이는?


#### - 웹방화벽이 일반 방화벽과 어떻게 다른지?


#### - RAID는?

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
