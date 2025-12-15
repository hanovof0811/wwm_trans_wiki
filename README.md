# wwm_trans_wiki
✅ Tính năng Find & Replace - Hoàn thành
🎯 Yêu cầu
Chọn cột nguồn để tìm kiếm
Chọn cột đích để lưu kết quả sau khi thay thế
Có tùy chọn phân biệt chữ hoa thường
Áp dụng cho các dòng đang được filter
✅ Đã hoàn thành
Tính năng chính:
✅ Chọn cột nguồn: CN, EN, VI-EN, VI-CN, VI Auto Edit, AI Translation, Manual Translation, Note
✅ Chọn cột đích: Tất cả 8 cột (mặc định: VI Auto Edit)
✅ Linh hoạt: Có thể chọn cùng cột nguồn và cột đích để thay thế trực tiếp
✅ Bảo toàn dữ liệu: Nếu cột nguồn ≠ cột đích, dữ liệu gốc không thay đổi
✅ Checkbox "Tìm chính xác": Có thể bật/tắt phân biệt chữ hoa thường
✅ Áp dụng cho dòng đã chọn: Chỉ xử lý các bản ghi được chọn sau khi filter
✅ Tự động lưu editor: Cập nhật editor_id với người thực hiện
✅ Thông báo kết quả: Hiển thị số lượng bản ghi đã cập nhật vào cột nào
Cách sử dụng:
Filter dữ liệu (nếu cần)
Chọn các dòng cần xử lý
Click Bulk Actions → Find & Replace
Điền thông tin:
Cột nguồn (tìm kiếm): Chọn cột để tìm
Tìm: Nhập chuỗi cần tìm
Thay thế bằng: Nhập chuỗi thay thế
☑️ Tìm chính xác: Tích nếu muốn phân biệt chữ hoa/thường
Cột đích (lưu kết quả): Chọn cột để lưu (mặc định: VI Auto Edit)
Click Thực hiện
Ví dụ 1: Bảo toàn dữ liệu gốc
Cột nguồn: Manual Translation
Tìm: "game"
Thay thế: "trò chơi"
Cột đích: VI Auto Edit
Tìm chính xác: ☐

Kết quả:
- Manual Translation: "Game offline" (GIỮ NGUYÊN)
- VI Auto Edit: "trò chơi offline" (MỚI)
Ví dụ 2: Thay thế trực tiếp (ghi đè)
Cột nguồn: Manual Translation
Tìm: "game"
Thay thế: "trò chơi"
Cột đích: Manual Translation (cùng cột)
Tìm chính xác: ☐

Kết quả:
- Manual Translation: "Game offline" → "trò chơi offline" (GHI ĐÈ)
Ví dụ 3: Copy và chỉnh sửa từ EN sang Manual Translation
Cột nguồn: EN
Tìm: "System"
Thay thế: "Hệ thống"
Cột đích: Manual Translation
Tìm chính xác: ✅

Kết quả:
- EN: "System Settings" (GIỮ NGUYÊN)
- Manual Translation: "Hệ thống Settings" (MỚI)
📁 File đã chỉnh sửa
app/Filament/Resources/WWMTranslationResource.php
📄 Tài liệu
Xem file HUONG_DAN_FIND_REPLACE.md để biết chi tiết và ví dụ đầy đủ
⚠️ Lưu ý quan trọng
🔴 Cột nguồn vs Cột đích
Trường hợp 1: Cột nguồn ≠ Cột đích (Khuyến nghị)

✅ Dữ liệu gốc KHÔNG thay đổi
✅ Kết quả lưu vào cột đích
✅ An toàn, có thể khôi phục
Trường hợp 2: Cột nguồn = Cột đích (Thay thế trực tiếp)

⚠️ Dữ liệu gốc sẽ bị GHI ĐÈ
⚠️ KHÔNG thể hoàn tác
⚠️ Hãy cẩn thận khi dùng!
📌 Lưu ý khác
Kết quả CHỈ lưu vào cột đích mà bạn chọn
Nếu cột đích đã có dữ liệu, sẽ bị GHI ĐÈ
KHÔNG thể hoàn tác sau khi thực hiện
Chỉ áp dụng cho các dòng ĐÃ CHỌN, không tự động áp dụng cho tất cả kết quả filter
Status: ✅ COMPLETED Version: 2.0 - Với tính năng chọn cột đích
