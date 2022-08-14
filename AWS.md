# AWS

## Getting started
### AWS Regions
- 리전은 데이터 센터의 클러스트
- us-east-1, eu-west-3, ap-northeast-2 같은 명칭
- 대부분의 AWS서비스는 리전에 종속적
- 컴플라이언스 측면을 고려하여 리전을 선택
- 가격은 지역마다 다름

### AWS Availability Zones
- 각 리전에는 많은 AZ가 있음(보통 3, 최대 6)
- 서로 분리되어 있어 장애로부터 격리
- 고 대역폭, 초 저지연 네트워크로 연결
- 최종 사용자에 가까운 AZ일 수록 더 짧은 지연시간으로 도달

## IAM Section
### Users & Groups
- IAM = Identity and Access Management, 글로벌 서비스
- 루트 계정은 기본 생성, 공유하거나 직접적으로 사용하는 것은 지양
- 사용자는 그룹에 속할 필요는 없고, 여러 그룹에 속하는 것도 가능

### MFA
- Virtual MFA device : Google Authenticator, Authy (어플리케이션)
- Universal 2nd Factor(U2F) Security Key (USB 타입)
- Hardware Key Fob MFA Device (OTP 기계처럼 생김)

### Access Keys
- Access Key ID / Secret Access Key : 마치 ID와 PW처럼 동작. 절대 공유 금지

### Guideline
- AWS 계정 설정 외에는 루트 계정 사용 금지
- 사용자를 그룹에 할당하고 그룹에 권한 할당
- 프로그래밍 방식 액세스(CLI / SDK)에 엑세스 키 사용
- IAM 사용자 및 액세스 키는 절대 공유 금지

=======

+++++++


## EC2
### EC2
- Elastic Compute Cloud = IaaS
- 주로 EC2, 가상 드라이브(EBS)에 데이터 저장, 부하 분산(ELB)로 구성
- Auto-Scaling group(ASG)을 사용하여 서비스 확장

### Sizing & Configuration
- OS : 리눅스, 윈도우즈, 맥OS
- CPU Core / RAM
- Storage 용량(EBS & EFS or EC2 Instance Store)
- 부트스트랩 스크립트(최초 시작 시 구성)

### User data script
- BootStrap 스크립트는 인스턴스가 처음 시작될 때 한번만 실행
- 업데이트 설치, 소프트웨어 설치 등등 생각하는 모든 것
- EC2 User data script는 Root 사용자로 실행 됨




## Storage Section

### EBS(Elastic Block Store)
- 인스턴스가 실행되는 동안 연결할 수 있는 네트워크 드라이브
- 인스턴스가 종료된 후에도 데이터를 유지할 수 있음
- 한 번에 하나의 인스턴스에만 마운트할 수 있음
- 특정 AZ(Availabiltity Zones)에 바인딩
- EC2 인스턴스가 종료될 때, 기본 설정은 루트 EBS 볼륨이 삭제됨
- 루트 EBS볼륨이 삭제되지 않도록 AWS콘솔/CLI로 제어 가능
- EBS 볼륨의 스냅샷을 만들어서 AZ또는 리전간에 복사 가능

### EFS

