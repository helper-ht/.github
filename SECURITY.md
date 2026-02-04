# 🛡️ Security Policy: Helper 2026

At Helper 2026, the security of patient data and clinical records is our highest priority. This document outlines our security standards and how to report vulnerabilities.

## 🔒 Security Standards by Layer

### 1. Infrastructure (Terraform)
* **Secret Management:** Never hardcode credentials. Use Terraform's `random_password` provider for auto-generation or fetch secrets from a secure Vault/Secret Manager.
* **Least Privilege:** All IAM roles and security groups must follow the principle of least privilege.
* **State Security:** Terraform state files must be stored in encrypted remote backends with state locking enabled.

### 2. Backend (Spring Boot)
* **Data Access:** Ensure Row-Level Security (RLS) or specific filters so health professionals can only access data for patients who have granted permission.
* **Encryption:** All PII (Personally Identifiable Information) must be encrypted at rest and in transit (TLS 1.2+).
* **Validation:** Strict input validation using JSR-303/JSR-380 to prevent SQL injection and XSS.

### 3. Frontend (React)
* **Authentication:** Sessions must be managed via secure, HTTP-only cookies.
* **State Safety:** Never store sensitive clinical data in persistent local storage (localStorage). Use memory-only stores (Zustand) that clear on logout.



## 🛡️ Reporting a Vulnerability

If you discover a security vulnerability, please do NOT open a public issue. Instead, follow these steps:

1. **Private Disclosure:** Use the [GitHub Security Advisory](https://github.com/orgs/helper-ht/security/advisories/new) tool to report the finding privately.
2. **Details to Include:**
   - Description of the vulnerability.
   - Steps to reproduce.
   - Potential impact (e.g., data leak, unauthorized access).
3. **Response Time:** Our Tech Leadership team will acknowledge your report within 48 hours and provide a timeline for the fix.

## ⚖️ Compliance
All code must comply with **LGPD (Lei Geral de Proteção de Dados)**. Ensure that any feature involving patient data includes a clear audit log and a mechanism for data deletion/portability.

---
*Maintained by the Helper 2026 Security Team.*