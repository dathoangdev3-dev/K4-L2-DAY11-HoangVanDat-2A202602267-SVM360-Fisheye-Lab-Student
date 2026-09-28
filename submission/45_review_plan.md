# Kế hoạch review từ lỗi quan sát được

Từ `findings.csv` và `zone_table.md`, chọn **hai lát cắt của bài ADASIND một camera** cần review trước. Bảng này
giải thích dữ liệu thật bạn vừa làm; nó không thay cho kế hoạch bốn camera giả lập ở `45_sampling_plan.csv`.

| Lát cắt / frame | Số ca và loại lỗi | Vì sao review trước | Bằng chứng cần giữ |
|---|---|---|---|
| B2-edge / adasind_102750.jpg | WRONG_CLASS Truck/ThreeWheeler; L_only L5; RM_noL R5+M8 | Frame yếu nhất local-quality (accuracy 0.500); class Truck recall 0.333 | Ảnh gốc; r1_craft/compare.html; local_quality_conflicts.csv; screenshots/adasind_102750.png |
| B2-edge / adasind_082170.jpg | BOX_GEOMETRY L2+R5; nhiều M_only mid | IoU 0.5 tách một Bike mép trái thành L_only/R_only; model thừa 8 box mid | Ảnh gốc; model_compare.html; iou_sweep.md; screenshots/adasind_082170.png |

Giới hạn của kết luận từ ba frame ADASIND: chỉ là lát cắt nhỏ và không đại diện cho mọi camera thời tiết khoảng cách hay chuyển động.

## Chuyển sang kế hoạch bốn camera giả lập

Cách soát độ phủ của 200 frame ở `45_sampling_plan.csv` (kể cả tránh đếm nhiều frame liền nhau trong cùng cảnh
như nhiều ca độc lập), và vì sao kế hoạch đó chỉ giúp tìm ca cần soi, chưa đo được tỷ lệ lỗi: phân bổ đủ front/rear/left/right × normal/hard, chọn frame cách nhau theo cảnh chứ không lấy cụm liên tiếp; kế hoạch chỉ nêu chỗ cần review trước khi gọi gold, không phải mẫu ngẫu nhiên có ground truth nên không ước lượng tỷ lệ lỗi hệ SVM.
