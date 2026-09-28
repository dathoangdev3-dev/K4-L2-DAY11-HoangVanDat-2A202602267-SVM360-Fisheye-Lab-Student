# QA review · B2-edge

Mã khóa: E999-723D

Cold review trên bản khóa `final_b2_day11.zip` (ảnh gốc + `qa_overlay.html` + `docs/02-rules-vi.md`). Chưa dùng teaching reference khi ghi các dòng dưới.

| frame | object_ref | rule_id | nhận xét |
|---|---|---|---|
| adasind_069450.jpg | L5 | R01 | ThreeWheeler bên phải (xe/cart xanh) cao ≥40 px, nằm mid. Cần xác nhận đây có phải class động trong phạm vi hay stall tĩnh ngoài 6 class. |
| adasind_082170.jpg | L2 | R02 | Bike sát mép trái, `truncated=true`, box rất hẹp. Kiểm tra box có bám đúng phần nhìn thấy trên fisheye gốc hay đang cắt quá tay so với vật. |
| adasind_102750.jpg | L5 | R01 | ThreeWheeler nhỏ ở center. Kiểm tra có đủ H=40 và có nhầm với xe tải nhỏ phía trước (vật reference đánh Truck). |

Ghi finding r2_qa: cell=L_only, rule_id có giá trị, why để trống.
