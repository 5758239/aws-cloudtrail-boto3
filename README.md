### 프로젝트 개요

이번 프로젝트의 목표는 AWS CloudTrail 로그를 활용하여 AWS 보안을 강화하는 자동화 시스템을 구축하는 것이었습니다. 이를 위해 Boto3 라이브러리를 활용하여 AWS 리소스를 프로그래밍 방식으로 관리하고, AWS Lambda와 EventBridge를 사용해 특정 이벤트에 자동으로 대응하는 시스템을 개발했습니다.

#### 프로젝트 요약

1. **S3 버킷 생성 및 CloudTrail 설정**:
   - Boto3를 사용하여 로그를 저장할 S3 버킷을 생성했습니다.
   - CloudTrail 로그를 저장할 수 있도록 S3 버킷에 필요한 정책을 추가했습니다.
   - Boto3를 통해 CloudTrail을 생성하고, Python 코드를 사용해 로깅을 활성화했습니다.

2. **EventBridge 설정**:
   - Boto3를 사용해 EventBridge에서 이벤트 버스와 이벤트 규칙(event rule)을 설정했습니다.
   - EC2 인스턴스 관련 모든 이벤트를 감지하는 규칙을 JSON 형태로 작성하여 EventBridge 규칙으로 추가했습니다.

3. **Lambda 함수 작성 및 연결**:
   - EventBridge에서 감지된 이벤트에 대응하는 Lambda 함수를 작성했습니다.
   - Lambda 함수는 이벤트 로그에서 인스턴스 ID와 사용자명을 추출하여, 비허가 사용자일 경우 인스턴스를 종료시키고 권한을 차단했습니다.
   - 사용자명을 추출하기 위해 최근 3분 내 CloudTrail 로그를 분석하는 함수를 작성했습니다.
