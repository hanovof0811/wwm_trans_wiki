# Hướng dẫn sử dụng tính năng Export

## Mục đích

Tính năng Export cho phép bạn xuất file ngôn ngữ `translate_words_map` từ database, áp dụng các bản dịch đã được chỉnh sửa và đóng gói lại thành file sẵn sàng sử dụng.

---

## Yêu cầu

### Quyền truy cập
- Chỉ người dùng có vai trò **Admin** hoặc **SMod** mới có thể sử dụng tính năng này.

### Điều kiện tiên quyết
- Đã có file ngôn ngữ gốc được import vào hệ thống trước đó
- Thư mục output tương ứng phải tồn tại

---

## Các bước thực hiện

### Bước 1: Truy cập trang Export

1. Đăng nhập vào hệ thống với tài khoản có quyền Admin hoặc SMod
2. Vào menu **Where Winds Meet** → **Export**

### Bước 2: Chọn ngôn ngữ

Chọn ngôn ngữ bạn muốn export:

| Mã ngôn ngữ | Tên hiển thị |
|-------------|--------------|
| `en` | English |
| `zh_cn` | 中文 (Tiếng Trung) |
| `vi_en` | Tiếng Việt - EN |
| `vi_cn` | Tiếng Việt - CN |

### Bước 3: Chọn loại file

Chọn loại file cần export:

| Loại | Mô tả |
|------|-------|
| `full` | File đầy đủ (translate_words_map) |
| `diff` | File chỉ chứa thay đổi (translate_words_map_diff) |

### Bước 4: Thực hiện Export

1. Nhấn nút **"Export"**
2. Xác nhận trong hộp thoại xuất hiện
3. Theo dõi thanh tiến độ để biết trạng thái export

---

## Trạng thái Export

| Trạng thái | Mô tả | Tiến độ |
|------------|-------|---------|
| `queued` | Đang chờ trong hàng đợi | 0% |
| `reading` | Đang đọc file JSON gốc | 0-5% |
| `fetching` | Đang tải translations từ database | 5-30% |
| `processing` | Đang áp dụng bản dịch | 30-90% |
| `writing` | Đang ghi file JSON | 90-92% |
| `repacking` | Đang đóng gói file (wwm_utils) | 92-95% |
| `completed` | Export hoàn tất thành công | 100% |
| `cancelled` | Export bị hủy bởi người dùng | - |
| `failed` | Export thất bại | - |

---

## Thứ tự ưu tiên bản dịch

Khi export, hệ thống sẽ lấy bản dịch theo thứ tự ưu tiên sau:

1. **`manual_translation`** - Bản dịch thủ công (ưu tiên cao nhất)
2. **`vi_auto_edit`** - Bản dịch tự động đã chỉnh sửa
3. **`vi_cn`** - Bản dịch Tiếng Việt từ Tiếng Trung
4. **`vi_en`** - Bản dịch Tiếng Việt từ Tiếng Anh
5. **`ai_translation`** - Bản dịch AI (ưu tiên thấp nhất)

> Nếu tất cả đều trống, giữ nguyên giá trị gốc.

---

## Tải file đã export

Sau khi export hoàn tất:

1. Link tải file sẽ xuất hiện trên trang
2. Nhấn vào link để tải file về máy
3. File sẽ có tên dạng: `translate_words_map_{language}` hoặc `translate_words_map_{language}_diff`

---

## Hủy Export đang chạy

Nếu muốn hủy export đang chạy:

1. Nhấn nút **"Hủy Export"** (nếu có)
2. Xác nhận hủy
3. Job sẽ dừng lại ở batch tiếp theo

> **Lưu ý:** Việc hủy có thể mất vài giây để có hiệu lực.

---

## Lưu ý quan trọng

### ⚠️ Chỉ có 1 job chạy tại một thời điểm

- Hệ thống chỉ cho phép **1 job Import hoặc Export** chạy đồng thời trên toàn hệ thống
- Nếu có job đang chạy (kể cả Import), bạn không thể Export và ngược lại
- Thông báo sẽ hiển thị:
  - Ai đang chạy job
  - Loại job (Import/Export)
  - Thời gian bắt đầu

### ⏱️ Thời gian xử lý

- Thời gian export phụ thuộc vào số lượng records trong database
- Export có thể mất từ vài phút đến 1-2 giờ với database lớn
- Tiến độ được cập nhật real-time trên thanh progress

### 💾 Bộ nhớ

- Export sử dụng tối đa **8GB RAM** cho file lớn
- Đảm bảo server có đủ bộ nhớ trước khi export

---

## Xử lý lỗi

### Job bị treo (Lock không tự xóa)

Nếu job hoàn thành nhưng lock không tự xóa (Admin thấy nút "🔓 Xóa Lock"):

1. Đảm bảo không có job nào đang thực sự chạy
2. Nhấn nút **"🔓 Xóa Lock"** (chỉ Admin)
3. Xác nhận xóa lock

### Lỗi "File không tồn tại"

- Đảm bảo đã import file ngôn ngữ gốc trước đó
- Kiểm tra thư mục `storage/app/public/wwm_tools/output/`

### Lỗi "Repack thất bại"

1. Kiểm tra file `wwm_utils` có quyền execute
2. Kiểm tra log tại `storage/logs/laravel.log`
3. Đảm bảo file output JSON được tạo thành công

### Export bị hủy ngoài ý muốn

1. Kiểm tra log để xem lý do
2. Có thể do timeout hoặc lỗi memory
3. Thử export lại với batch size nhỏ hơn

---

## Cấu trúc thư mục

```
storage/app/public/wwm_tools/
├── wwm_utils                    # Tool đóng gói file
├── translate_words_map_vi_en    # File gốc (đã import)
├── translate_words_map_vi_cn    # File gốc (đã import)
└── output/
    ├── translate_words_map_vi_en/
    │   ├── entries.json         # File JSON gốc
    │   ├── entries_edited.json  # File JSON đã áp dụng bản dịch
    │   └── result/
    │       └── merged/          # File đã đóng gói (kết quả cuối)
    └── translate_words_map_vi_cn/
        └── ...
```

---

## Ví dụ quy trình hoàn chỉnh

```
1. Vào menu: Where Winds Meet → Export
2. Chọn ngôn ngữ: Tiếng Việt - EN
3. Chọn loại: Full
4. Nhấn "Export" → Xác nhận
5. Theo dõi tiến độ:
   - Đang tải translations từ database... (30%)
   - Đang xử lý: 500,000/1,000,000 (60%)
   - Đang ghi file JSON... (92%)
   - Đang repack file... (95%)
   - Export hoàn tất! (100%)
6. Tải file từ link xuất hiện
```

---

## So sánh Import vs Export

| Tính năng | Import | Export |
|-----------|--------|--------|
| Mục đích | Nhập file vào database | Xuất file từ database |
| File đầu vào | translate_words_map | File JSON trong thư mục output |
| File đầu ra | Records trong database | translate_words_map (đã dịch) |
| Thứ tự ưu tiên | Ghi đè theo ngôn ngữ | manual > vi_auto_edit > vi_cn > vi_en > ai |

---

## Hỗ trợ

Nếu gặp vấn đề, vui lòng:
1. Kiểm tra log hệ thống tại `storage/logs/laravel.log`
2. Xem trạng thái queue worker
3. Liên hệ Admin để được hỗ trợ

