# AgentCorp AI 3.0

Fault-tolerant local multi-model orchestration prototype built with Node.js, vanilla JavaScript and OpenRouter. Five simulated business roles share sequential reports, followed by a CEO synthesis stage.

## Highlights
- Role-aware free-model routing and distinct fallbacks
- Adaptive generation budgets and requested low reasoning effort
- Streaming NDJSON telemetry, JSON report export and local rotating logs
- Graceful stage failure recovery and a final executive summary

## Quick start (Windows PowerShell)
Requires Node.js 22 or newer. No external npm dependencies.

```powershell
npm test
$env:PORT = '4318'
node server.js
```
Open http://127.0.0.1:4318 and select Demo for scripted outputs. For live mode, stop the server and enter your OpenRouter key privately:

```powershell
$secret = Read-Host 'OpenRouter API key' -AsSecureString
$env:OPENROUTER_API_KEY = [System.Net.NetworkCredential]::new('', $secret).Password
node server.js
```
Never commit keys. Free model availability varies. Optional OPENROUTER_MODEL and OPENROUTER_MODEL_CEO, _RESEARCHER, _DEVELOPER, _MARKETER, _QA, _CEO_FINAL (with the full OPENROUTER_MODEL prefix) select free model IDs. Use the numeric localhost address, not localhost hostname.

## Observed benchmark
V3 completed six of six stages in 57.148 seconds, recovering three failed requests. Recorded tokens: 11230; reported cost $0 for seven metered attempts, two unmetered. Single development run before release hardening; not a controlled evaluation.

## Documentation
- [Architecture](docs/ARCHITECTURE.md)
- [Benchmark records](docs/BENCHMARKS.md)
- [Security and limitations](SECURITY.md)

## Limitations
Local only, no autonomous tool access or independent research. Model outputs require human review. Reasoning controls may be ignored. Goals and prior reports go to external providers. Do not expose the server publicly. Automated demo/security checks passed; live retest after local hardening pending.

## License
MIT. See [LICENSE](LICENSE).
