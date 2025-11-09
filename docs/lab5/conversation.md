# Conversation

이 페이지는 Lab 5 실습 중 자주 묻는 질문과 문제 해결 방법을 정리합니다.

## 자주 묻는 질문 (FAQ)

### Q1: Codespaces가 시작되지 않아요

**A:** 다음 사항을 확인하세요:
1. GitHub 로그인 상태 확인
2. 브라우저 쿠키/캐시 삭제 후 재시도
3. 다른 브라우저에서 시도
4. GitHub Status 확인: [status.github.com](https://status.github.com)
5. Codespaces 할당량 확인 (무료 계정은 월 120시간 제한)

### Q2: start.sh 실행 시 에러가 발생해요

**A:** 실행 권한을 부여하세요:
```bash
chmod +x scripts/start.sh
./scripts/start.sh
```

포트 충돌 시:
```bash
pkill -f "uvicorn"
pkill -f "vite"
./scripts/start.sh
```

### Q3: Azure 로그인이 실패해요

**A:** 다음을 확인하세요:
1. Azure 계정이 활성화되어 있는지 확인
2. 구독이 있는지 확인
3. 로그아웃 후 다시 시도:
```bash
az logout
az login
```

### Q4: GitHub Actions 워크플로우가 실패해요

**A:** 다음을 확인하세요:
1. Actions 탭에서 상세 에러 로그 확인
2. Secrets가 올바르게 설정되었는지 확인:
   - Settings → Secrets and variables → Actions
   - 필수: `AZURE_CLIENT_ID`, `AZURE_TENANT_ID`, `AZURE_SUBSCRIPTION_ID`
3. Repository permissions 확인:
   - Settings → Actions → General
   - "Read and write permissions" 활성화

### Q5: 배포된 앱에 접속할 수 없어요

**A:** 다음을 확인하세요:
1. Azure Portal에서 Container App 상태 확인
2. Container App의 "Application Url" 확인
3. Ingress가 활성화되어 있는지 확인
4. 로그 스트림에서 에러 확인:
```bash
az containerapp logs show \
  --name affinity-app \
  --resource-group <resource-group> \
  --follow
```

### Q6: WebSocket 연결이 안 돼요

**A:** 다음을 확인하세요:
1. 백엔드 서버가 실행 중인지 확인
2. 브라우저 개발자 도구(F12) → 콘솔 탭에서 에러 확인
3. WebSocket URL이 올바른지 확인
4. 방화벽이나 프록시 설정 확인

### Q7: 실시간 동기화가 작동하지 않아요

**A:** 다음을 시도하세요:
1. 페이지 새로고침 (F5)
2. 브라우저 콘솔에서 WebSocket 연결 상태 확인
3. 우측 상단 연결 상태 표시 확인 (초록색 = 연결됨)
4. 백엔드 로그에서 WebSocket 연결 메시지 확인

### Q8: Docker 이미지 빌드가 실패해요

**A:** 다음을 확인하세요:
1. Dockerfile이 프로젝트 루트에 있는지 확인
2. GitHub Actions 로그에서 상세 에러 확인
3. 로컬에서 빌드 테스트:
```bash
docker build -t affinity-app .
```

##지원 채널

### 공식 문서
- [Azure 지원 문서](https://learn.microsoft.com/azure/container-apps/)
- [GitHub 지원 문서](https://docs.github.com/)

### 커뮤니티
- [Azure 커뮤니티 포럼](https://techcommunity.microsoft.com/t5/azure/ct-p/Azure)
- [GitHub Community](https://github.community/)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/azure-container-apps)

## 트러블슈팅 체크리스트

배포 문제가 발생하면 다음 순서로 확인하세요:

- [ ] GitHub 저장소가 올바르게 포크되었는가?
- [ ] Codespaces가 정상적으로 실행되는가?
- [ ] 로컬에서 앱이 정상 실행되는가?
- [ ] Azure에 로그인되어 있는가?
- [ ] Azure 구독이 활성화되어 있는가?
- [ ] GitHub Secrets가 모두 설정되었는가?
- [ ] GitHub Actions 워크플로우가 실행되었는가?
- [ ] Azure Portal에서 Container App이 생성되었는가?
- [ ] Container App의 상태가 "Running"인가?
- [ ] Ingress가 활성화되어 있는가?
