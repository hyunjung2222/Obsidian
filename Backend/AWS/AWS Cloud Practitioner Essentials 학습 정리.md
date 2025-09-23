[노션](https://fanatical-margin-183.notion.site/AWS-Cloud-Practitioner-Essentials-20250915-17-f5b05965d1c746cabff6dc25bd056e1e)
[책](https://online.vitalsource.com/reader/books/100-ACPEXX-37-KO-SG-E?library_return_url=https%3A%2F%2Fonline.vitalsource.com%2Fhome%2Fmy-library)


## 1. 기본 개념

### 온프레미스 배포
- 자체적인 클라우드에 고객 정보 저장 및 업데이트를 하는 데이터베이스를 두는 방식

### 클라우드 컴퓨팅
- **EC2 (Amazon Elastic Compute Cloud)**: 결국 서버
- **AWS Lambda**: 서버를 프로비저닝하거나 관리하지 않고 코드 실행 (최대 실행시간: 15분)

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

### CloudTrail
- 최대 90일까지 모니터링 정보 저장

### 보안
- **MFA** 설정으로 root 계정 보호
- 로그 데이터는 **S3 Glacier**에 저장 (자주 접근하지 않는 데이터)

### Trusted Advisor
- AWS 계정 최적화를 위한 대시보드 제공

## 9. 네트워킹

### 서브넷 유형
- **퍼블릭 서브넷**: 인터넷 통신 가능
- **프라이빗 서브넷**: 인터넷 통신 불가능
### 네트워킹 구성요소
- **NAT Gateway**: 사설 IP를 공인 IP로 변환하여 인터넷 접속 가능
- **EIP (Elastic IP)**: IP 주소 고정
- **보안 그룹**: 트래픽 허용/차단 규칙
- 인스턴스 메타데이터: ec2 인스턴스에서 명령을 내리는 작업