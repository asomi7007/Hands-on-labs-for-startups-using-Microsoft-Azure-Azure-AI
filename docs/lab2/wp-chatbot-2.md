# WordPress 챗봇 통합 (2)

## 고급 통합
- 사용자 인증 연동(멤버십/포럼)
- 세션 컨텍스트 유지
- 대화 로그 수집/시각화

## 코드 스니펫 (Shortcode 예시)
```php
function azure_ai_chatbot() {
  return '<div id="azure-ai-chat"></div><script src="/wp-content/azure-ai-chat.js"></script>';
}
add_shortcode('azure_ai_chatbot', 'azure_ai_chatbot');
```
