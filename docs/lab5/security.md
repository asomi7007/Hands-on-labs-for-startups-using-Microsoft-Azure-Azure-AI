# Security

이 문서는 Affinity Diagram App 배포 시 보안 설정과 모범 사례를 정리합니다.

## Identity & Access (Entra ID)

### Service Principal 권한 관리

배포 스크립트가 자동으로 생성한 Service Principal은 최소 권한 원칙을 따릅니다:

- **역할**: Contributor (리소스 그룹 범위)
- **사용처**: GitHub Actions에서 Azure 리소스 배포

### Federated Credentials (OIDC)

비밀번호 대신 OIDC를 사용하여 GitHub Actions와 Azure 간 인증:

**장점:**
- ✅ 비밀번호 없이 안전한 인증
- ✅ 자동 갱신, 만료 걱정 없음
- ✅ 특정 저장소/브랜치로만 제한 가능

**설정 확인:**
```bash
az ad app federated-credential list \
  --id <client-id>
```

## Secrets & Keys management

### GitHub Secrets

민감한 정보는 반드시 GitHub Secrets에 저장:

**저장된 Secrets:**
- `AZURE_CLIENT_ID`: Service Principal ID
- `AZURE_TENANT_ID`: Azure AD 테넌트 ID
- `AZURE_SUBSCRIPTION_ID`: 구독 ID
- `AZURE_RESOURCE_GROUP`: 리소스 그룹 이름
- `AZURE_CONTAINER_APP_NAME`: 앱 이름

**Secrets 확인:**
1. GitHub 저장소 → Settings
2. Secrets and variables → Actions
3. Repository secrets 목록 확인

!!! warning "주의사항"
    Secrets는 절대 코드나 로그에 노출하지 마세요!

### Environment Variables vs. Secrets

| 유형 | 저장 위치 | 용도 |
|------|----------|------|
| Environment Variables | Container App 설정 | 비민감 설정값 |
| Secrets | GitHub Secrets | 인증 정보, API 키 |

## Network & Data protection

### HTTPS 강제

Azure Container Apps는 기본적으로 HTTPS를 제공:

- ✅ 자동 TLS/SSL 인증서
- ✅ HTTP → HTTPS 자동 리다이렉트
- ✅ 최신 TLS 1.2/1.3 지원

### CORS 설정

백엔드에서 CORS를 허용하여 프론트엔드와 통신:

```python
# backend/app.py
from fastapi.middleware.cors import CORSMiddleware

app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],  # 프로덕션에서는 특정 도메인만 허용
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
```

!!! tip "프로덕션 권장 설정"
    ```python
    allow_origins=["https://your-domain.com"]
    ```

### 데이터 보호

현재 앱은 인메모리 저장소를 사용:

**프로덕션 강화 방안:**
1. **영구 저장소 사용**: Azure Cosmos DB, Azure SQL
2. **데이터 암호화**: 저장 시 암호화 (Encryption at rest)
3. **백업 설정**: 자동 백업 정책 구성

### Container 보안

**이미지 스캔:**
```bash
# Docker 이미지 취약점 스캔
docker scan affinity-app
```

**최소 권한 실행:**
- Container는 root가 아닌 사용자로 실행
- 불필요한 패키지 제거

## 모범 사례

### 1. Secrets 로테이션

정기적으로 Service Principal 인증서 갱신:

```bash
# 새 Federated Credential 생성
az ad app federated-credential create \
  --id <client-id> \
  --parameters credential.json
```

### 2. 최소 권한 원칙

필요한 최소 권한만 부여:

```bash
# 특정 리소스 그룹에만 권한 부여
az role assignment create \
  --assignee <service-principal-id> \
  --role Contributor \
  --scope /subscriptions/<subscription-id>/resourceGroups/<resource-group>
```

### 3. 감사 로그 활성화

Azure Activity Log로 모든 작업 추적:

```bash
# Activity Log 확인
az monitor activity-log list \
  --resource-group <resource-group> \
  --max-events 50
```

### 4. 네트워크 제한

필요시 IP 제한 설정:

```bash
# Container App에 IP 제한 추가
az containerapp ingress access-restriction set \
  --name affinity-app \
  --resource-group <resource-group> \
  --rule-name "office" \
  --ip-address "1.2.3.4/32" \
  --action Allow
```

### 5. Container Registry 보안

GHCR 대신 Azure Container Registry 사용 시:

```bash
# ACR 생성
az acr create \
  --resource-group <resource-group> \
  --name <registry-name> \
  --sku Basic \
  --admin-enabled false

# Managed Identity로 이미지 pull
az containerapp update \
  --name affinity-app \
  --resource-group <resource-group> \
  --registry-server <registry-name>.azurecr.io \
  --registry-identity system
```

## 보안 체크리스트

배포 전 다음 항목을 확인하세요:

- [ ] GitHub Secrets가 안전하게 저장됨
- [ ] OIDC 인증이 설정됨 (비밀번호 미사용)
- [ ] Service Principal이 최소 권한만 가짐
- [ ] HTTPS가 강제됨
- [ ] CORS 설정이 프로덕션 환경에 맞게 조정됨
- [ ] 환경 변수에 민감한 정보 없음
- [ ] Container 이미지에 취약점 없음
- [ ] 정기적인 보안 업데이트 계획 수립

## 보안 사고 대응

### 1. Secrets 유출 시

즉시 다음 조치:

```bash
# 1. Service Principal 비활성화
az ad sp update --id <service-principal-id> --set accountEnabled=false

# 2. GitHub Secrets 갱신
# GitHub 저장소 → Settings → Secrets → 각 Secret 재생성

# 3. 새 Service Principal 생성
./scripts/setup-azure-cicd.sh
```

### 2. 비정상 활동 감지 시

```bash
# Azure Activity Log 확인
az monitor activity-log list \
  --resource-group <resource-group> \
  --max-events 100 \
  --offset 7d

# Container App 로그 확인
az containerapp logs show \
  --name affinity-app \
  --resource-group <resource-group> \
  --follow
```

## 추가 보안 리소스

- [Azure 보안 모범 사례](https://learn.microsoft.com/azure/security/fundamentals/best-practices-and-patterns)
- [Container Apps 보안 가이드](https://learn.microsoft.com/azure/container-apps/security)
- [GitHub Actions 보안 강화](https://docs.github.com/actions/security-guides/security-hardening-for-github-actions)
