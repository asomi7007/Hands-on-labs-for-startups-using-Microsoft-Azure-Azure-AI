# Lab 5 · Node.js 앱 GitHub → Azure 배포

## 목표
- App Service + GitHub Actions로 CI/CD 구성

## 예시 workflow.yaml
```yaml
name: Node CI/CD to Azure
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
      - run: npm ci && npm run build && npm test
      - name: 'Deploy to Azure Web App'
        uses: azure/webapps-deploy@v3
        with:
          app-name: YOUR_APP_NAME
          slot-name: production
          publish-profile: ${{ secrets.AZURE_PUBLISH_PROFILE }}
          package: .
```

## 체크리스트
- [ ] 빌드 성공
- [ ] 웹앱 배포 및 헬스체크 OK
