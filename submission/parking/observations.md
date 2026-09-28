# Quan sát vạch ô đỗ

- Hai vạch `parking_line` đã vẽ (mô tả vị trí trong ảnh): Hai đoạn sơn phân chia giữa các ô đỗ ở nửa trên và giữa ảnh, chạy dọc theo hướng gần như ngang/chéo theo mặt bằng bãi đỗ. Chúng là các vạch chia ô rõ ràng, không phải mép lối xe chạy chung.
- Một vạch/dấu sơn hoặc biên **không** vẽ, và vì sao: Không vẽ đường kẻ lớn ở giữa bãi hoặc mép đường dẫn xe chạy; nó là vạch dẫn lối xe hoặc biên vùng di chuyển, không phải vạch chia từng ô đỗ. Vạch đó không xác định ranh giới ô riêng mà chỉ định hướng di chuyển/lan can thô.
- Polygon `free_space` dừng ở đâu; có phần bị che nào không: Polygon được đặt ở phần mặt bãi trống nhìn thấy rõ, nằm giữa các vạch chia ô và không xuyên qua xe, cây, hoặc phần bị che khuất. Nó dừng ở mép trống thực tế nhìn thấy trên ảnh, không mở rộng sang vùng bị che.
- Ca chưa chắc cần hỏi người soát (nếu không có, ghi “không có”): Không có ca chưa chắc đáng báo; nếu có, cần hỏi lại về ranh giới chính xác của mép lối xe chạy với vạch ô đỗ ở vùng gần tâm ảnh.
