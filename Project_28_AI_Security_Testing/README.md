# Project 28: AI Security Testing Assistant

## Overview

Security testing requires specialized knowledge that many QA teams lack. This project builds an AI-powered security testing assistant that generates security test cases, crafts targeted payloads, analyzes scanner results, and tests for prompt injection vulnerabilities in LLM-powered features. It bridges the gap between QA engineers and security specialists by making security testing accessible through natural language prompts.

---

## Objective

Build a Python-based AI security testing toolkit that generates context-aware security test cases for web applications, produces targeted XSS/SQLi payloads, integrates with OWASP ZAP for automated scanning, analyzes scan results with AI for actionable insights, tests LLM features for prompt injection vulnerabilities, and generates professional security reports.

---

## Tech Stack

| Tool / Library | Purpose |
|----------------|---------|
| Python 3.10+ | Core language |
| LangChain | LLM orchestration for security analysis |
| OpenAI API | Security test generation and result analysis |
| OWASP ZAP (API) | Automated security scanning |
| Playwright | Browser-based security testing |
| Requests | HTTP-level payload delivery |
| Jinja2 | Security report templating |
| Burp Suite concepts | Proxy-based testing methodology |

---

## What You Will Learn

- OWASP Top 10 vulnerabilities and how to test for each
- Using LLMs to generate context-specific security test cases from application descriptions
- Crafting XSS payloads that bypass common sanitization (encoding, filter evasion)
- SQL injection testing strategies from basic to advanced (blind, time-based, UNION-based)
- Integrating OWASP ZAP API for automated scans with custom policies
- AI-powered analysis of scanner results to filter false positives and prioritize findings
- Prompt injection testing for applications with LLM-powered features (chatbots, search, summarizers)
- Indirect prompt injection and data exfiltration attack patterns
- Writing professional security test reports with severity ratings and remediation guidance
- Responsible disclosure principles and ethical testing boundaries

---

## Key Deliverables

1. **AI Security Test Case Generator** — Describe your application and get targeted security test cases mapped to OWASP Top 10
2. **XSS/SQLi Payload Generator** — Context-aware payload generation that considers the target's technology stack and known defenses
3. **ZAP Integration Layer** — Python wrapper around OWASP ZAP API for automated scanning with custom scan policies
4. **AI Scanner Result Analyzer** — LLM analyzes ZAP/scanner output to eliminate false positives and provide clear remediation steps
5. **Prompt Injection Test Suite** — Comprehensive tests for LLM-powered features: direct injection, indirect injection, jailbreaking, data exfiltration
6. **Security Report Generator** — Professional HTML/PDF report with executive summary, detailed findings, severity ratings, and fix recommendations

---

## Project Structure

```text
Project_28_AI_Security_Testing/
├── README.md
├── requirements.txt
├── config/
│   ├── settings.yaml
│   └── zap_scan_policy.yaml
├── src/
│   ├── __init__.py
│   ├── test_case_generator.py
│   ├── payload_generator.py
│   ├── xss_tester.py
│   ├── sqli_tester.py
│   ├── zap_integration.py
│   ├── result_analyzer.py
│   ├── prompt_injection_tester.py
│   ├── llm_chain.py
│   └── report_generator.py
├── payloads/
│   ├── xss_payloads.json
│   ├── sqli_payloads.json
│   └── prompt_injection_payloads.json
├── templates/
│   └── security_report.html
├── sample_app/
│   ├── __init__.py
│   ├── vulnerable_app.py
│   └── llm_feature.py
├── tests/
│   ├── test_payload_generator.py
│   ├── test_zap_integration.py
│   ├── test_prompt_injection.py
│   └── test_report.py
└── reports/
    └── .gitkeep
```

---

## Getting Started

1. **Clone the repository and navigate to the project folder**
   ```bash
   cd Project_28_AI_Security_Testing
   ```

2. **Create and activate a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   playwright install chromium
   ```

4. **Set your API keys**
   ```bash
   export OPENAI_API_KEY="your-key-here"
   ```

5. **Start OWASP ZAP in daemon mode** (requires ZAP installed separately)
   ```bash
   zap.sh -daemon -port 8080 -config api.key=your-zap-api-key
   ```

6. **Start the sample vulnerable application**
   ```bash
   python sample_app/vulnerable_app.py
   ```

7. **Generate security test cases for the sample app**
   ```bash
   python src/test_case_generator.py --app-url http://localhost:5000 --description "E-commerce app with user login, product search, and checkout"
   ```

8. **Run XSS payload testing**
   ```bash
   python src/xss_tester.py --target http://localhost:5000 --endpoints /search,/comment
   ```

9. **Run the ZAP automated scan with AI analysis**
   ```bash
   python src/zap_integration.py --target http://localhost:5000 --analyze
   ```

10. **Test prompt injection on LLM features**
    ```bash
    python src/prompt_injection_tester.py --target http://localhost:5000/chat --suite payloads/prompt_injection_payloads.json
    ```

11. **Generate the security report**
    ```bash
    python src/report_generator.py --results reports/ --output reports/security_report.html
    ```

---

## QA Angle

Security testing is increasingly expected of QA engineers, not just dedicated security teams. This project makes that transition practical:

- **Lower the barrier to security testing** — You do not need to memorize payload databases or vulnerability taxonomies. Describe the feature, and the AI generates relevant security tests.
- **Move beyond "run a scanner and hope"** — AI analysis of scanner results eliminates the noise of false positives and provides clear, developer-friendly remediation steps instead of cryptic CVE references.
- **Test the new attack surface** — Applications with LLM-powered features (chatbots, AI search, summarizers) introduce prompt injection as a new vulnerability class. This project provides a structured approach to testing it.
- **Generate professional reports** — Security findings need to be communicated clearly to developers and management. The AI report generator produces actionable reports with severity ratings and prioritized fix recommendations.
- **Build security into the QA process** — Instead of treating security as a separate phase, these tools integrate into your existing test workflow. Run them alongside functional tests to catch vulnerabilities early.

This project is essential for QA engineers working on applications that handle user data, process payments, or integrate LLM features — which increasingly means every application.

---

## Learning Companion Structure

This project now also includes a teaching-friendly folder structure for guided study:

```text
Project_28_AI_Security_Testing/
├── 01_Learning/
├── 02_Exercises/
├── 03_Interview_Questions/
```

### What to Use Each Folder For

- `01_Learning` — topic summary, learning goals, QA/SDET framing, and a concept diagram
- `02_Exercises` — guided practice tasks that students can use before implementation
- `03_Interview_Questions` — QA/SDET-oriented interview prep tied to the same topic

Recommended order:

1. Start with `01_Learning`
2. Work through `02_Exercises`
3. Review `03_Interview_Questions`
4. Return to the implementation assets in the rest of the project
