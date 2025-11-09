# 도메인 구매

## 목표
- 커스텀 도메인 구매 및 DNS 레코드 설정

## 단계
1. 도메인 레지스트라(가비아/Namecheap/Cloudflare 등)에서 도메인 구매
2. Azure DNS 또는 레지스트라 DNS에서 A/CNAME/TXT(소유권) 레코드 구성
3. SSL/TLS 적용 (App Service 관리형 인증서 또는 Let's Encrypt)

## 체크리스트
- [ ] A/CNAME 레코드 정상
- [ ] `https://` 접속 가능
- [ ] 만료 알림 설정
