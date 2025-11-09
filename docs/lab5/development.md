# Development

이 문서는 GitHub Codespaces에서 Affinity Diagram App을 실행하고, 코드 구조를 이해하며, 로컬 개발 환경에서 테스트하는 전체 과정을 안내합니다.

## Step 1: GitHub 저장소 포크

### 1.1 저장소 포크하기

1. 브라우저에서 원본 저장소 접속: `https://github.com/asomi7007/affinity-app`
2. 우측 상단 **Fork** 버튼 클릭
3. **Create fork** 클릭 (본인 GitHub 계정에 복사됨)

!!! tip "포크란?"
    원본 저장소를 본인 계정으로 복사하는 것입니다. 원본에 영향을 주지 않고 자유롭게 수정할 수 있습니다.

## Step 2: GitHub Codespaces 실행

### 2.1 Codespaces 시작

1. 포크한 저장소에서 초록색 **<> Code** 버튼 클릭
2. **Codespaces** 탭 선택
3. **Create codespace on main** 클릭
4. 새 탭에서 VS Code 환경이 자동으로 열림 (2-3분 소요)

### 2.2 자동 설정 확인

Codespaces가 시작되면 자동으로:
- ✅ Python 3.11+ 설치
- ✅ Node.js 20+ 설치
- ✅ Docker 사용 가능
- ✅ VS Code 익스텐션 로드

## Step 3: 로컬 개발 환경 실행

### 3.1 터미널 열기

```bash
# VS Code에서 터미널 열기
# 메뉴: Terminal → New Terminal
# 또는 단축키: Ctrl + ` (백틱)
```

### 3.2 애플리케이션 시작

```bash
# 프로젝트 루트에서 실행
./scripts/start.sh
```

스크립트가 자동으로 수행하는 작업:
1. Python 가상환경 생성 (`venv`)
2. 백엔드 패키지 설치 (`pip install -r backend/requirements.txt`)
3. 프론트엔드 패키지 설치 (`npm install --prefix frontend`)
4. 백엔드 서버 시작 (포트 8000)
5. 프론트엔드 개발 서버 시작 (포트 5173)

### 3.3 실행 확인

터미널에 다음과 같은 메시지가 표시됩니다:

```
✅ 백엔드 서버: http://localhost:8000
✅ API 문서: http://localhost:8000/docs
✅ 프론트엔드: http://localhost:5173

🎉 애플리케이션이 성공적으로 시작되었습니다!
```

### 3.4 브라우저에서 확인

1. VS Code 하단 **포트** 탭 확인
2. 포트 `5173` 옆 🌐 지구본 아이콘 클릭
3. 새 탭에서 애플리케이션이 열림

## Step 4: 애플리케이션 테스트

### 4.1 프론트엔드 기능 테스트

```
1. 브라우저에서 앱 열기
2. [포스트잇 추가] 버튼 클릭
3. 생성된 포스트잇을 드래그로 이동
4. 포스트잇 더블클릭으로 내용 수정
5. 우측 상단 연결 상태 확인 (초록색 = 연결됨)
6. X 버튼으로 포스트잇 삭제
```

### 4.2 백엔드 API 확인

1. 새 탭에서 `http://localhost:8000/docs` 접속
2. FastAPI 자동 생성 API 문서 확인

**주요 엔드포인트:**

| Method | Endpoint | 설명 |
|--------|----------|------|
| GET | `/health` | 서버 상태 확인 |
| GET | `/api/notes` | 모든 노트 조회 |
| POST | `/api/notes` | 새 노트 생성 |
| PUT | `/api/notes/{id}` | 노트 수정 |
| DELETE | `/api/notes/{id}` | 노트 삭제 |
| WS | `/ws/board/{board_id}` | WebSocket 연결 |

### 4.3 실시간 동기화 테스트

1. 브라우저에서 앱을 두 개의 탭/창으로 열기
2. 한 쪽에서 포스트잇 생성
3. 다른 쪽에서 즉시 반영되는지 확인
4. 포스트잇 이동, 수정, 삭제 모두 실시간 동기화 확인

## Step 5: 코드 구조 이해

### 5.1 프로젝트 구조

```
affinity-app/
├── frontend/              # React 애플리케이션
│   ├── src/
│   │   ├── components/   # UI 컴포넌트
│   │   ├── modules/      # 페이지 모듈
│   │   ├── ws/          # WebSocket 관리
│   │   └── App.tsx      # 메인 앱
│   ├── package.json     # Node.js 의존성
│   └── vite.config.ts   # Vite 설정
│
├── backend/             # FastAPI 서버
│   ├── app.py          # 메인 서버 파일
│   ├── models.py       # 데이터 모델
│   └── requirements.txt # Python 의존성
│
├── .github/workflows/   # GitHub Actions CI/CD
│   └── ci-cd.yml       # 메인 파이프라인
│
└── scripts/            # 유틸리티 스크립트
    ├── start.sh       # 개발 서버 시작
    └── setup-azure-cicd.sh # Azure 배포 설정
```

## 문제 해결

### Q1: start.sh 실행 시 권한 오류

```bash
chmod +x scripts/start.sh
./scripts/start.sh
```

### Q2: 포트가 이미 사용 중

```bash
pkill -f "uvicorn"
pkill -f "vite"
./scripts/start.sh
```

### Q3: WebSocket 연결 실패

- 백엔드 서버가 실행 중인지 확인 (`http://localhost:8000/health`)
- 브라우저 콘솔에서 오류 메시지 확인

## 다음 단계

로컬 개발 환경 설정이 완료되었습니다. 이제 [Deployment](./deployment.md) 페이지로 이동하여 Azure에 배포하는 방법을 알아보세요!
