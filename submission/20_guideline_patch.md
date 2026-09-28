# Guideline patch

- **Rule mới đề xuất:** Ở vùng edge phải kiểm tra box theo phần nhìn thấy trên ảnh gốc trước khi quyết định giữ box nhỏ hoặc gắn `truncated`.
- **Áp dụng cho:** sáu class động và attribute `truncated` ở zone edge.
- **Vì sao luật hiện tại (`docs/02-rules-vi.md`) không đủ:** Luật hiện tại nêu box bám phần nhìn thấy nhưng chưa có bước kiểm tra riêng cho biến dạng và cắt vật ở rìa fisheye.
- **`rules_version` mới:** v1.1.0
- **Hiệu lực từ:** r1_craft sau khi QA xác nhận patch.
