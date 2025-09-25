[노션](https://fanatical-margin-183.notion.site/AWS-Cloud-Practitioner-Essentials-20250915-17-f5b05965d1c746cabff6dc25bd056e1e)
[책](https://online.vitalsource.com/reader/books/100-ACPEXX-37-KO-SG-E?library_return_url=https%3A%2F%2Fonline.vitalsource.com%2Fhome%2Fmy-library)


## 1. 기본 개념
### AWS 클라우드의 이점
- 규모의 경제에 대한 이해(ex. 비용 절감)
- 글로벌 인프라의 이점 이해(ex. 배포 속도, 글로벌 범위)
- 고가용성, 탄력성, 민첩성의 이점 이해

### 온프레미스 배포
- 자체적인 클라우드에 고객 정보 저장 및 업데이트를 하는 데이터베이스를 두는 방식

### 클라우드 컴퓨팅
- **EC2 (Amazon Elastic Compute Cloud)**: 결국 서버
- **AWS Lambda**: 서버를 프로비저닝하거나 관리하지 않고 코드 실행 (최대 실행시간: 15분)
- 클라우드 실무자가 AWS Outposts로 수행할 수 있는 작업
	- AWS 인프라 및 서비스를 고객사의 온프레미스 데이터 센터 등 다른 위치로 확장합니다.
- AWS Outposts는 온프레미스 또는 엣지 로케이션에서 실행되는 완전 관리형 솔루션 제품군임.

- Amazon CloudFront를 가장 잘 설명한 것
	- 글로벌 콘텐츠 전송 서비스(CDN?)

## 2. 글로벌 인프라 및 안정성
### 가용 영역 (Availability Zone)
- 데이터 센터가 3개씩 구성됨

- (102p) 컨텐츠를 빠르게 전송하는 기능 제공

## 3. EC2 인스턴스
### EC2 생성 시 고려사항
1. **이름 (태그)**: 구분, 서비스, 개발/QA/운영/비용
2. **AMI (Amazon Machine Image)**: OS 이미지 + 필수 패키지
    - Amazon Quick Start 이미지
    - Marketplace
    - 기존 EC2 인스턴스 → AMI 변환
3. **Key Pair**: 비대칭키 방식
4. **네트워크 및 방화벽**
5. **인스턴스 유형**

- 고객이 배치 처리 워크로드에 Amazon EC2 인스턴스를 사용하려고 한다. 어떤 인스턴스 유형? -> 컴퓨터 최적화
- 예약 인스턴스의 약정 기간 옵션 : 1년, 3년 (RI, reserved instance)
- saving plan
### 로드 밸런싱
- **로드 밸런서**: Auto Scaling 그룹으로 들어오는 모든 웹 트래픽의 단일 접점 역할
- 트래픽 양에 따라 EC2 인스턴스가 추가/제거되며, 요청은 먼저 로드 밸런서로 라우팅됨

## 4. 인프라 계층 구조

|계층|내용|
|---|---|
|App Code, 데이터|애플리케이션 코드 및 데이터|
|패키지|필요한 패키지들|
|플랫폼|런타임 플랫폼|
|OS|운영체제|
|가상화|가상화 계층|
|서버, Net, 스토리지|물리적 인프라|
|데이터센터|물리적 시설|

## 5. AWS 주요 서비스
### IAM (Identity and Access Management)
- AWS 서비스 및 리소스에 대한 액세스를 안전하게 관리
- **3가지 접속 방법**:
    - 관리콘솔: Username, Password
    - CLI: Access Key, Secret Access Key
    - SDK

### 스토리지
- **인스턴스 스토어**: 임시 스토리지
- **EBS (Elastic Block Store)**: 가상 디스크

### 데이터베이스
- **DMS (Database Migration Service)**: 데이터베이스 마이그레이션 서비스
- **DocumentDB** : 고성능과 확장성을 제공하는 NoSQL 데이터베이스 서비스
- **Amazon DynamoDB**: 서버리스 키 값 데이터베이스 서비스 (NoSQL 데이터베이스 서비스), 완전 관리형 데이터베이스 서비스
- **Amazon RDS**: 고객(데이터베이스 연결 설정, 사용자 계정 관리, 데이터 관리 등 담당), AWS(하드웨어, OS, 데이터베이스 소프트웨어 관리 담당), 완전 관리형 데이터베이스 서비스

### AI/ML 서비스
- **SageMaker**:
    - GPU 사용 가능
    - 모델 생성 및 사용
    - EC2 기반
- **Bedrock**:
    - 고성능 파운데이션 모델을 통합 API로 제공하는 완전 관리형 서비스
    - 프롬프트와 구성으로 실험 가능
    - 데이터 소스 정보로 응답 생성 강화
    - 특정 작업 및 도메인에 맞게 모델 조정 가능

## 6. 로드 밸런서 (Elastic Load Balancer)
### 기능
- 단일 엔드포인트 제공
- 하나 이상의 가용 영역에 있는 여러 대상에 트래픽 자동 분산

### 이점
- 고가용성 및 탄력성
- 보안
- 기능 적용 범위
- 강력한 모니터링

### 구성요소
- 리스너
- 대상 그룹
- 규칙

### 유형
- **ALB (Application Load Balancer)**: HTTP 처리, 7계층
- **NLB (Network Load Balancer)**: IP 처리, L4
- **GLB (Gateway Load Balancer)**: L3, L4 지원
- **CLB (Classic Load Balancer)**: 더 이상 사용되지 않음

## 7. Auto Scaling

### 크기 조정 방식
- **수직적 크기 조정**: 인스턴스 크기/유형 변경 (확장/축소)
- **수평적 크기 조정**: 인스턴스 개수 변경 (추가/종료)

### Amazon EC2 Auto Scaling 장점
- 내결함성 개선
- 애플리케이션 가용성 향상
- 비용 절감

## 8. 모니터링 및 분석
### CloudWatch
- **알람 상태**: "In alarm"은 반드시 나쁜 상태는 아님
- 경보 설정 시 **SNS (Simple Notification Service)** 사용
- Amazon EC2 인스턴스의 CPU 사용률, 메모리 사용량, 네트워크 트래픽을 실시간으로 모니터링하는 데 사용
### CloudTrail
- 최대 90일까지 모니터링 정보 저장
- AWS 인프라 전체에 걸쳐 사용자 활동 및 API 요청을 추적
- ex. 보안 그룹 변경 사항을 상세히 추적 가능

### 보안
- **MFA** 설정으로 root 계정 보호
- 로그 데이터는 **S3 Glacier**에 저장 (자주 접근하지 않는 데이터)
- S3 Standard-IA: 자주 액세스하지 않는 데이터를 저장하려고 하지만 필요한 경우 즉시 사용할 수 있어야하는 경우
	- **AWS Shield**: 분산 서비스 거부 공격 막는 것

### Trusted Advisor
- AWS 계정 최적화를 위한 대시보드 제공

## 9. 네트워킹

### 서브넷 유형
- **퍼블릭 서브넷**: 인터넷 통신 가능
- **프라이빗 서브넷**: 인터넷 통신 불가능
### 네트워킹 구성요소
- **NAT Gateway**: 사설 IP를 공인 IP로 변환하여 인터넷 접속 가능
- **EIP (Elastic IP)**: IP 주소 고정
- **보안 그룹**: 트래픽 허용/차단 규칙, 상태(Stateful)방식으로 작동한다.(들어갈 때는 검사를 하지만 나올때는 굳이 검사하지 않음. 검사한  사람은 다시 검사하지 않음)
- **인스턴스 메타데이터**: ec2 인스턴스에서 명령을 내리는 작업
- **Amazon Route 53**: 도메인 이름의 DNS 레코드를 관리하는 데 사용되는 서비스
- **네트워크 ACL** : 상태 비저장 방식(stateless), 규칙 번호 순서에 따라 순차적으로 평가됨

----
- **AWS Cloud Adoption Framework (AWS CAF)**
	- 비즈니스 역량: 비지니스, 인력, 거버넌스
	- 기술 역량: 플랫폼, 보안, 운영

- 마이그레이션 전략
	- 온-프레미스: Retire, Retain
	- 클라우드에서: Rehost, Relocate, Repurchase, Replatform, Refactor 또는 Re-architect


Q. 여러 가용 영역에 걸친 워크로드 분산을 지원하는 설계원칙은>
	- 실패를 
Q. 서버 그룹을 검토, 서버가 AWS로 마이그레이션되고 있음. 서버에는 현재 소유자 없음. 서버로의 트래픽이 거의 또는 전혀 없음. 이러한 서버에 대해 어떤 마이그레이션 전략을 제안해야하는가
	- 폐기

- AWS Lambda의 기본 인프라 패치는 누가 담당? : Amazon, AWS
- Amazon Textract의 데이터 암호화에 대한 책임은 누구에게 있는가: 고객 또는 우리

Q. AWS 클라우드에서는 어떤 암호화 옵션을 사용할 수 있는가
- 저장 중 암호화, 전송 중 암호화, 서버 측 및 클라이언트 측 암호화, Cloud HSM

- 위협 탐지 서비스 : Amazon GuardDuty
- 고객이 무료로 이용할 수 있는 서비스: AWS Shield Standard
- 데이터 보안 서비스 : Amazon Macie
- 모범 사례 검사를 자동화한 서비스 : AWS Security Hub

Q. AWS에서는 어떤 인증 방법을 사용할 수 있는가
	- 다단계 인증 (MFA), IAM 사용자 계정, IAM 단기 자격 증명

- 사용자를 권한 부여
	- IAM, AWS Resource Access Manager, AWS Organization
	- AWS Organization: 여러 AWS 계정을 중앙에서 생성하고 관리하며, 서비스 제어 정책(SCP) 적용과 통합 청구를 제공하는 계정 관리 서비스
	
- 사용자를 인증하는 데 사용
	- Amazon Cognito, AWS IAM Identity Center, AWS Directory Service

- 보안 관련 정보를 위한 데이터 스토어
	- AWS CloudHSM, AWS Key Management Service, AWS Secrets Manager, AWS Certificate 

Q. 인스턴스 수준에서 추가 보안 계층을 제공하는

Q. trusted Advisor는 어떤 실시간 지침을 제공하나요?
	- EC2 인스턴스의 낮은 사용률, 노출된 액세스 키, 퍼블릭 S3 버킷

Q. AWS 공동 책임 모델에 따른 고객의 책임은?


Q. 프라이빗 Amazon S3 버킷 내의 콘텐스에 액세스해야함
	- 적절한 권한을 가진 IAM 역할을 생성. 역할을 EC2 인스턴스에 연결


Q. 한 회사가 클라우드로 마이그레이션하고 있음. 규제 제한이 있어 하드웨어를 다른 회사와 공유할 수 없음. 다음 중 해당 요구사항을 충족하는 것은?
- 프라이빗 클라우드 배포


- 평균 15분밖에 지속되지 않는 매우 간단한 스크립트를 실행: AWS Lambda
- docker 에서 실행되는 애플리케이션을 배포해야함: Amazon EC2
- 복잡한 데이터 분석 애플리케이션을 EC2에서 호스팅해야 함.: 스토리지 최적화 인스턴스
- 개발자는 인스턴스 재부팅 시 제거되는 임시 데이터를 저장해야하나요?: EC2 인스턴스 스토어

AWS Storage Gateway
- 온프레미스 환경을 클라우드 스토리지 서비스와 연결함

Q. 데이터 액세스 패턴이 확실하지 않을 때는 어떤 Amazon S3 스토리지 클래스를 사용해야 하는가
	- S3 Intelligent-Tlering

- 분석 서비스
	- Amazon Athena, Amazon EMR, Amazon Kinesis, AWS Glue

- **Amazon AppStream 2.0**
	- 완전 관리형 애플리케이션 스트리밍 서비스
	- 데스크톱 애플리케이션을 클라우드에서 실행하고 사용자에게 안전하게 스트리밍함

- **AWS Global Accelerator**
	- AWS의 글로벌 네트워크 인프라와 엣지 로케이션을 활용하여 애플리케이션 트래픽을 최적화하고 성능을 향상시킴

- **Service Quotas**
	- AWS 서비스 한도를 중앙에서 확인하고, 증가 요청을 제출하며, 승인 상태를 추적할 수 있는 통합 관리 도구

- **VPC**
	- 특정 AWS Region 내에서만 생성
	- 해당 Region의 모든 Availability Zone에 걸쳐 서브넷을 배치할 수 있음
	  
- **Site-to-Site VPN**
	- AWS 측의 Virtual private gateway와 고객 온프레미스 측의 Customer gateway 간의 암호화된 터널로 구성

- **AWS Fargate**
	- docker 컨테이너 기반 마이크로서비스 애플리케이션을 배포해야할 때, 컨테이너를 실행할 서버 인프라의 프로비저닝과 관리 부담을 제거해주는 AWS 서비스
	
- **AWS Enterprise Support**
	- 전담 기술 계정 관리자(TAM)와 타사 소프트웨어 통합에 대한 전문 지원을 포함

- **Business agility**
	- 신제품과 서비스를 빠르게 출시하고 시장 변화와 고객 요구에 신속하게 대응할 수 있는 능력을 의미합니다.

- **Security Groups**: RDS 인스턴스에 대한 가상 방화벽 역할을 하여 특정 IP 주소나 포트에서의 인바운드/아웃바운드 트래픽을 제어함