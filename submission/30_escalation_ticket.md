# Escalation ticket

## Ticket 1

- **Frame:** adasind_102750.jpg
- **Ảnh chụp:** submission/screenshots/adasind_102750.png
- **object_ref:** L2+R2 (compare) / R2+M2 (model)
- **Expected impact:** Nếu copy class Truck từ teaching reference trong khi vật nhìn giống ThreeWheeler (hoặc ngược lại) sẽ vừa tạo WRONG_CLASS vừa lệch confusion Truck (recall 0.333 trên local-quality).
- **Owner:** guideline
- **Recommendation:** Lab Coach phân xử class cho xe mép trái bị cắt + lóa nắng; bổ sung ví dụ R04 (ThreeWheeler vs Truck nhỏ) trước khi dùng ca này trong gold set. Không lấy quyết định từ một mình model.

## Ticket 2

- **Frame:** adasind_082170.jpg
- **Ảnh chụp:** submission/screenshots/adasind_082170.png
- **object_ref:** M2 M5 M6 M7 M9
- **Expected impact:** Nhiều `M_only` ở mid làm prefill ồn; nếu tin model sẽ tăng FP khi gán nhãn.
- **Owner:** ai_team
- **Recommendation:** Soi hard negative mid/edge trên ảnh fisheye gốc; không kết luận domain shift từ một box.
