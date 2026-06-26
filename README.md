stateDiagram-v2
    [*] --> TonKho : Tạo mới / Nhập kho
    TonKho --> DangSuDung : Bàn giao cho nhân viên
    DangSuDung --> ChoSuaChua : Báo hỏng
    ChoSuaChua --> DangSuDung : Sửa thành công
    ChoSuaChua --> ChoThanhLy : Không thể sửa
    TonKho --> DaThanhLy : Thanh lý / Tiêu hủy
    ChoThanhLy --> DaThanhLy : Thanh lý / Tiêu hủy
    DaThanhLy --> [*]

    TonKho : Tồn kho (In Stock)
    DangSuDung : Đang sử dụng (In Use)
    ChoSuaChua : Chờ sửa chữa (Pending Repair)
    ChoThanhLy : Chờ thanh lý (Pending Liquidation)
    DaThanhLy : Đã thanh lý (Liquidated)
