# Security Policy

## Reporting Security Issues

**Please do not report security vulnerabilities through public GitHub issues.**

If you discover a security vulnerability in this repository, please report it to us privately. We take all security vulnerabilities seriously and will respond promptly.

### How to Report

To report a security vulnerability, please send an email to:

📧 **[opencode@microsoft.com](mailto:opencode@microsoft.com)**

Please include the following information in your report:

- Type of issue (e.g., buffer overflow, SQL injection, cross-site scripting, etc.)
- Full paths of source file(s) related to the manifestation of the issue
- The location of the affected source code (tag/branch/commit or direct URL)
- Any special configuration required to reproduce the issue
- Step-by-step instructions to reproduce the issue
- Proof-of-concept or exploit code (if possible)
- Impact of the issue, including how an attacker might exploit it

This information will help us triage your report more quickly.

### What to Expect

- We will acknowledge receipt of your vulnerability report within 48 hours
- We will send a more detailed response within 7 days indicating the next steps
- We will keep you informed of the progress towards a fix and announcement
- We may ask for additional information or guidance

## Security Best Practices for Workshop Users

This workshop is designed for **learning and demonstration purposes**. Before deploying any code or infrastructure to production, please follow these security best practices:

### 1. Secrets Management

**❌ DON'T:**
- Hard-code API keys, passwords, or connection strings in code
- Commit secrets to Git repositories
- Share credentials in documentation or comments

**✅ DO:**
- Use [Azure Key Vault](https://azure.microsoft.com/services/key-vault/) for secret management
- Use [GitHub Secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets) for CI/CD workflows
- Use [Managed Identities](https://learn.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview) when possible
- Rotate credentials regularly

### 2. Authentication & Authorization

**✅ DO:**
- Implement proper authentication (Azure AD, Azure AD B2C)
- Use Role-Based Access Control (RBAC)
- Enable Multi-Factor Authentication (MFA)
- Follow the principle of least privilege

### 3. Network Security

**✅ DO:**
- Use Private Endpoints for Azure services
- Configure Network Security Groups (NSGs)
- Enable Azure Firewall or Web Application Firewall (WAF)
- Use HTTPS/TLS for all communications

### 4. Data Protection

**✅ DO:**
- Enable encryption at rest and in transit
- Use Azure Private Link for data access
- Implement proper data backup and recovery
- Follow data residency and compliance requirements

### 5. Monitoring & Logging

**✅ DO:**
- Enable [Azure Monitor](https://azure.microsoft.com/services/monitor/)
- Use [Application Insights](https://azure.microsoft.com/services/monitor/#features)
- Set up alerts for suspicious activities
- Review logs regularly

### 6. Dependency Management

**✅ DO:**
- Keep dependencies up to date
- Use Dependabot for automated security updates
- Scan for vulnerabilities regularly (e.g., with `pip-audit`, `npm audit`)
- Review security advisories

### 7. Azure-Specific Security

**✅ DO:**
- Enable [Microsoft Defender for Cloud](https://azure.microsoft.com/services/defender-for-cloud/)
- Use [Azure Policy](https://azure.microsoft.com/services/azure-policy/) for compliance
- Enable [Azure DDoS Protection](https://azure.microsoft.com/services/ddos-protection/)
- Follow [Azure Security Baseline](https://learn.microsoft.com/security/benchmark/azure/)

## Azure AI Security Considerations

When working with Azure AI services in this workshop:

### Content Safety
- Implement content filtering for user inputs and AI outputs
- Use [Azure AI Content Safety](https://azure.microsoft.com/products/ai-services/ai-content-safety)
- Monitor for prompt injection attacks
- Validate and sanitize all user inputs

### Data Privacy
- Don't send sensitive or personal information to AI models without proper controls
- Understand data residency requirements for your region
- Review [Azure OpenAI data privacy](https://learn.microsoft.com/azure/ai-services/openai/how-to/data-privacy)
- Consider using customer-managed keys

### Model Security
- Use private endpoints for AI service access
- Implement rate limiting and quotas
- Monitor usage patterns for anomalies
- Keep API keys secure and rotate regularly

## Known Limitations

⚠️ **Important**: This workshop includes preview features that may have security limitations:

- Some Azure AI features are in preview and not recommended for production
- Sample code prioritizes clarity over security hardening
- Default configurations may not meet enterprise security requirements

## Resources

### Microsoft Security Documentation
- [Azure Security Documentation](https://learn.microsoft.com/azure/security/)
- [Azure AI Security Best Practices](https://learn.microsoft.com/azure/developer/ai/get-started-securing-your-ai-app)
- [Microsoft Security Response Center (MSRC)](https://www.microsoft.com/msrc)

### Security Tools
- [Microsoft Defender for Cloud](https://azure.microsoft.com/services/defender-for-cloud/)
- [Azure Security Benchmark](https://learn.microsoft.com/security/benchmark/azure/)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)

### Community
- [Azure Security Community](https://techcommunity.microsoft.com/t5/azure-security/ct-p/AzureSecurity)
- [Microsoft Security Blog](https://www.microsoft.com/security/blog/)

## Disclaimer

This project is provided as-is for educational purposes. Users are responsible for implementing appropriate security measures in their own deployments. The maintainers are not liable for any security issues arising from the use of this code.

---

Thank you for helping keep this project and the community safe! 🔒
