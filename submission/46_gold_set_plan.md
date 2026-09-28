# Đề xuất gold set theo camera — tình huống giả lập

**Đầu bài:** 50.000 frame từ bốn camera SVM, ngân sách chọn 200 frame để review/gold. Đây là tình huống trên slide,
**không phải** 50.000 frame có trong repo. Phân bổ đúng 200 ở `45_sampling_plan.csv` cho bốn camera, mỗi camera có
normal và hard slice. “Gold set” ở đây là **kế hoạch tạo** reference sau kiểm chứng, không phải teaching reference
ADASIND hoặc nhãn bạn vừa vẽ. Nếu cần, dùng `notebooks/day11-svm360-colab.ipynb` để thử tổng phân bổ; notebook
không làm thay phần lý do.

| camera_id | Hard case cần chọn | Vì sao dễ sai | Annotation space / calibration cần giữ | Cách review trước khi gọi là gold |
|---|---|---|---|---|
| front | Vật ở mép kính, vật vừa xuất hiện/không rõ thân, và đối tượng sát góc trước xe | Vùng mép có méo fisheye mạnh, dễ làm hỏng bề mặt box và xác định class | Giữ vùng nhìn hợp lệ, không ép vẽ box ở mép không thấy rõ; giữ calibration và khung nhìn constante | Review độc lập trên 2 người, ưu tiên hard case và so với vùng ignore đã xác định |
| rear | Vật bị che bởi góc xe, trụ, hoặc bị bóng đen | Tỉ lệ occlusion cao, nằm gần đường viền dưới/hai bên | Không dùng vùng mờ làm annotation space; giữ rõ vùng thân xe và lens border | Chọn ít nhất một frame có occlusion, một frame không che và so sánh mối tương quan |
| left | Vật sát thành xe và đối tượng nhỏ nằm ngang | Có nguy cơ nhầm giữa người, xe ba bánh và vật cản do layout hông | Giữ khu vực hông xe và vùng chồng phải phân biệt rõ ràng | Dùng peer agreement và kiểm lại `ignore_region` và `ego_body` trước khi ký gold |
| right | Hình ảnh sát mép và chồng với vùng not-in-view | Khó nhận diện do góc biển và méo ở cạnh phải | Chỉ giữ phần vật thực sự nhìn thấy; không “fill” bằng cách kéo box quá mép | Review theo cả class và geometry, không chỉ một mẫu dễ nhất |

- Khi nào cần refresh gold set (đổi camera, calibration hoặc rule): Khi thay đổi góc gắn camera, thay đổi hệ số distortion hoặc các nguyên tắc ignore/ego body; khi rule mới làm ảnh hưởng đến vùng hợp lệ hoặc tracking seam; khi có thêm dữ liệu từ một camera chưa đại diện rõ.
- Một ca seam/cross-camera cần policy và evidence trước khi ghép hai box: Khi một vật xuất hiện ở vùng chồng của hai camera nhưng thiếu timestamp hoặc calibration; chỉ ghép khi có cùng vật, cùng thời điểm và cùng rule output, không chỉ theo vị trí gần nhau.
- Vì sao peer agreement hoặc quality report trên ảnh một camera chưa chứng minh gold set đúng cho cả bốn camera: Vì gold set phải bao phủ sự đa dạng của bốn camera, các tần suất occlusion, mép kính và seam khác nhau; một camera riêng không thể đại diện cho toàn hệ thống 360°.
