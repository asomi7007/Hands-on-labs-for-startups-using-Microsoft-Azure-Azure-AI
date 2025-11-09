# Lab 5 · Affinity Diagram App - GitHub에서 Azure로 자동 배포

Affinity Diagram App은 실시간 협업이 가능한 온라인 포스트잇 보드 애플리케이션입니다. 이 랩에서는 GitHub Codespaces에서 풀스택 앱을 실행하고, GitHub Actions를 통해 Azure Container Apps에 자동으로 배포하는 완전한 CI/CD 파이프라인을 구축합니다.

## 문서 구조 안내

랩 5 콘텐츠는 실습 흐름에 맞춰 여러 문서로 나뉘어 있습니다. 필요한 주제를 빠르게 찾아볼 수 있도록 아래 페이지를 참고하세요.

- **[Introduction](./introduction.md)**: 프로젝트 개요, 기술 스택, 주요 기능을 소개합니다.
- **[Development](./development.md)**: GitHub 포크부터 Codespaces 실행, 로컬 개발 환경 구축까지 단계별 실습을 안내합니다.
- **[Deployment](./deployment.md)**: Azure 배포 설정, CI/CD 파이프라인 구성, 배포 확인까지의 전 과정을 다룹니다.
- **[Security](./security.md)**: GitHub Secrets, Azure 권한 관리, OIDC 인증 등 보안 설정을 정리했습니다.
- **[Resources](./resources.md)**: 공식 문서, 추가 학습 자료, 관련 링크 모음을 제공합니다.
- **[Conversation](./conversation.md)**: 자주 묻는 질문과 문제 해결 가이드를 다룹니다.
- **[Summary](./summary.md)**: 완료 후 점검 항목과 다음 단계 추천 작업을 제공합니다.

## Affinity Diagram App이란?

실시간으로 여러 사용자가 함께 아이디어를 정리할 수 있는 디지털 포스트잇 보드입니다. 브레인스토밍, 회고, 프로젝트 기획 등 다양한 협업 시나리오에서 활용할 수 있습니다.

### 기술 스택
- **Frontend**: React + TypeScript + Vite
- **Backend**: FastAPI (Python)
- **실시간 통신**: WebSocket
- **컨테이너**: Docker
- **호스팅**: Azure Container Apps
- **CI/CD**: GitHub Actions

### 주요 기능
- ✅ 실시간 포스트잇 생성/수정/삭제
- ✅ 드래그 앤 드롭으로 위치 이동
- ✅ WebSocket 기반 실시간 동기화
- ✅ 자동 배포 파이프라인
- ✅ 멀티 유저 동시 편집

## 사전 점검

> 이 랩은 클라우드 기반 개발 환경을 활용하므로 로컬 개발 도구 설치가 필요 없습니다.

- **GitHub 계정**: 저장소 포크와 Codespaces 사용을 위해 필요합니다.
- **Azure 계정 및 활성 구독**: Container Apps 배포를 위해 필요하며, Lab 1에서 받은 크레딧을 사용할 수 있습니다.
- **최신 브라우저**: Chrome, Edge, Firefox 최신 버전 권장

## 빠른 시작 가이드

### 1. GitHub 저장소 포크
1. [원본 저장소](https://github.com/asomi7007/affinity-app) 접속
2. 우측 상단 **Fork** 버튼 클릭
3. **Create fork** 클릭하여 본인 계정에 복사

### 2. Codespaces 실행
1. 포크한 저장소에서 초록색 **<> Code** 버튼 클릭
2. **Codespaces** 탭 선택
3. **Create codespace on main** 클릭
4. VS Code 환경이 브라우저에서 자동으로 열림 (2-3분 소요)

### 3. 개발 서버 시작
```bash
# VS Code 터미널에서 실행
./scripts/start.sh
```

자동으로 다음 작업이 수행됩니다:
- Python 가상환경 생성 및 패키지 설치
- Node.js 패키지 설치
- 백엔드 서버 시작 (포트 8000)
- 프론트엔드 개발 서버 시작 (포트 5173)

### 4. 앱 확인
- VS Code 하단 **포트** 탭에서 포트 5173 옆 🌐 아이콘 클릭
- 새 탭에서 애플리케이션 실행 확인

### 5. Azure 배포
```bash
# 배포 스크립트 실행
./scripts/setup-azure-cicd.sh
```

대화형 프롬프트를 따라 Azure 리소스를 생성하고 CI/CD를 설정합니다.

## 확인 체크리스트

- [ ] GitHub 저장소 포크 완료
- [ ] Codespaces에서 앱 정상 실행
- [ ] 포스트잇 생성/수정/삭제 작동 확인
- [ ] WebSocket 연결 상태 확인 (우측 상단 초록색)
- [ ] Azure 리소스 생성 완료
- [ ] GitHub Actions 워크플로우 성공
- [ ] 배포된 앱 접속 및 작동 확인

## 학습 목표

이 랩을 완료하면 다음 내용을 이해하고 실습할 수 있습니다:

1. **GitHub Codespaces**: 클라우드 기반 개발 환경 활용
2. **풀스택 개발**: React + FastAPI 앱 구조 이해
3. **WebSocket**: 실시간 통신 구현 방법
4. **Docker**: 컨테이너 이미지 빌드 및 배포
5. **CI/CD**: GitHub Actions로 자동화된 배포 파이프라인 구축
6. **Azure Container Apps**: 서버리스 컨테이너 호스팅 서비스 활용

## 실습 시간

- **개발 환경 설정**: 10분
- **로컬 실행 및 테스트**: 15분
- **Azure 배포 설정**: 20분
- **CI/CD 파이프라인 구축**: 15분
- **총 예상 시간**: 약 60분

## 다음 단계

모든 단계를 완료한 후에는:
- 코드를 수정하여 새로운 기능 추가
- 다른 사용자와 실시간 협업 테스트
- 추가 Azure 서비스 통합 (예: Azure Storage, CosmosDB)
- 프로덕션 환경을 위한 보안 강화

이제 [Introduction](./introduction.md) 페이지로 이동하여 프로젝트를 자세히 살펴보세요!
