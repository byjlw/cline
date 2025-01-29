# Architecture

```mermaid
graph TD
    A[Webview UI] <-->B[Cline Core]
    B-->C[Tool Chain]
    B-->D[Services]
    C-->E[Diff/Patch]
    C-->F[Terminal]  
    C-->G[Browser]
    C-->H[MCP]
    D-->I[File System]
    D-->J[Network]
    D-->K[Processes]
```

- **Webview UI**: User interface.
- **Cline Core**: Central controller.
- **Tool Chain**:
  - **Diff/Patch**: Virtual file editing with diffs and merging.
  - **Terminal**: Manages terminals for CLI execution. 
  - **Browser**: Interacts with web browsers.
  - **MCP**: Integrates external tools/services.
- **Services**:
  - **File System**: File operations.
  - **Network**: Network communication and APIs.
  - **Processes**: Spawns/manages external processes.
