# Hands-on Labs for Startups using Microsoft Azure & Azure AI

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub Pages](https://img.shields.io/badge/docs-GitHub%20Pages-blue)](https://asomi7007.github.io/Hands-on-labs-for-startups-using-Microsoft-Azure-Azure-AI/)
[![MkDocs](https://img.shields.io/badge/built%20with-MkDocs-green)](https://www.mkdocs.org/)

스타트업을 위한 Microsoft Azure 및 Azure AI 핸즈온 워크샵 시리즈입니다. 이 워크샵을 통해 Azure의 핵심 서비스와 AI 기능을 실제로 구현하고 배포하는 방법을 배울 수 있습니다.

> **워크샵 문서**: [https://asomi7007.github.io/Hands-on-labs-for-startups-using-Microsoft-Azure-Azure-AI/](https://asomi7007.github.io/Hands-on-labs-for-startups-using-Microsoft-Azure-Azure-AI/)

---

## 📚 Workshop Overview

스타트업 개발자와 엔지니어를 위한 실전 중심의 Azure & Azure AI 핸즈온 워크샵입니다. Azure 크레딧을 효율적으로 활용하여 AI 에이전트부터 풀스택 웹 애플리케이션까지 실제 프로덕션 환경을 구축하는 방법을 배웁니다.

### What you will learn

이 워크샵을 통해 다음을 배우게 됩니다:

- **Microsoft for Startups 활용**: Founders Hub에서 $1,000 Azure 크레딧 받기
- **WordPress + AI 챗봇 구축**: Azure Marketplace 배포, Azure AI 에이전트 통합
- **세일즈 AI 에이전트**: Contoso Sales Assistant로 RAG 기반 고객 응대 시스템 구현
- **정적 웹사이트 배포**: Azure Static Web Apps로 GitHub 자동 배포 파이프라인 구축
- **실시간 협업 앱 개발**: WebSocket 기반 Affinity Diagram 보드, Docker 컨테이너화, Azure Container Apps 배포

---

## 📖 Workshop Guide

워크샵을 시작하려면 아래 링크에서 전체 가이드를 확인하세요:

**👉 [Hands-on Labs 워크샵 가이드 보기](https://asomi7007.github.io/Hands-on-labs-for-startups-using-Microsoft-Azure-Azure-AI/)**

워크샵 가이드에는 다음 내용이 포함되어 있습니다:

- 📝 5개 Lab의 상세한 단계별 실습 가이드
- 🎯 각 Lab의 학습 목표 및 예상 소요 시간
- 💻 코드 예제 및 스크린샷
- 🔧 트러블슈팅 가이드 및 FAQ
- 🔗 추가 학습 자료 및 참고 문서

---

## 🎯 Workshop Labs Overview

| Lab | 주제 | 핵심 기술 |
|-----|------|----------|
| **Lab 1** | Microsoft for Startups Founders Hub & Azure 크레딧 받기 | Microsoft 계정, LinkedIn, $1,000 크레딧 |
| **Lab 2** | Azure Marketplace에서 WordPress 홈페이지 구축 | 도메인 구매, WordPress, Azure AI 에이전트, 챗봇 통합 |
| **Lab 3** | Contoso Sales Assistant 사용해보기 | 샘플 에이전트, 시스템 프롬프트, RAG, 세일즈 Q&A |
| **Lab 4** | Static Web Apps Azure 배포 | GitHub 연동, Static Web Apps, PR 미리보기 |
| **Lab 5** | Affinity Diagram Web App - 실시간 협업 보드 만들기 | GitHub Codespaces, React+FastAPI, WebSocket, Docker, Container Apps |

> 💡 각 Lab의 자세한 내용은 [워크샵 가이드](https://asomi7007.github.io/Hands-on-labs-for-startups-using-Microsoft-Azure-Azure-AI/)를 참고하세요.

---

## � Prerequisites

이 워크샵을 진행하기 위해 필요한 준비사항:

1. **Azure 계정**: 무료 계정 생성 ([Lab 1 가이드](https://asomi7007.github.io/Hands-on-labs-for-startups-using-Microsoft-Azure-Azure-AI/lab1/) 참고)
2. **GitHub 계정**: 저장소 포크 및 GitHub Codespaces 사용
3. **기본 지식**: 
   - Python 또는 JavaScript 기본 문법
   - Git 및 터미널 기본 사용법
   - (선택) 클라우드 서비스에 대한 기본 이해

> 💰 **Azure 크레딧**: Lab 1에서 스타트업을 위한 무료 Azure 크레딧을 받는 방법을 안내합니다. 전체 워크샵 진행에 필요한 비용은 약 $1 미만입니다.

---

## 📂 Repository Structure

```
.
├── docs/                      # 워크샵 문서 (MkDocs)
│   ├── lab1/                 # Lab 1: Microsoft for Startups Founders Hub & Azure 크레딧
│   ├── lab2/                 # Lab 2: WordPress 홈페이지 구축
│   ├── lab3/                 # Lab 3: Contoso Sales Assistant
│   ├── lab4/                 # Lab 4: Static Web Apps 배포
│   ├── lab5/                 # Lab 5: Affinity Diagram 실시간 협업 보드
│   ├── css/                  # 커스텀 스타일
│   ├── js/                   # 커스텀 스크립트
│   └── media/                # 이미지 및 미디어
├── .github/
│   └── workflows/
│       └── deploy.yml        # GitHub Pages 자동 배포
├── mkdocs.yml                # MkDocs 설정
├── requirements.txt          # Python 의존성
├── LICENSE                   # MIT 라이선스
├── CODE_OF_CONDUCT.md        # 행동 강령
├── CONTRIBUTING.md           # 기여 가이드라인
├── SECURITY.md               # 보안 정책
├── CHANGELOG.md              # 변경 이력
└── README.md                 # 이 파일
```

워크샵 문서 수정에 대한 자세한 내용은 [CONTRIBUTING.md](CONTRIBUTING.md)를 참고하세요.

---

## � Important Security Notice

이 워크샵의 샘플 코드와 설정은 **학습 및 데모 목적**으로 제작되었습니다. Microsoft는 이 코드를 프로덕션 환경에 배포하기 전에 추가 보안 기능을 구현하거나 활성화할 것을 강력히 권장합니다.

프로덕션 배포 시 고려해야 할 보안 권장사항:

- ✅ Azure Key Vault를 사용한 비밀키 관리
- ✅ Managed Identity 및 RBAC 구성
- ✅ 네트워크 보안 (NSG, Private Endpoints, WAF)
- ✅ Application Insights 모니터링 및 경고 설정
- ✅ 정기적인 보안 패치 및 업데이트

자세한 보안 가이드는 [SECURITY.md](SECURITY.md) 및 [Azure AI 보안 모범 사례](https://learn.microsoft.com/azure/developer/ai/get-started-securing-your-ai-app)를 참고하세요.

> ⚠️ **경고**: 이 저장소의 일부 기능은 미리보기(Preview) 상태입니다. 미리보기 버전은 서비스 수준 계약 없이 제공되며 프로덕션 워크로드에는 권장되지 않습니다. 자세한 내용은 [Microsoft Azure 미리보기 추가 사용 약관](https://azure.microsoft.com/support/legal/preview-supplemental-terms/)을 참조하세요.

---

## 🤝 Contributing

워크샵 개선을 위한 여러분의 의견과 제안을 환영합니다! 문제를 발견하거나 개선사항이 있다면 이 저장소에 Issue로 제보해 주세요.

이 프로젝트는 기여와 제안을 환영합니다. 대부분의 기여는 기여자가 기여를 사용할 권리를 부여한다는 것을 선언하는 기여자 라이선스 계약(CLA)에 동의해야 합니다. 자세한 내용은 [https://cla.opensource.microsoft.com](https://cla.opensource.microsoft.com)을 방문하세요.

Pull Request를 제출하면 CLA 봇이 자동으로 CLA 제공 여부를 결정하고 PR을 적절히 장식합니다(예: 상태 확인, 댓글). 봇이 제공하는 지침을 따르기만 하면 됩니다. CLA를 사용하는 모든 저장소에서 한 번만 수행하면 됩니다.

이 프로젝트는 [Microsoft 오픈 소스 행동 강령](https://opensource.microsoft.com/codeofconduct/)을 채택했습니다. 자세한 내용은 [행동 강령 FAQ](https://opensource.microsoft.com/codeofconduct/faq/)를 참조하거나 추가 질문이나 의견이 있는 경우 [opencode@microsoft.com](mailto:opencode@microsoft.com)으로 문의하세요.

자세한 기여 가이드라인은 [CONTRIBUTING.md](CONTRIBUTING.md)를 참고하세요.

---

## � Additional Resources

- **Azure 공식 문서**: [Azure Documentation](https://docs.microsoft.com/azure/)
- **Azure AI Foundry**: [Azure AI Studio](https://learn.microsoft.com/azure/ai-studio/)
- **Microsoft Learn**: [Azure 학습 경로](https://learn.microsoft.com/training/azure/)
- **커뮤니티**: [Azure Tech Community](https://techcommunity.microsoft.com/t5/azure/ct-p/Azure)

---

## 📄 License

이 프로젝트는 MIT 라이선스를 따릅니다. 자세한 내용은 [LICENSE](LICENSE) 파일을 참고하세요.

---

## �️ Trademarks

이 프로젝트에는 프로젝트, 제품 또는 서비스에 대한 상표 또는 로고가 포함될 수 있습니다. Microsoft 상표 또는 로고의 승인된 사용은 [Microsoft의 상표 및 브랜드 가이드라인](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general)을 준수해야 합니다. 이 프로젝트의 수정된 버전에서 Microsoft 상표 또는 로고를 사용하는 경우 혼란을 야기하거나 Microsoft의 후원을 암시해서는 안 됩니다. 제3자 상표 또는 로고의 사용은 해당 제3자의 정책을 따릅니다.

---

**Happy Learning! 🚀**
