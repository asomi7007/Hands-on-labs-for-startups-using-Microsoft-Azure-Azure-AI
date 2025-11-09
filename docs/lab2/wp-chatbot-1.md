# WordPress 챗봇 통합 (1)

## 목표
- 간단한 위젯/스니펫으로 챗봇 삽입

## 단계
1. WordPress 관리자 → **Appearance / Theme file editor** 혹은 헤더/푸터 스니펫 플러그인 사용
2. 아래 스니펫을 `<head>` 또는 `<body>` 끝에 삽입 후, 엔드포인트/키를 연동

```html
<script>
  window.azureAgent = {
    endpoint: "https://<your-ai-endpoint>/invoke",
    apiKey: "YOUR_PUBLIC_PROXY_KEY"
  };
</script>
<script src="https://cdn.example.com/azure-agent-widget.js"></script>
```

## 체크리스트
- [ ] 위젯 아이콘/패널 표시
- [ ] 기본 질의 응답 동작
