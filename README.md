```mermaid
graph TD
    %% Central System
    COS((Cafeteria Ordering System))

    %% External Entities
    Patron[Patron]
    MM[Menu Manager]
    PS[Payroll System]
    CIS[Cafeteria Inventory System]
    MD[Meal Deliverer]
    CS[Cafeteria Staff]

    %% Data Flows
    Patron -->|meal order and meal changes| COS
    Patron -->|payroll deduction registration| COS
    COS -->|menu| Patron

    MM -->|menu contents| COS

    COS -->|payroll deduction registration request| PS
    PS -->|payroll deduction response| COS
    COS -->|payment request| PS

    COS -->|food item orders| CIS
    CIS -->|food item availability information| COS

    COS -->|delivery request| MD
    MD -->|delivery confirmation| COS

    COS -->|meal order| CS
    CS -->|delivery request| COS
    CS -->|meal status update| COS
    CS -->|payment request| COS

    %% Style Adjustments
    style COS fill:#f9f,stroke:#333,stroke-width:2px;
    style Patron fill:#fff,stroke:#333,stroke-width:1px;
    style MM fill:#fff,stroke:#333,stroke-width:1px;
    style PS fill:#fff,stroke:#333,stroke-width:1px;
    style CIS fill:#fff,stroke:#333,stroke-width:1px;
    style MD fill:#fff,stroke:#333,stroke-width:1px;
    style CS fill:#fff,stroke:#333,stroke-width:1px;
