```mermaid
    graph TD;
        A[Client] --> B[Load Balancer];
        B --> C[API Server];
        C --> D[Service 1];
        C --> E[Service 2];
        D --> F[Database];
        E --> F;
```