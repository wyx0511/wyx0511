graph TD;
    A[Input\n(Batch Size, Seq Len, Input Dim)] --> B{Is Seq Len == 1?}
    B -- Yes --> C[Unsqueeze to\n(Batch Size, Seq Len=1, Input Dim)]
    B -- No --> D[Seq Len > 1]
    C --> E[GRU Layer 1\n(Input Dim -> Hidden Size 16)]
    D --> E[GRU Layer 1\n(Input Dim -> Hidden Size 16)]
    E --> F[Output from GRU Layer 1\n(Batch Size, Seq Len, Hidden Size 16)]
    F --> G[Take Last Time Step\n(Batch Size, Hidden Size 16)]
    G --> H[Linear Layer\n(Hidden Size 16 -> Output Dim 1)]
    H --> I[Output Prediction\n(Batch Size, Output Dim)]
