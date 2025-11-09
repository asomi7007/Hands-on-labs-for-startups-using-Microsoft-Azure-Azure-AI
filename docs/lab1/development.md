# Development

이 랩은 애플리케이션 코드를 배포하는 대신 Azure 사용을 위한 계정과 구독을 준비하는
데 초점을 맞춥니다. 따라서 “개발 환경”은 곧 온보딩 플로우이며, 아래 순서를 따르면
팀 전체가 동일한 조건에서 실습을 진행할 수 있습니다.

## Local dev steps

1. **프라이빗 브라우저 세션 시작**: Edge InPrivate 또는 Chrome 시크릿 창을 실행합니다.
2. **Outlook 계정 생성**: [signup.live.com](https://signup.live.com/)에서 실습 전용 이메일과 비밀번호를 등록합니다.
3. **LinkedIn 계정 생성**: [linkedin.com/signup](https://www.linkedin.com/signup)에서 동일 이메일로 계정을 만들고 인증합니다.
4. **Founders Hub 등록**: [portal.startups.microsoft.com/signup](https://portal.startups.microsoft.com/signup)의 `Get started quickly` 섹션에서 새 Microsoft 계정으로 로그인합니다.
5. **MFA 및 PIN 설정**: 보조 이메일 기반 MFA를 구성하고 Windows Hello PIN은 `사용 안 함`을 선택합니다.
6. **Azure 크레딧 사용**: Founders Hub Benefits에서 `$1,000 Azure 크레딧`을 선택하고 Azure 구독 생성 절차를 완료합니다.

## SDK/CLI commands

온보딩 과정 자체에는 명령줄 입력이 필요 없지만, 크레딧이 활성화된 후에는 아래 도구를 설치해
추가 실습에 대비할 수 있습니다.

- **Azure CLI**: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`
- **Azure Developer CLI (azd)**: `curl -fsSL https://aka.ms/install-azd.sh | bash`
- **GitHub CLI**: `sudo apt install gh` 또는 [GitHub CLI 설치 가이드](https://cli.github.com/manual/installation) 참고

설치 후 `az login` 명령으로 브라우저 로그인을 수행하면 새 구독이 연동됩니다.

## Testing strategies

- **계정 충돌 검사**: Outlook/LinkedIn/Founders Hub가 모두 새 이메일로 연결되었는지 확인합니다.
- **Azure 포털 확인**: `portal.azure.com` 접속 후 우측 상단 배너와 `비용 관리 + 청구` → `결제 방법` 페이지에서 크레딧을 검증합니다.
- **시간 지연 대응**: 크레딧 금액이 보이지 않을 경우 30~60분 대기 후 새로고침하고, 그래도 표시되지 않으면 Founders Hub를 다시 방문해 혜택을 재실행합니다.
- **GitHub Codespaces 리허설**: 전용 GitHub 계정을 만들었다면, 빈 리포지토리에서 Codespaces를 생성해 계정 권한이 정상인지 확인합니다.
