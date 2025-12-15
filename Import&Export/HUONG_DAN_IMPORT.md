# Hướng dẫn sử dụng tính năng Import

## Mục đích

Tính năng Import cho phép bạn nhập file ngôn ngữ `translate_words_map` vào hệ thống để cập nhật hoặc thêm mới các bản dịch.

---

## Yêu cầu

### Quyền truy cập
- Chỉ người dùng có vai trò **Admin** hoặc **SMod** mới có thể sử dụng tính năng này.

### Định dạng file
- Tên file **bắt buộc** phải bắt đầu bằng `translate_words_map`
- Kích thước file tối đa: **50MB**
- Ví dụ tên file hợp lệ:
  - `translate_words_map`
  - `translate_words_map_diff`
  - `translate_words_map_v1.2`

---

## Các bước thực hiện

### Bước 1: Truy cập trang Import

1. Đăng nhập vào hệ thống với tài khoản có quyền Admin hoặc SMod
2. Vào menu **Where Winds Meet** → **Import**

### Bước 2: Chọn file để import

1. Nhấn vào ô **"Import file ngôn ngữ"**
2. Chọn file `translate_words_map` từ máy tính của bạn
3. Đợi file được tải lên hoàn tất

### Bước 3: Chọn ngôn ngữ

Chọn một trong các ngôn ngữ sau:

| Mã ngôn ngữ | Tên hiển thị |
|-------------|--------------|
| `en` | English |
| `zh_cn` | 中文 (Tiếng Trung) |
| `vi_en` | Tiếng Việt - EN |
| `vi_cn` | Tiếng Việt - CN |

### Bước 4: Thực hiện Import

1. Nhấn nút **"Import"**
2. Xác nhận trong hộp thoại xuất hiện
3. Theo dõi thanh tiến độ để biết trạng thái import

---

## Trạng thái Import

| Trạng thái | Mô tả |
|------------|-------|
| `queued` | Đang chờ trong hàng đợi |
| `reading` | Đang đọc file JSON |
| `processing` | Đang xử lý và nhập dữ liệu |
| `completed` | Import hoàn tất thành công |
| `failed` | Import thất bại (xem thông báo lỗi) |

---

## Lưu ý quan trọng

### ⚠️ Chỉ có 1 job chạy tại một thời điểm

- Hệ thống chỉ cho phép **1 job Import hoặc Export** chạy đồng thời trên toàn hệ thống
- Nếu có job đang chạy, bạn sẽ thấy thông báo:
  - Ai đang chạy job
  - Loại job (Import/Export)
  - Thời gian bắt đầu

### ⏱️ Thời gian xử lý

- Thời gian import phụ thuộc vào kích thước file
- File lớn có thể mất từ vài phút đến vài giờ
- Không đóng trình duyệt trong khi job đang chạy

### 🔄 Cập nhật dữ liệu

- Nếu `ukey` đã tồn tại trong database → **Cập nhật** giá trị mới
- Nếu `ukey` chưa tồn tại → **Thêm mới** record

---

## Xử lý lỗi

### Job bị treo (Lock không tự xóa)

Nếu job hoàn thành nhưng lock không tự xóa (Admin thấy nút "🔓 Xóa Lock"):

1. Đảm bảo không có job nào đang thực sự chạy
2. Nhấn nút **"🔓 Xóa Lock"** (chỉ Admin)
3. Xác nhận xóa lock

### File không được chấp nhận

- Kiểm tra tên file bắt đầu bằng `translate_words_map`
- Kiểm tra kích thước file không vượt quá 50MB

### Import thất bại

1. Kiểm tra log tại `storage/logs/laravel.log`
2. Đảm bảo file JSON có định dạng đúng
3. Thử import lại sau khi xóa progress cũ

---

## Ví dụ quy trình hoàn chỉnh

```
1. Vào menu: Where Winds Meet → Import
2. Chọn file: translate_words_map_v1.5
3. Chọn ngôn ngữ: Tiếng Việt - EN
4. Nhấn "Import" → Xác nhận
5. Theo dõi tiến độ: 0% → 50% → 100%
6. Thông báo: "Import hoàn tất!"
```

---

## Hỗ trợ

Nếu gặp vấn đề, vui lòng:
1. Kiểm tra log hệ thống
2. Liên hệ Admin để được hỗ trợ

