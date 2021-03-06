

# Cloud Native Computing (CNCF:Cloud Native Computing Foundation)

클라우드 네이티브 애플리케이션은 프라이빗, 퍼블릭 및 하이브리드 클라우드 환경에서 지속적인 개발과 자동화된 관리 환경을 제공하기 위해 설계된 앱을 말합니다.
이러한 설계는 피드백을 반영하고 지속적, 탄력적으로 결합된 소규모의 독립적인 서비스 컬렉션을 가능하게 합니다.
CNCF의 목적은 클라우드 네이티브 컴퓨팅을 유비쿼터스로 만드는 것입니다. (The Foundation’s mission is to make cloud native computing ubiquitous.)

클라우드 네이티브 기술은 조직이 퍼블릭, 프라이빗, 그리고 하이브리드 클라우드와 같은 현대적이고 동적인 환경에서 확장 가능한 애플리케이션을 개발하고 실행할 수 있게 해준다. 
컨테이너, 서비스 메쉬, 마이크로서비스, 불변(Immutable) 인프라, 그리고 선언형(Declarative) API가 이러한 접근 방식의 예시들이다.
이 기술은 회복성, 관리 편의성, 가시성을 갖춘 느슨하게 결합된 시스템을 가능하게 한다. 견고한 자동화 기능을 함께 사용하면, 엔지니어는 영향이 큰 변경을 최소한의 노력으로 자주, 예측 가능하게 수행할 수 있다.

클라우드 네이티브 컴퓨팅은 요악하면 크게 **4가지 요소**가 있습니다.
```
- MSA (MicroService Architecture)
- Container
- CI/CD
- DevOps
```

구글은 첫 프로젝트로 쿠버네티스를 기부했습니다. CNCF는 오픈소스 프로젝트 성숙도를 샌드박스(Sandbox), 인큐베이팅(Incubating), 졸업(Graduated)으로 나누고 있습니다.

Cloud Native, Microservices, Container 등에 대해서 많이 들어봤을 겁니다. 이 용어들은 서로 밀접한 관련이 있는 듯 보이지만 정작 어떤 관계인지를 설명하기란 쉽지 않습니다. **용어들 간의 관련성**을 간단히 정리하자면,
```
- ① 애플리케이션의 구조를 한 가지 업무에 특화된 독립적인 단위로 개발 (Microservices) 하고,
- ② MSA(①)을 경량화된 가상화 환경에서 구동을 할 수 있는 단위 (Container)로 생성하고,
- ③ 여러 개의 Container(②)들을 관리를 할 수 있는 환경 (Cloud Native)이 Cloud Native Computing 이다.
```

## Cloud Native 기술 배경

기존 VM과 비교했을 때, 컨테이너 기술은 **Hypervisor 엔진과 Guest OS를 제거**하여 자원효율화를 제공합니다. 기존 가상머신에서 컨테이너로 기술이 전환이 이뤄지면서 생겨난 변화는 다음과 같습니다. 이러한 변화는 Cloud Native Architecture의 주요한 특징으로 등장하게 됩니다.

 - 독립적인 구동 단위의 패키징
     : Monolithic한 통합시스템의 가상화에서 여러 개로 분산된 시스템의 컨테이너 구조로 변화
 - 서비스 모델 기반 관리
     : 시스템을 개별 단위로 관리하는 방식에서 동일한 기능을 제공하는 복수의 컨테이너 관리로 변화

![image](https://user-images.githubusercontent.com/94558947/162226482-bdd6fbcc-ebf8-4fc8-bb8a-06b7680ac2d1.png)

CNCF에서 정의하는 Cloud Native system은 다음과 같은 특성을 갖습니다.
1) (a) Container 단위로 관리: 구동되는 애플리케이션은 독립적인 배포 단위인 동시에 독립적인 자원관리 단위임. 또한 Cloud Native application은 코드와 컴포넌트 재사용 가능
2) (b) 동적 관리: 중앙관리 방식의 스케줄과 관리로 서버 자원의 효율성을 높이고 자원관리와 운영비용을 절감시킴.
3) (c) Microservices 중심 관리: 의존관계가 명확하고, 결합이 느슨한 모듈은 애플리케이션 전반에 민첩성과 관리 용이성을 제공함.

CNCF는 아래와 같은 Cloud Native 참조 아키텍처를 제시하고 있습니다.

![image](https://user-images.githubusercontent.com/94558947/162245961-222da24a-b57f-4fdb-a802-162a49e7b83f.png)

1) Application definition/development: Container native 애플리케이션 구현하는데 필요한 meta data, 설정, 도구, 컨테이너 이미지 관리 도구 등
2) Orchestration & Management: 컨테이너 오케스트레이션 (Kubernetes, SWARM 등) 도구를 활용한 컨테이너 배포, Logging & Monitoring, Service discovery 등
3) Runtime: 컨테이너 실행 표준(OCI), 컨테이너 네트워킹 (Container Networking Interface project), Storage (Volume driver) 등
4) Provisioning: Container환경을 고려한 DevOps deployment 도구와 provisioning 등
5) Infrastructure: CNCF의 프로젝트 영역은 아니지만 Bare metal, Public cloud 구동 호환성을 유지


https://jwher.github.io/cncf

https://www.samsungsds.com/kr/insights/101917_RD_Cloudnative.html

## Cloud

![image](https://user-images.githubusercontent.com/94558947/162244638-3f928282-49fa-4c98-a56a-1e0fb023a436.png)

노란색의 You manage는 사용자가 관리해야 할 부분이고, 흰색의 Managed by vendor는 기업(Providers or MSPs)에서 관리해주는 부분입니다

- **클라우드 컴퓨팅**은 (서로 다른 물리적인 위치에 존재하는) 컴퓨터들의 리소스를 **가상화 기술로 통합**해 제공하는 기술을 말합니다.

예를들면, 개인용 컴퓨터나 기업의 서버에 개별적으로 저장해 두었던 프로그램이나 문서를 클라우드에 저장하고 웹 브라우저 등 필요한 어플리케이션을 구동해 원하는 작업을 수행할 수 있는 사용자 중심의 컴퓨터 환경을 말합니다.

예시: Google DOCs(Google), 네이버 오피스 etc

__가상화와 클라우드 컴퓨팅의 차이__ 
- 가상화는 기술이고 클라우드는 방법론 입니다.

__가상화__
- 가상화는 우리가 쓰던 VMware나 Virtualbox와 같이 단일한 물리 하드웨어 시스템에서 여러 환경이나 자원을 생성할 수 있는 기술입니다.
하이퍼바이저 라고 불리는 소프트웨어가 하드웨어에 직접 연결되며 가상 머신을 만들 수 있습니다.
이러한 가상 머신은 하이퍼바이저의 자원을 적절하게 배분받은 후 사용합니다.

. 클라우드 (컴퓨팅)
클라우드 컴퓨팅은 가상화를 통해 분리,분할된 자원(컴퓨팅, 네트워크, 스토리지 인프라 자원, 서비스, 플랫폼, 애플리케이션)을 사용자에게 제공하는 접근 방식입니다.

즉, 가상화는 하드웨어의 기능을 공유(분리, 분할)하는 기술이고 클라우드 컴퓨팅은 하드웨어의 분할된 자원을 사용하는 (솔루션보다 큰 개념인) 방법론입니다.

### IaaS

Infrastructure 레벨을 제공하는 서비스를 의미합니다. 위에 보이는 것과 같이 사용자는 OS를 직접 올리고 그 상위 계층만 구성하면 되는 모델입니다.

예시: AWS의 EC2

### PaaS

개발자가 응용 프로그램을 작성할 수 있도록 플랫폼 및 환경을 제공하는 모델입니다.

예시: PaaS의 제공 업체로는 Heroku, Google App Engine, etc.

### SaaS

설치할 필요도 없이 클라우드를 통해 제공되는 SW입니다.

예시: Gmail, Google Docs, MS오피스365, 드롭박스, etc

https://wnsgml972.github.io/network/2018/08/14/network_cloud-computing/




## VMware, Nutanix, Openstack 비교

https://disciplechoi.github.io/cloud/2021/06/10/comparision-cloud-vendor.html

https://wnsgml972.github.io/network/2018/08/14/network_cloud-computing/
