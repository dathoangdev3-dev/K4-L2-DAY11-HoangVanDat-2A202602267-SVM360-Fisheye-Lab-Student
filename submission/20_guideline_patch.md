# Guideline patch

- **Rule mới đề xuất:** Với xe mép fisheye bị cắt/lóa, không gán Truck chỉ vì thân hộp; cần thấy bánh/khung ba bánh hoặc cabin tải. Nếu không đọc được class, dùng `ignore_region` reason `unreadable` thay vì đoán. Box mép: bám phần nhìn thấy, chấp nhận IoU với reference < 0.5 mà không tự coi là thiếu.
- **Áp dụng cho:** `Truck` vs `ThreeWheeler` (R04) và `Bike` truncated ở zone edge (R02/R05).
- **Vì sao luật hiện tại (`docs/02-rules-vi.md`) không đủ:** R04 liệt kê ánh xạ nhưng không có phép phân xử khi chỉ thấy một góc xe cắt bởi vòng kính. Ca `adasind_102750.jpg` L2+R2 (IoU 0.909, lệch class) không khép được bằng luật hiện hành.
- **`rules_version` mới:** v1.1.0
- **Hiệu lực từ:** sau khi Lab Coach chốt ticket escalation frame 102750.
