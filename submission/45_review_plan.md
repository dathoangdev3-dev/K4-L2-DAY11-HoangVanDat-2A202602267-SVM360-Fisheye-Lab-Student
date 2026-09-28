# Kế hoạch review từ lỗi quan sát được

Từ `findings.csv` và `zone_table.md`, chọn **hai lát cắt của bài ADASIND một camera** cần review trước. Bảng này
giải thích dữ liệu thật bạn vừa làm; nó không thay cho kế hoạch bốn camera giả lập ở `45_sampling_plan.csv`.

| Lát cắt / frame | Số ca và loại lỗi | Vì sao review trước | Bằng chứng cần giữ |
|---|---|---|---|
| B2-edge / adasind_102750.jpg | MISSING SPURIOUS WRONG_CLASS | Nhiều khác biệt L/R/M và recall thấp hơn ở Truck | Ảnh gốc compare.html model_compare.html |
| B2-edge / adasind_082170.jpg | MISSING SPURIOUS | Có nhiều M_only và ca edge cần kiểm hình học | Ảnh gốc qa_overlay.html local_quality_conflicts.csv |

Giới hạn của kết luận từ ba frame ADASIND: chỉ là lát cắt nhỏ và không đại diện cho mọi camera thời tiết khoảng cách hay chuyển động.

## Chuyển sang kế hoạch bốn camera giả lập

Cách soát độ phủ của 200 frame ở `45_sampling_plan.csv` (kể cả tránh đếm nhiều frame liền nhau trong cùng cảnh
như nhiều ca độc lập), và vì sao kế hoạch đó chỉ giúp tìm ca cần soi, chưa đo được tỷ lệ lỗi: kiểm đủ bốn camera và hai mức normal/hard rồi chọn frame cách nhau theo cảnh; kế hoạch giúp phân bổ việc soi nhưng chưa phải mẫu ngẫu nhiên có ground truth nên không ước lượng được tỷ lệ lỗi.
