# Architecture

```mermaid
flowchart TD
 UI[Local browser dashboard] --> API[Node HTTP server: validation and single-run gate]
 API --> CEO --> Researcher --> Developer --> Marketer --> QA --> Final[CEO synthesis]
 CEO & Researcher & Developer & Marketer & QA & Final --> Router[Role-based routing and fallback]
 Router --> OR[OpenRouter API]
 Router --> Logs[Local NDJSON telemetry]
 API --> UI
```

Each stage receives previous reports as untrusted data. Models are sequential, not autonomous tool users. The router selects distinct free candidates and escalates budgets (1600, 3000, 4500, 6000). Failed stages are represented in subsequent context. Responses stream as NDJSON events; browser renders text rather than HTML. API key stays server-side. No independent web research or code execution.

```mermaid
sequenceDiagram
 participant B as Browser
 participant S as Server
 participant O as OpenRouter
 B->>S: POST /run (JSON)
 loop Six stages
 S-->>B: working
 S->>O: Preferred model
 alt Failure or truncated output
 O-->>S: Error
 S-->>B: Attempt telemetry
 S->>O: Alternate model and higher budget
 end
 O-->>S: Response and optional usage
 S-->>B: Stage result
 end
 S-->>B: Completion summary
```
