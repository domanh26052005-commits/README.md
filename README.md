stateDiagram-v2
    %% Định nghĩa các khối trạng thái
    state "Tồn kho (In Stock)" as TonKho
    state "Đang sử dụng (In Use)" as DangSuDung
    state "Chờ sửa chữa (Pending Repair)" as ChoSuaChua
    state "Chờ thanh lý (Pending Liquidation)" as ChoThanhLy
    state "Đã thanh lý (Liquidated)" as DaThanhLy

    %% Mũi tên thể hiện luồng chuyển trạng thái
    [*] --> TonKho : Nhập mới tài sản vào kho
    TonKho --> DangSuDung : Cấp phát cho nhân viên
    DangSuDung --> TonKho : Thu hồi tài sản
    DangSuDung --> ChoSuaChua : Nhân viên báo hỏng
    ChoSuaChua --> DangSuDung : Sửa chữa thành công
    ChoSuaChua --> ChoThanhLy : Hỏng nặng (Không thể sửa)
    TonKho --> ChoThanhLy : Tài sản cũ / Quá hạn
    ChoThanhLy --> DaThanhLy : Thực hiện thanh lý / Tiêu hủy
    DaThanhLy --> [*]
