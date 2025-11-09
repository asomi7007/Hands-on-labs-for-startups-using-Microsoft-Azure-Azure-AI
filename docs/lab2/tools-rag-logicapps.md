# Tool · RAG · Logic App 실습

## 목표
- 문서 색인 기반 RAG로 정확도 향상
- Logic Apps로 알림/후속 작업 자동화

## 예시 아키텍처
- WordPress 문의 → 에이전트 → RAG 조회 → 답변
- 특정 키워드 감지 시 Logic Apps로 티켓 생성/메일 발송

## 코드 예시 (요청 라우터)
```js
// Node.js Express 예시
app.post('/agent/invoke', async (req, res) => {
  const { message } = req.body;
  const answer = await agent.invoke({
    message,
    tools: ['search', 'kb'],
  });
  res.json({ answer });
});
```

## 체크리스트
- [ ] RAG 연결 테스트
- [ ] Logic Apps 트리거 작동
