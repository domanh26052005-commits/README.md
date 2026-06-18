### 1.2.4 Business Flow

This section illustrates the core business workflow of the VIVAS Internal Training Management System: **The Core Training Lifecycle (Creation, Approval, and Execution Flow)**. The swimlane flowchart below demonstrates how different actors interact sequentially to complete a full training cycle, strictly adhering to the company's operational rules such as mandatory approvals and sequential learning[cite: 1].

```mermaid
flowchart TD
    %% Swimlanes definition
    subgraph TStaff [Training Staff]
        A(Create Course & Test)
        B(Assign to Employees/Dept)
        C(Submit for Approval)
    end

    subgraph Head [Head of Training]
        D{Approve?}
    end

    subgraph Emp [Employee]
        F(Login via AIO)
        G(Access Assigned Course)
        H(Study Lectures Sequentially)
        I(Take Final Test)
        J(View Final Score)
    end

    subgraph Sys [VIVAS System]
        S1[Status: Pending]
        S2[Status: Published]
        S3[Auto-grade & Save Result]
    end

    subgraph Mgr [Managers & Head]
        K(View Progress & Reports)
    end

    %% Flow connections
    A --> B
    B --> C
    C --> S1
    S1 --> D
    D -->|Rejected| A
    D -->|Approved| S2
    
    %% Note: If Head creates the course, it bypasses approval
    A -.->|Created by Head| S2

    S2 --> F
    F --> G
    G --> H
    H --> I
    I --> S3
    S3 --> J
    S3 --> K

    %% Styling
    classDef process fill:#f9f9f9,stroke:#333,stroke-width:1px;
    classDef decision fill:#ffe6cc,stroke:#d79b00,stroke-width:2px;
    classDef system fill:#e1d5e7,stroke:#9673a6,stroke-width:2px;
    
    class A,B,C,F,G,H,I,J,K process;
    class D decision;
    class S1,S2,S3 system;
