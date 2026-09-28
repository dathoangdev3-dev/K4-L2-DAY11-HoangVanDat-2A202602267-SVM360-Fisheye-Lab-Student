# Sensor context

- Rig: Đây là camera fisheye gắn trên xe, nhìn thẳng về phía trước/trước mặt xe, với vùng ảnh ở trung tâm rõ hơn và méo ở mép. Theo quan sát, camera đặt ở góc trên của thân xe, không phải camera ngoài trời; hình ảnh cho thấy bóng/đường viền đối tượng ở mép bị bóp méo do kính fisheye.
- `ego_body`: phần thân xe hiện ra ở cuối khung hình, chủ yếu ở vùng dưới cùng gần đáy ảnh: cản xe, mặt trước/đáy xe hoặc phần vỏ xe sát góc gầm. Trong các frame không thấy thân xe, không vẽ `ego_body`.
- Vòng kính (lens circle): là vùng tròn/đường khung méo ở mép ảnh, thường nằm gần rìa ngoài khung hình và làm mất một phần đối tượng ở viền. Khu vực này không phải vùng đánh dấu đối tượng chính, nên cần kiểm tra lại trước khi gán box hoặc ignore region.
- Mục đích quan sát: vì không có metadata rig đầy đủ, ta chỉ ghi theo quan sát trực tiếp trên ảnh và giữ phạm vi label trong vùng hợp lệ, không suy đoán quá mức về khoảng cách hay góc gắn camera.
