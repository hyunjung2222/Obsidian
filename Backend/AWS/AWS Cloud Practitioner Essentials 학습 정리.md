[노션](https://fanatical-margin-183.notion.site/AWS-Cloud-Practitioner-Essentials-20250915-17-f5b05965d1c746cabff6dc25bd056e1e)
[책](https://online.vitalsource.com/reader/books/100-ACPEXX-37-KO-SG-E?library_return_url=https%3A%2F%2Fonline.vitalsource.com%2Fhome%2Fmy-library)


# AWS Cloud Practitioner Essentials 정리

## 1. 클라우드 컴퓨팅 기본 개념

### AWS 클라우드의 주요 이점

- **규모의 경제**: 비용 절감 효과
- **글로벌 인프라**: 빠른 배포 속도와 전 세계 서비스 제공
- **고가용성, 탄력성, 민첩성**: 안정적이고 유연한 서비스 운영

### 배포 모델

- **온프레미스**: 자체 데이터센터에서 인프라 운영
- **클라우드**: AWS에서 제공하는 인프라 활용
- **하이브리드**: 온프레미스와 클라우드 혼합 사용

## 2. AWS 글로벌 인프라

### 가용 영역 (Availability Zone)

- 각 가용 영역은 3개의 데이터센터로 구성
- 지역적으로 분산되어 고가용성 제공

### 콘텐츠 전송

- **Amazon CloudFront**: 글로벌 CDN 서비스로 빠른 콘텐츠 전송

## 3. 컴퓨팅 서비스

### Amazon EC2 (Elastic Compute Cloud)

#### 인스턴스 생성 시 고려사항

1. **이름/태그**: 서비스 구분, 환경 분류, 비용 관리
2. **AMI**: OS + 필수 패키지 이미지
3. **Key Pair**: SSH 접속용 비대칭 키
4. **네트워크 설정**: VPC, 보안 그룹
5. **인스턴스 유형**: 용도에 맞는 성능 선택

#### 인스턴스 유형별 용도

- **컴퓨팅 최적화**: 배치 처리 워크로드
- **스토리지 최적화**: 복잡한 데이터 분석
- **예약 인스턴스**: 1년/3년 약정으로 비용 절약

### AWS Lambda

- **서버리스 컴퓨팅**: 서버 관리 불필요
- **실행 시간 제한**: 최대 15분
- **적용 사례**: 15분 이내의 간단한 스크립트 실행

### AWS Fargate

- **컨테이너 서비스**: Docker 기반 마이크로서비스
- **서버리스 컨테이너**: 인프라 관리 부담 제거

## 4. 로드 밸런싱 및 Auto Scaling

### Elastic Load Balancer (ELB)

#### 유형별 특징

- **ALB (Application Load Balancer)**: HTTP/HTTPS, 7계층
- **NLB (Network Load Balancer)**: TCP/UDP, 4계층
- **GLB (Gateway Load Balancer)**: 3/4계층 지원
- **CLB (Classic Load Balancer)**: 레거시 (사용 중단)

### Auto Scaling

#### 크기 조정 방식

- **수직적 크기 조정**: 인스턴스 성능 변경 (Scale Up/Down)
- **수평적 크기 조정**: 인스턴스 개수 변경 (Scale Out/In)

#### 장점

- 내결함성 개선
- 애플리케이션 가용성 향상
- 비용 최적화

## 5. 스토리지 서비스

### EC2 스토리지

- **인스턴스 스토어**: 임시 스토리지 (재부팅 시 삭제)
- **EBS (Elastic Block Store)**: 영구 블록 스토리지

### Amazon S3

#### 스토리지 클래스

- **S3 Standard**: 자주 액세스하는 데이터
- **S3 Standard-IA**: 자주 액세스하지 않지만 즉시 필요한 데이터
- **S3 Glacier**: 장기 보관용 (로그 데이터 등)
- **S3 Intelligent-Tiering**: 액세스 패턴 불확실시 사용

### AWS Storage Gateway

- 온프레미스와 클라우드 스토리지 연결

## 6. 데이터베이스 서비스

### 관계형 데이터베이스

- **Amazon RDS**: 완전 관리형 관계형 DB
    - 고객 담당: DB 연결, 사용자 계정, 데이터 관리
    - AWS 담당: 하드웨어, OS, DB 소프트웨어 관리

### NoSQL 데이터베이스

- **Amazon DynamoDB**: 서버리스 키-값 데이터베이스
- **Amazon DocumentDB**: 고성능 NoSQL 서비스

### 마이그레이션

- **DMS (Database Migration Service)**: 데이터베이스 마이그레이션

## 7. AI/ML 서비스

### Amazon SageMaker

- GPU 사용 가능한 ML 플랫폼
- EC2 기반 모델 학습 및 배포

### Amazon Bedrock

- 파운데이션 모델 통합 API 제공
- 완전 관리형 생성형 AI 서비스

## 8. 보안 및 자격 증명

### IAM (Identity and Access Management)

#### 접속 방법

- **관리 콘솔**: Username/Password
- **CLI**: Access Key/Secret Access Key
- **SDK**: 프로그래밍 방식 접근

### 인증 방법

- **MFA (다단계 인증)**: 추가 보안 계층
- **IAM 사용자 계정**: 개별 사용자 관리
- **IAM 역할**: 임시 자격 증명

### 권한 부여 서비스

- **AWS Organizations**: 다중 계정 중앙 관리
- **AWS Resource Access Manager**: 리소스 공유
- **Service Control Policy (SCP)**: 조직 수준 정책

### 보안 서비스

- **AWS Shield Standard**: 무료 DDoS 보호
- **Amazon GuardDuty**: 위협 탐지
- **Amazon Macie**: 데이터 보안
- **AWS Security Hub**: 보안 모범 사례 자동 검사
- **IAM Access Analyzer**: 과도한 권한 식별

### 암호화 및 키 관리

- **AWS KMS**: 키 관리 서비스
- **AWS CloudHSM**: 하드웨어 보안 모듈
- **AWS Secrets Manager**: 비밀 정보 관리
- **AWS Certificate Manager**: SSL/TLS 인증서

## 9. 네트워킹

### VPC (Virtual Private Cloud)

- 특정 리전 내에서 생성
- 모든 가용 영역에 서브넷 배치 가능

### 서브넷 유형

- **퍼블릭 서브넷**: 인터넷 게이트웨이 연결
- **프라이빗 서브넷**: NAT 게이트웨이를 통한 인터넷 접근

### 네트워킹 구성요소

- **NAT Gateway**: 사설 IP → 공인 IP 변환
- **EIP (Elastic IP)**: 고정 IP 주소
- **보안 그룹**: 상태 저장(Stateful) 방화벽
- **네트워크 ACL**: 상태 비저장(Stateless) 방화벽

### 연결 서비스

- **Site-to-Site VPN**: 온프레미스-AWS 암호화 연결
- **AWS Global Accelerator**: 글로벌 네트워크 최적화
- **Amazon Route 53**: DNS 관리 서비스

## 10. 모니터링 및 관리

### Amazon CloudWatch

- 실시간 모니터링: CPU, 메모리, 네트워크 사용률
- 알람 설정 및 SNS 알림 연동
- 알람 상태가 반드시 문제를 의미하지는 않음

### AWS CloudTrail

- 사용자 활동 및 API 요청 추적
- 최대 90일 저장
- 보안 그룹 변경사항 등 상세 추적

### AWS Trusted Advisor

- 계정 최적화 대시보드
- 실시간 지침 제공:
    - EC2 낮은 사용률 식별
    - 노출된 액세스 키 탐지
    - 퍼블릭 S3 버킷 확인

## 11. 분석 서비스

- **Amazon Athena**: S3 데이터 쿼리
- **Amazon EMR**: 빅데이터 처리
- **Amazon Kinesis**: 실시간 데이터 스트리밍
- **AWS Glue**: ETL 서비스

## 12. 마이그레이션 전략 (6R)

### 클라우드 마이그레이션

- **Rehost**: 리프트 앤 시프트
- **Relocate**: 하이퍼바이저 수준 이동
- **Repurchase**: SaaS로 전환
- **Replatform**: 부분적 최적화
- **Refactor/Re-architect**: 완전 재설계

### 온프레미스 유지

- **Retire**: 서비스 폐기 (트래픽 없는 서버)
- **Retain**: 현상 유지

## 13. 공동 책임 모델

### AWS 책임

- 물리적 인프라
- 하드웨어 관리
- 네트워크 제어
- 호스트 OS 패치 (Lambda 등)

### 고객 책임

- 게스트 OS 패치
- 애플리케이션 보안
- 데이터 암호화
- 네트워크 트래픽 보호
- IAM 사용자/그룹/역할 관리

## 14. 지원 계획

### AWS Enterprise Support

- 전담 기술 계정 관리자 (TAM)
- 타사 소프트웨어 통합 지원
- 24/7 프리미엄 지원

## 15. AWS Cloud Adoption Framework (AWS CAF)

### 역량 구분

#### 비즈니스 역량

- 비즈니스
- 인력
- 거버넌스

#### 기술 역량

- 플랫폼
- 보안
- 운영

## 16. 인프라 계층 구조

|계층|내용|
|---|---|
|App Code, 데이터|애플리케이션 코드 및 데이터|
|패키지|필요한 패키지들|
|플랫폼|런타임 플랫폼|
|OS|운영체제|
|가상화|가상화 계층|
|서버, Net, 스토리지|물리적 인프라|
|데이터센터|물리적 시설|

## 17. 실전 문제 유형 및 답안

### 설계 원칙

- **여러 가용 영역에 걸친 워크로드 분산**: 실패 대비 설계 원칙

### 마이그레이션 시나리오

- **소유자 없고 트래픽 없는 서버**: Retire(폐기) 전략 적용

### 인증 관련

- **인증 방법**: MFA, IAM 사용자 계정, IAM 단기 자격 증명
- **사용자 인증**: Amazon Cognito, AWS IAM Identity Center, AWS Directory Service
- **프라이빗 S3 버킷 접근**: 적절한 권한을 가진 IAM 역할 생성 후 EC2 인스턴스에 연결

### 보안 모범 사례

- **인스턴스 메타데이터**: EC2 인스턴스에서 명령을 내리는 작업
- **보안 그룹의 특징**: 상태 저장(Stateful) 방식 - 들어갈 때 검사하지만 나올 때는 재검사하지 않음
- **네트워크 ACL**: 상태 비저장(Stateless) 방식, 규칙 번호 순서대로 평가

### 암호화 옵션

- 저장 중 암호화
- 전송 중 암호화
- 서버 측 및 클라이언트 측 암호화
- Cloud HSM

### 규제 요구사항

- **하드웨어 공유 제한**: 프라이빗 클라우드 배포 사용

### 워크로드별 최적 선택

- **15분 이내 간단한 스크립트**: AWS Lambda
- **Docker 애플리케이션 배포**: Amazon EC2
- **복잡한 데이터 분석**: 스토리지 최적화 인스턴스
- **임시 데이터 저장**: EC2 인스턴스 스토어
- **데이터 액세스 패턴 불확실**: S3 Intelligent-Tiering

### 책임 구분

- **AWS Lambda 인프라 패치**: AWS/Amazon 담당
- **Amazon Textract 데이터 암호화**: 고객 담당

## 18. 추가 서비스 상세

### 애플리케이션 서비스

- **Amazon AppStream 2.0**: 완전 관리형 애플리케이션 스트리밍 서비스, 데스크톱 애플리케이션을 클라우드에서 실행하고 사용자에게 안전하게 스트리밍

### 네트워크 최적화

- **AWS Global Accelerator**: AWS 글로벌 네트워크 인프라와 엣지 로케이션 활용하여 애플리케이션 트래픽 최적화 및 성능 향상

### 관리 도구

- **Service Quotas**: AWS 서비스 한도를 중앙에서 확인하고, 증가 요청 제출 및 승인 상태 추적하는 통합 관리 도구

### VPC 특성

- **생성 범위**: 특정 AWS Region 내에서만 생성 가능
- **서브넷 배치**: 해당 Region의 모든 Availability Zone에 걸쳐 서브넷 배치 가능

### 연결 서비스 상세

- **Site-to-Site VPN**: AWS 측 Virtual Private Gateway와 고객 온프레미스 측 Customer Gateway 간의 암호화된 터널 구성

### 컨테이너 서비스

- **AWS Fargate**: Docker 컨테이너 기반 마이크로서비스 애플리케이션 배포 시 서버 인프라 프로비저닝과 관리 부담 제거하는 서비스

### 지원 서비스

- **AWS Enterprise Support**: 전담 기술 계정 관리자(TAM)와 타사 소프트웨어 통합에 대한 전문 지원 포함

### 보안 분석

- **IAM Access Analyzer**: IAM 정책 분석하여 과도한 권한, 외부 액세스, 보안 위험을 식별하고 권한 최소화를 위한 구체적인 권장 사항 제공

### 데이터베이스 보안

- **Security Groups**: RDS 인스턴스에 대한 가상 방화벽 역할, 특정 IP 주소나 포트에서의 인바운드/아웃바운드 트래픽 제어

### 비즈니스 혜택

- **Business Agility**: 신제품과 서비스를 빠르게 출시하고 시장 변화와 고객 요구에 신속하게 대응할 수 있는 능력