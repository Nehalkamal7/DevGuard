# DevGuard AI — Automated Code Security & Vulnerability Diagnostics Engine

DevGuard AI is a hybrid static analysis and LLM-assisted code security diagnostic platform designed to detect runtime vulnerabilities, injection vectors, and insecure programming patterns in Python codebases.

## Architecture & Detection Pipeline

DevGuard combines two complementary layers of analysis:
1. **Deterministic Static Rule Engine:** High-throughput client-side heuristic engine scanning for Common Weakness Enumerations (CWEs) including CWE-89 (SQL Injection), CWE-78 (Command Injection via `shell=True`), CWE-502 (Insecure `pickle` Deserialization), and CWE-798 (Hardcoded Secrets).
2. **Generative Context Audit:** Deep semantic audit powered by Google Generative AI (Gemini 3.8 Flash) to detect contextual flaws across multi-line scopes, including path traversal (`os.path.join`), unprotected API endpoints, and production debug modes.
3. **Domain-Specific SLM (LoRA Adapter):** Fine-tuned `Qwen2.5-Coder-1.5B-Instruct` using 4-bit QLoRA on curated secure-coding instructions, hosted directly on the Hugging Face Hub.

## Key Features
- **Deterministic vs. Generative Auditing:** Dual-scan approach ensuring fast heuristic filtering followed by deep AST/contextual reasoning.
- **Line-Level Diagnostic Reports:** Pinpoints vulnerable lines with CWE mapping, risk severity classification (CRITICAL, HIGH, MEDIUM, LOW), and actionable remediation snippets.
- **Client-Side Privacy:** Executes static rules and interacts with LLM endpoints directly from the browser; sensitive keys remain in local storage.
- **JSON Audit Export:** Generates structured vulnerability reports for integration with CI/CD pipelines.

## Fine-Tuned Model Weights
The companion LoRA adapter trained for this project is available on Hugging Face:
- Model Hub: `https://huggingface.co/nehalkamal7/devguard-qwen-1.5b-security`

## Tech Stack
- **Frontend / Engine:** HTML5, CSS3 (Enterprise Dark UI), Vanilla JavaScript (ES6+)
- **LLM / APIs:** Google Gemini 3.8 Flash REST API
- **Model Fine-Tuning:** PyTorch, Hugging Face `transformers`, `peft` (QLoRA), `bitsandbytes`, `trl`
- **Deployment:** Hugging Face Spaces (Static SDK)

## Live Demo
Check out the live interactive space on Hugging Face: [DevGuard AI Live Space](https://huggingface.co/spaces/nehalkamal7/DevGuard-AI)
