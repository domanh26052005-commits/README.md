## 1.1 Context Diagram

Hệ thống Quản lý Đào tạo Nội bộ là giải pháp phần mềm được xây dựng nhằm hỗ trợ Ban đào tạo tại Công ty VIVAS tổ chức, quản lý và tối ưu hóa các hoạt động đào tạo nội bộ. Hệ thống kết nối đồng bộ với hệ thống quản lý nhân sự có sẵn (AIO) nhằm tự động hóa việc đồng bộ dữ liệu nhân viên và thông tin đăng nhập. Sơ đồ ngữ cảnh dưới đây minh họa các thực thể bên ngoài (External Entities) và các dòng dữ liệu tương tác với hệ thống cho phiên bản phát hành đầu tiên, đảm bảo tính phân quyền và bảo mật dữ liệu theo phạm vi phụ trách.

```mermaid
graph TD
    %% Central System
    VIVAS_TMS((Hệ thống QL Đào tạo Nội bộ))

    %% External Entities
    AIO[Hệ thống Nhân sự AIO]
    Admin[Người quản trị ứng dụng]
    TStaff[Nhân viên đào tạo]
    Head[Trưởng ban đào tạo]
    Manager[Quản lý phòng ban]
    Emp[Nhân viên]
    Comms[Nhân viên truyền thông nội bộ]

    %% Data Flows
    AIO -->|Thông tin nhân viên & Tài khoản đăng nhập| VIVAS_TMS
    
    Admin -->|Thông tin phân quyền & Cấu hình danh mục loại| VIVAS_TMS
    
    TStaff -->|Dữ liệu khóa học, Bài kiểm tra, Danh sách gán| VIVAS_TMS
    
    Head -->|Lệnh duyệt khóa học/bài thi, Yêu cầu báo cáo| VIVAS_TMS
    VIVAS_TMS -->|Báo cáo thống kê tình hình học tập toàn công ty| Head
    
    Manager -->|Yêu cầu xem thông tin nhân viên thuộc phòng| VIVAS_TMS
    VIVAS_TMS -->|Tiến độ học tập & Điểm thi của phòng ban| Manager
    
    Emp -->|Yêu cầu học, Bài làm kiểm tra| VIVAS_TMS
    VIVAS_TMS -->|Nội dung bài giảng, Điểm thi, Tiến độ cá nhân| Emp
    
    Comms -->|Tin bài truyền thông, Quản lý bình luận/vote| VIVAS_TMS

    %% Style Adjustments
    style VIVAS_TMS fill:#f9f,stroke:#333,stroke-width:2px;
    style AIO fill:#fff,stroke:#333,stroke-width:1px;
    style Admin fill:#fff,stroke:#333,stroke-width:1px;
    style TStaff fill:#fff,stroke:#333,stroke-width:1px;
    style Head fill:#fff,stroke:#333,stroke-width:1px;
    style Manager fill:#fff,stroke:#333,stroke-width:1px;
    style Emp fill:#fff,stroke:#333,stroke-width:1px;
    style Comms fill:#fff,stroke:#333,stroke-width:1px;
