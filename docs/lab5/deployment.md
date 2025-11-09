# Deployment

이 문서는 Azure Container Apps에 Affinity Diagram App을 배포하고, CI/CD 파이프라인을 설정하며, 배포된 앱을 확인하는 전체 과정을 안내합니다.

## Step 1: Azure 배포 설정

### 1.1 배포 스크립트 실행

```bash
# Codespaces 터미널에서 실행
./scripts/setup-azure-cicd.sh
```

### 1.2 단계별 설정

#### 📍 Azure CLI 확인
스크립트가 자동으로 Azure CLI 설치 여부를 확인합니다.

#### 📍 Azure 로그인
1. 브라우저가 자동으로 열림
2. Azure 계정으로 로그인
3. 터미널로 돌아오면 자동 진행

#### 📍 구독 선택
```
현재 구독 확인 → Enter (기본값 사용)
또는 다른 구독 선택
```

#### 📍 GitHub 저장소 정보
```
자동으로 감지됨
확인 후 Enter
```

#### 📍 Azure 리소스 설정
```
프로젝트 이름: affinity-app [Enter]
리소스 그룹: 자동 생성된 이름 [Enter]
지역: 1 (한국 중부) [Enter]
Container App 이름: affinity-app [Enter]
환경 이름: affinity-app-env [Enter]
Docker 이미지: 자동 생성 [Enter]
```

#### 📍 리소스 생성
```
리소스 그룹 생성 중... (30초)
Service Principal 생성 중... (1분)
Federated Credentials 설정 중... (30초)
```

#### 📍 GitHub Secrets 설정
```
설정 방법 선택: 1 (자동 설정) [Enter]

GitHub Token 생성 방법:
1) GitHub CLI Device Flow (권장) → 1 [Enter]

Device Flow 선택 시:
1. 브라우저에서 https://github.com/login/device 열림
2. 표시된 코드 입력
3. 권한 승인
4. 터미널로 돌아와서 대기
```

## Step 2: CI/CD 파이프라인 이해

### 2.1 파이프라인 흐름

```mermaid
graph LR
    A[코드 Push] --> B[GitHub Actions 트리거]
    B --> C[테스트 실행]
    C --> D[Docker 이미지 빌드]
    D --> E[GHCR에 이미지 푸시]
    E --> F[Azure에 배포]
    F --> G[앱 실행]
```

### 2.2 각 단계 설명

#### 1️⃣ 코드 Push → GitHub Actions 트리거
- `main` 브랜치에 코드 푸시 시 자동 시작
- `.github/workflows/ci-cd.yml` 파일이 실행 규칙 정의

#### 2️⃣ 테스트 실행
- TypeScript 타입 체크
- ESLint 코드 품질 검사
- 단위 테스트 실행

#### 3️⃣ Docker 이미지 빌드
- Dockerfile 기반으로 컨테이너 이미지 생성
- 멀티 스테이지 빌드로 최적화된 프로덕션 이미지 생성

#### 4️⃣ GitHub Container Registry (GHCR) 푸시
- 빌드된 이미지를 GitHub의 컨테이너 저장소에 업로드
- 버전 태그 자동 생성 (latest, main, commit-hash)

#### 5️⃣ Azure Container Apps 배포
- Azure 로그인 (OIDC 인증)
- 새 이미지로 Container App 업데이트
- 무중단 배포 (Blue-Green)

#### 6️⃣ 앱 실행 및 확인
- 배포 완료 후 자동으로 앱 URL 제공
- Health check로 정상 작동 확인

## Step 3: 첫 배포 실행

### 3.1 Git 커밋 및 푸시

```bash
# 변경사항 확인
git status

# 변경사항 커밋
git add .
git commit -m "feat: Initial deployment setup"

# main 브랜치로 푸시
git push origin main
```

### 3.2 GitHub Actions 모니터링

1. 브라우저에서 GitHub 저장소 접속
2. **Actions** 탭 클릭
3. 실행 중인 워크플로우 확인 (주황색 동그라미)
4. 클릭해서 실시간 로그 확인
5. 완료까지 5-10분 대기

## Step 4: 배포 확인

### 4.1 배포 상태 확인

워크플로우가 성공하면 (초록색 체크):
1. 워크플로우 Summary 클릭
2. "Deploy to Azure" 섹션 확인
3. 배포된 앱 URL 확인

### 4.2 배포된 앱 접속

```
URL 형식: https://affinity-app.{region}.azurecontainerapps.io

예시:
https://affinity-app.koreacentral.azurecontainerapps.io
```

### 4.3 배포 확인 체크리스트

- [ ] 앱 접속 가능
- [ ] 포스트잇 생성/수정/삭제 작동
- [ ] WebSocket 연결 (우측 상단 초록색)
- [ ] 다른 브라우저/탭에서 실시간 동기화 확인

## Step 5: 지속적 배포

### 5.1 코드 수정

로컬에서 코드를 수정합니다:

```typescript
// frontend/src/components/Note.tsx
// 포스트잇 색상 변경 예제
style={{
  backgroundColor: '#ffeb3b'  // 노란색으로 변경
}}
```

### 5.2 자동 배포

```bash
# 변경사항 커밋 및 푸시
git add .
git commit -m "feat: Change note color to yellow"
git push origin main
```

GitHub Actions가 자동으로:
1. 새 코드 감지
2. 테스트 실행
3. 새 이미지 빌드
4. Azure에 자동 배포

## 문제 해결

### Q1: Azure 로그인 실패

```bash
# 다시 로그인 시도
az logout
az login
```

### Q2: GitHub Actions 실패

1. Actions 탭에서 에러 로그 확인
2. Secrets 설정 확인 (Settings → Secrets)
3. 권한 설정 확인

### Q3: 배포된 앱 접속 불가

1. Azure Portal에서 Container App 상태 확인
2. 로그 스트림 확인
3. Health check 엔드포인트 확인

## 다음 단계

배포가 완료되었습니다! 이제:
- 새 기능을 추가하고 자동 배포 테스트
- [Security](./security.md)에서 보안 설정 확인
- [Summary](./summary.md)에서 전체 과정 복습
