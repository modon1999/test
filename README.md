flowchart LR
    U[User]
    B[bifrost proxy]

    subgraph VLLMCluster[Behind proxy: vLLM]
        A[vLLM on A100]
        I[vLLM on Immerse]
    end

    P[(Prometheus)]

    U -->|API requests| B
    B -->|Routes traffic| A
    B -->|Routes traffic| I

    A -->|/metrics| P
    I -->|/metrics| P
