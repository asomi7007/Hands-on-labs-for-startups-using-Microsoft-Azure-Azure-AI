# Resources

온보딩을 원활하게 진행하려면 공식 문서와 참고 자료를 함께 확인하는 것이 좋습니다.
다음 목록은 실습 중 바로 활용할 수 있는 핵심 링크와 자료입니다.

## Azure services used

- **Microsoft for Startups Founders Hub**: [portal.startups.microsoft.com](https://portal.startups.microsoft.com/) – 혜택 신청 및 관리 포털
- **Azure Portal**: [portal.azure.com](https://portal.azure.com/) – 크레딧 적용과 리소스 관리를 확인하는 기본 인터페이스
- **Azure Cost Management**: Azure 포털 내 `비용 관리 + 청구` 메뉴 – 크레딧 잔액과 사용량 모니터링

## Sample data & links

- **Outlook 계정 생성 가이드**: [signup.live.com](https://signup.live.com/)
- **LinkedIn 계정 생성 가이드**: [linkedin.com/signup](https://www.linkedin.com/signup)
- **GitHub 계정 생성**: [github.com/signup](https://github.com/signup)
- **Azure CLI 설치 문서**: [Install the Azure CLI](https://learn.microsoft.com/cli/azure/install-azure-cli)
- **Azure Developer CLI**: [Azure Developer CLI 설치](https://learn.microsoft.com/azure/developer/azure-developer-cli/install-azd)

## Environment variables

본 랩에서는 환경 변수가 필수적이지 않지만, 이후 실습을 대비해 아래 값을 관리해 두면 좋습니다.

- `AZURE_SUBSCRIPTION_ID`: 크레딧이 적용된 새 구독의 ID. `az account show --query id -o tsv`로 확인 가능.
- `AZURE_TENANT_ID`: 새 Microsoft 계정에 연결된 Entra ID 테넌트 ID. `az account show --query tenantId -o tsv`로 확인.
- `GITHUB_TOKEN` (선택): Codespaces나 GitHub CLI 자동화를 위해 Personal Access Token을 생성할 경우 사용합니다.
