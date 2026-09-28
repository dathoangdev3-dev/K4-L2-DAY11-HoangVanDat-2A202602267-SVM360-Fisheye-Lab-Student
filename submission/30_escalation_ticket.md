# Escalation ticket

## Ticket 1

- **Frame:** adasind_102750.jpg
- **Ảnh chụp:** submission/screenshots/adasind_102750_model.png
- **Expected impact:** Model có nhiều box M_only ở mid; nếu dùng trực tiếp sẽ tăng false positive và làm lệch thống kê zone.
- **Owner:** ai_team
- **Recommendation:** Soi lại các box M_only trên ảnh gốc và bổ sung hard negative mid/edge trước khi dùng model để hỗ trợ prefill.
