

클라우드 네이티브 (CNCF - Cloud Native Computing Foundation)

클라우드 네이티브 애플리케이션은 프라이빗, 퍼블릭 및 하이브리드 클라우드 환경에서 지속적인 개발과 자동화된 관리 환경을 제공하기 위해 설계된 앱을 말합니다.
이러한 설계는 피드백을 반영하고 지속적, 탄력적으로 결합된 소규모의 독립적인 서비스 컬렉션을 가능하게 합니다.
CNCF의 목적은 클라우드 네이티브 컴퓨팅을 유비쿼터스로 만드는 것입니다. (The Foundation’s mission is to make cloud native computing ubiquitous.)

클라우드 네이티브 기술은 조직이 퍼블릭, 프라이빗, 그리고 하이브리드 클라우드와 같은 현대적이고 동적인 환경에서 확장 가능한 애플리케이션을 개발하고 실행할 수 있게 해준다. 
컨테이너, 서비스 메쉬, 마이크로서비스, 불변(Immutable) 인프라, 그리고 선언형(Declarative) API가 이러한 접근 방식의 예시들이다.
이 기술은 회복성, 관리 편의성, 가시성을 갖춘 느슨하게 결합된 시스템을 가능하게 한다. 견고한 자동화 기능을 함께 사용하면, 엔지니어는 영향이 큰 변경을 최소한의 노력으로 자주, 예측 가능하게 수행할 수 있다.

```
클라우드 네이티브 컴퓨팅은 요악하면 크게 4가지 요소를 들 수 있습니다.

- MSA (MicroService Architecture)
- Container
- CI/CD
- DevOps
```

구글은 첫 프로젝트로 쿠버네티스를 기부했습니다. CNCF는 오픈소스 프로젝트 성숙도를 샌드박스(Sandbox), 인큐베이팅(Incubating), 졸업(Graduated)으로 나누고 있습니다.

Cloud Native, Microservices, Container 등에 대해서 많이 들어봤을 겁니다. 이 용어들은 서로 밀접한 관련이 있는 듯 보이지만 정작 어떤 관계인지를 설명하기란 쉽지 않습니다. 용어들 간의 관련성을 간단히 정리하자면,
- ① 애플리케이션의 구조를 한 가지 업무에 특화된 독립적인 단위로 개발 (Microservices) 하고,
- ② MSA(①)을 경량화된 가상화 환경에서 구동을 할 수 있는 단위 (Container)로 생성하고,
- ③ 여러 개의 Container(②)들을 관리를 할 수 있는 환경 (Cloud Native)이 Cloud Native Computing 이다.

https://jwher.github.io/cncf

https://www.samsungsds.com/kr/insights/101917_RD_Cloudnative.html
