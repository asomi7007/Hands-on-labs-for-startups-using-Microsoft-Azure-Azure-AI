# Azure AI Foundry 에이전트 생성

## 목표
- Azure AI Foundry에서 **에이전트**를 만들고 RAG/툴 설정

## 준비물
- 리소스 그룹 / 지역
- 모델(예: GPT 계열) 사용 가능 지역/할당량
- 스토리지/인덱스(RAG) 준비

## 단계
1. Azure AI Foundry → 새 에이전트 생성
2. **System Prompt** 와 **Tools**(Function, Webhook 등) 정의
3. **Knowledge / Index** 연결(RAG)
4. 배포(Endpoint) 및 **키/엔드포인트** 발급

```bash
# 예시: 환경 변수
export AZURE_AI_ENDPOINT="https://<your-ai-endpoint>.azure.com/"
export AZURE_AI_KEY="<your-key>"
```
