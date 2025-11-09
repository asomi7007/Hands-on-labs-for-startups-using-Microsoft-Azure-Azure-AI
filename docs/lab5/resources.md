# Resources

이 페이지는 Lab 5 실습에 필요한 공식 문서, 학습 자료, 관련 링크를 정리합니다.

## Azure services used

- **Azure Container Apps**: [공식 문서](https://learn.microsoft.com/azure/container-apps/)
  - 서버리스 컨테이너 호스팅 서비스
  - 자동 스케일링 및 HTTPS 지원
  
- **Azure Container Registry (선택)**: [공식 문서](https://learn.microsoft.com/azure/container-registry/)
  - 프라이빗 Docker 이미지 저장소 (본 랩에서는 GHCR 사용)

## Sample data & links

### 원본 저장소
- **Affinity App**: [github.com/asomi7007/affinity-app](https://github.com/asomi7007/affinity-app)

### 공식 문서
- **GitHub Codespaces**: [docs.github.com/codespaces](https://docs.github.com/codespaces)
- **GitHub Actions**: [docs.github.com/actions](https://docs.github.com/actions)
- **GitHub Container Registry**: [docs.github.com/packages](https://docs.github.com/packages/working-with-a-github-packages-registry/working-with-the-container-registry)
- **Azure CLI**: [learn.microsoft.com/cli/azure](https://learn.microsoft.com/cli/azure/install-azure-cli)

### 기술 스택 문서
- **React**: [react.dev](https://react.dev/)
- **TypeScript**: [typescriptlang.org](https://www.typescriptlang.org/docs/)
- **Vite**: [vitejs.dev](https://vitejs.dev/guide/)
- **FastAPI**: [fastapi.tiangolo.com](https://fastapi.tiangolo.com/)
- **WebSocket**: [developer.mozilla.org/WebSocket](https://developer.mozilla.org/docs/Web/API/WebSocket)
- **Docker**: [docs.docker.com](https://docs.docker.com/get-started/)

## Environment variables

### GitHub Secrets (자동 설정됨)

배포 스크립트가 자동으로 다음 Secrets를 설정합니다:

- `AZURE_CLIENT_ID`: Service Principal의 앱 ID
- `AZURE_TENANT_ID`: Azure AD 테넌트 ID
- `AZURE_SUBSCRIPTION_ID`: Azure 구독 ID
- `AZURE_RESOURCE_GROUP`: 리소스 그룹 이름
- `AZURE_CONTAINER_APP_NAME`: Container App 이름

### 로컬 개발용 환경 변수

로컬에서 실행 시 필요한 환경 변수는 없습니다. 모든 설정이 코드에 포함되어 있습니다.

### 프로덕션 환경 변수 (선택)

Container Apps에 추가 설정이 필요한 경우:

```bash
# Azure Portal 또는 CLI로 환경 변수 추가
az containerapp update \
  --name affinity-app \
  --resource-group <resource-group> \
  --set-env-vars "KEY=value"
```

## 추가 학습 자료

### GitHub 관련
- [GitHub Skills - Codespaces](https://github.com/skills/code-with-codespaces)
- [GitHub Actions 워크플로우 구문](https://docs.github.com/actions/using-workflows/workflow-syntax-for-github-actions)
- [OIDC를 사용한 Azure 배포](https://docs.github.com/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-azure)

### Azure 관련
- [Container Apps 빠른 시작](https://learn.microsoft.com/azure/container-apps/quickstart-portal)
- [Container Apps 비용 최적화](https://learn.microsoft.com/azure/container-apps/billing)
- [Azure 무료 크레딧 활용](https://azure.microsoft.com/free/)

### 풀스택 개발
- [React + FastAPI 튜토리얼](https://testdriven.io/blog/fastapi-react/)
- [WebSocket 실시간 통신 가이드](https://developer.mozilla.org/docs/Web/API/WebSockets_API/Writing_WebSocket_client_applications)
- [Docker 멀티 스테이지 빌드](https://docs.docker.com/build/building/multi-stage/)

## 유용한 명령어

### Azure CLI

```bash
# 구독 목록 확인
az account list --output table

# Container App 로그 확인
az containerapp logs show \
  --name affinity-app \
  --resource-group <resource-group> \
  --follow

# Container App 상태 확인
az containerapp show \
  --name affinity-app \
  --resource-group <resource-group> \
  --query "{Name:name, Status:properties.runningStatus, URL:properties.configuration.ingress.fqdn}"
```

### GitHub CLI

```bash
# 워크플로우 실행 상태 확인
gh run list

# 최근 워크플로우 로그 보기
gh run view --log

# Secrets 목록 확인
gh secret list
```

### Docker

```bash
# 로컬에서 이미지 빌드
docker build -t affinity-app .

# 로컬에서 컨테이너 실행
docker run -p 80:80 affinity-app
```
