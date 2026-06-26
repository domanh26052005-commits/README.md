flowchart TD
    %% Định nghĩa các Style màu sắc giống trong ảnh
    classDef default fill:#fcfcfc,stroke:#ccc,stroke-width:1px,color:#333
    classDef systemNode fill:#d1c4e9,stroke:#9575cd,stroke-width:1px,color:#333
    classDef decisionNode fill:#ffe082,stroke:#ffb300,stroke-width:1px,color:#333
    classDef subgraphStyle fill:#fffde7,stroke:#c5e1a5,stroke-width:2px,color:#333

    %% Swimlane: Training Staff
    subgraph TS ["Training Staff"]
        A["Create Course & Test"]
        B["Assign to Employees/Dept"]
        C["Submit for Approval"]
        A --> B --> C
    end

    %% Swimlane: VIVAS System
    subgraph VIVAS ["VIVAS System"]
        D["Status: Pending"]:::systemNode
        E["Status: Published"]:::systemNode
        F["Auto-grade & Save Result"]:::systemNode
    end

    %% Swimlane: Head of Training
    subgraph HoT ["Head of Training"]
        G{"Approve?"}:::decisionNode
    end

    %% Swimlane: Employee
    subgraph EMP ["Employee"]
        H["Login via AIO"]
        I["Access Assigned Course"]
        J["Study Lectures Sequentially"]
        K["Take Final Test"]
        L["View Final Score"]
        
        H --> I --> J --> K
    end

    %% Swimlane: Managers & Head
    subgraph MGR ["Managers & Head"]
        M["View Progress & Reports"]
    end

    %% Các đường liên kết chéo giữa các Actor/System
    C --> D
    D --> G
    
    %% Các đường nhánh từ quyết định Approve
    G -- "Rejected" --> A
    G -- "Approved" --> E
    
    %% Đường rẽ nhánh đặc biệt
    A -- "Created by Head" --> E
    
    %% Tiếp tục luồng xử lý
    E --> H
    K --> F
    
    %% Từ hệ thống trả về kết quả
    F --> L
    F --> M

    %% Áp dụng style cho các khung subgraph (Tùy chọn hiển thị tùy nền tảng)
    style TS fill:#fffde7,stroke:#dce775,stroke-width:1px
    style VIVAS fill:#fffde7,stroke:#dce775,stroke-width:1px
    style HoT fill:#fffde7,stroke:#dce775,stroke-width:1px
    style EMP fill:#fffde7,stroke:#dce775,stroke-width:1px
    style MGR fill:#fffde7,stroke:#dce775,stroke-width:1px
