# Exit ticket

Đọc `docs/10-svm360-reading-vi.md` trước khi trả lời câu 1–2. Các câu về zone, `why`, rework, parking và sampling
đã nằm trong file tương ứng nên không hỏi lại ở đây.

1. Một vật ở vùng seam giữa hai camera thật xuất hiện với hai box khác nhau: đó là lỗi `DUPLICATE` hay cần một quy
   tắc riêng? Vì sao? Không tự động là `DUPLICATE`; cần quy tắc seam/cross-camera riêng vì hai ảnh có thể cùng thấy một vật nhưng chưa có calibration timestamp và policy nối kết.
2. Một vật đi qua nhiều frame trên cùng camera: khi nào giữ cùng track ID, khi nào thêm keyframe hoặc trạng thái
   Outside? Nêu bằng chứng sẽ cần trước khi nối track qua hai camera. Giữ cùng track ID khi có timestamp liên tục và chuyển động phù hợp; thêm keyframe khi hình học thay đổi rõ; dùng Outside khi vật ra khỏi trường nhìn. Trước khi nối qua hai camera cần timestamp calibration bằng chứng appearance và policy output.
3. Nhìn lại cả buổi: một chỗ bạn tin nhãn mình đúng nhưng reference hoặc người soát nghĩ khác (dẫn frame/`object_ref`),
   bạn đã xử lý thế nào, và nếu làm lại slice này bạn sẽ đổi gì trong cách làm? Ở `adasind_102750.jpg` ca `L2+R2` compare gán `WRONG_CLASS` (L ThreeWheeler, R Truck, IoU 0.909). Tôi không copy class của teaching reference; ghi `action=escalate` và ticket cho guideline. Nếu làm lại slice: khóa sau khi đã có `ego_body`, chạy `selfqc` trên đúng file khóa (không để draft/lock lệch nhau), và chụp mép trái frame này trước khi tranh luận class.
