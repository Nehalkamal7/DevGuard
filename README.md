

# DevGuard AI — Code Security Intelligence

A browser-based Python code security analysis prototype.

## Features
- Rule-based detection of risky Python patterns.
- Line-level findings with severity classification.
- Risk scoring and filtering.
- Actionable remediation recommendations.
- Exportable JSON security reports.
- Local browser-side analysis without uploading source code.

## Technical Approach
The current version uses a custom heuristic rule engine written in JavaScript. It analyzes Python syntax patterns for common vulnerabilities (eval/exec, SQL injection, hardcoded secrets, unsafe deserialization, insecure subprocessing).

## Roadmap
- Python AST-based deep syntax analysis.
- Integration with Bandit & custom security rules.
- Free Hugging Face Serverless Inference API integration for AI remediation.
