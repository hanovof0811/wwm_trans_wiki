# Hướng dẫn sử dụng tính năng Find & Replace - WWM Translation

## ✅ Tính năng đã hoàn thành

Tính năng **Find & Replace** đã được thêm vào trang **WWM Trans** với cơ chế:
- **Chọn cột nguồn** để tìm kiếm chuỗi
- **Chọn cột đích** để lưu kết quả sau khi thay thế

### 🎯 Các tính năng chính:
1. ✅ **Chọn cột nguồn tùy ý**: Tìm kiếm trong CN, EN, VI-EN, VI-CN, Manual Translation, v.v.
2. ✅ **Chọn cột đích tùy ý**: Lưu kết quả vào bất kỳ cột nào (mặc định: VI Auto Edit)
3. ✅ **Linh hoạt**: Có thể chọn cùng cột nguồn và cột đích để thay thế trực tiếp (ghi đè)
4. ✅ **Bảo toàn dữ liệu gốc**: Nếu chọn cột đích khác cột nguồn, dữ liệu gốc được giữ nguyên
5. ✅ **Áp dụng cho các dòng đã chọn**: Chỉ thay thế trên các bản ghi bạn đã chọn
6. ✅ **Kết hợp với Filter**: Bạn có thể lọc dữ liệu trước, sau đó chọn và thay thế
7. ✅ **Phân biệt chữ hoa thường**: Có checkbox để bật/tắt tìm kiếm chính xác
8. ✅ **Tự động lưu editor**: Người thực hiện sẽ được lưu vào trường "Người sửa"

---

## 📋 Cách sử dụng (Đơn giản)

### Bước 1: Lọc dữ liệu (nếu cần)
- Click nút **Filter**
- Nhập điều kiện lọc (ví dụ: CN chính xác, EN chính xác, v.v.)
- Kết quả sẽ chỉ hiển thị các dòng phù hợp

### Bước 2: Chọn các dòng cần thay thế
- ✅ Tích checkbox ở đầu mỗi dòng cần thay thế
- ✅ Hoặc tích checkbox ở header để chọn tất cả dòng **trên trang hiện tại**

### Bước 3: Mở Find & Replace
- Click vào **Bulk Actions** (hoặc icon 3 chấm)
- Chọn **Find & Replace**

### Bước 4: Điền thông tin
| Trường | Mô tả | Bắt buộc |
|--------|-------|----------|
| **Cột nguồn (tìm kiếm)** | Chọn cột để TÌM chuỗi | ✅ |
| **Tìm** | Chuỗi cần tìm | ✅ |
| **Thay thế bằng** | Chuỗi mới (để trống = xóa) | ☐ |
| **Tìm chính xác** | Phân biệt HOA/thường | ☐ |
| **Cột đích (lưu kết quả)** | Chọn cột để LƯU kết quả (mặc định: VI Auto Edit) | ✅ |

**📌 LƯU Ý QUAN TRỌNG:** 
- Kết quả sau khi thay thế sẽ được **LƯU VÀO CỘT ĐÍCH** (bạn chọn)
- Nếu cột nguồn ≠ cột đích: Dữ liệu gốc được **BẢO TOÀN**
- Nếu cột nguồn = cột đích: Dữ liệu gốc sẽ bị **GHI ĐÈ** (thay thế trực tiếp)

### Bước 5: Thực hiện
- Click **Thực hiện**
- Xác nhận
- Xem thông báo kết quả

---

## 🔍 Ví dụ thực tế

### Ví dụ 1: Tìm trong Manual Translation, lưu vào VI Auto Edit
```
Cột nguồn: Manual Translation
Tìm: "game"
Thay thế: "trò chơi"
Tìm chính xác: ☐ (KHÔNG tích)
Cột đích: VI Auto Edit

Kết quả:
Manual Translation (GỐC) | VI Auto Edit (MỚI)
"Game offline"           → "trò chơi offline"
"GAME mobile"            → "trò chơi mobile"  
"game online"            → "trò chơi online"

⚠️ Cột "Manual Translation" vẫn giữ nguyên giá trị gốc!
```

### Ví dụ 2: Thay thế TRỰC TIẾP trong Manual Translation
```
Cột nguồn: Manual Translation
Tìm: "game"
Thay thế: "trò chơi"
Tìm chính xác: ☐
Cột đích: Manual Translation (cùng với cột nguồn)

Kết quả:
Manual Translation (TRƯỚC) | Manual Translation (SAU)
"Game offline"             → "trò chơi offline"
"GAME mobile"              → "trò chơi mobile"  
"game online"              → "trò chơi online"

⚠️ Dữ liệu gốc bị GHI ĐÈ!
```

### Ví dụ 3: Tìm trong CN, thay thế và lưu vào Manual Translation
```
Cột nguồn: CN (zh_cn)
Tìm: "系统"
Thay thế: "Hệ thống"
Tìm chính xác: ✅ (CÓ tích)
Cột đích: Manual Translation

Kết quả:
CN (GỐC)      | Manual Translation (MỚI)
"系统设置"    → "Hệ thống设置"
"游戏系统"    → "游戏Hệ thống"

⚠️ Cột "CN" vẫn giữ nguyên!
```

### Ví dụ 4: Copy và sửa từ EN sang Manual Translation
```
Cột nguồn: EN
Tìm: "System"
Thay thế: "Hệ thống"
Tìm chính xác: ✅
Cột đích: Manual Translation

Kết quả:
EN (GỐC)              | Manual Translation (MỚI)
"System Settings"     → "Hệ thống Settings"
"SYSTEM mobile"       → (không thay đổi, vì khác chữ hoa)
```

### Ví dụ 5: Xóa chuỗi từ Note
```
Cột nguồn: Note
Tìm: "TODO: "
Thay thế: (để trống)
Cột đích: Note (cùng cột)

Kết quả:
Note (TRƯỚC)                | Note (SAU)
"TODO: Kiểm tra lại"       → "Kiểm tra lại"
"TODO: Cần xem xét"        → "Cần xem xét"
```

### Ví dụ 6: Kết hợp với Filter - Copy và chỉnh sửa hàng loạt
```
Bước 1: Áp dụng Filter
- CN chính xác = "系统"

Bước 2: Chọn tất cả kết quả (ví dụ: 50 dòng)

Bước 3: Find & Replace
- Cột nguồn: VI-CN
- Tìm: "hệ thống"
- Thay thế: "hệ thống game"
- Cột đích: Manual Translation

Kết quả: 
- Chỉ các dòng có CN = "系统" được xử lý
- Lấy giá trị từ VI-CN, thay thế "hệ thống" → "hệ thống game"
- Lưu vào Manual Translation
- VI-CN giữ nguyên
```

---

## ⚠️ Lưu ý quan trọng

### 🔴 CỘT NGUỒN vs CỘT ĐÍCH

#### Trường hợp 1: Cột nguồn ≠ Cột đích (Khuyến nghị)
```
Cột nguồn: EN
Cột đích: Manual Translation

✅ Dữ liệu gốc (EN) KHÔNG thay đổi
✅ Kết quả lưu vào Manual Translation
✅ An toàn, có thể khôi phục
```

#### Trường hợp 2: Cột nguồn = Cột đích (Thay thế trực tiếp)
```
Cột nguồn: Manual Translation
Cột đích: Manual Translation

⚠️ Dữ liệu gốc sẽ bị GHI ĐÈ
⚠️ KHÔNG thể hoàn tác
⚠️ Hãy cẩn thận khi dùng!
```

### 🔴 KHÔNG THỂ HOÀN TÁC (Undo)
- Sau khi click "Thực hiện", dữ liệu sẽ được lưu ngay vào database
- **KHÔNG CÓ** nút Undo
- ⚠️ Hãy kiểm tra kỹ trước khi thực hiện!

### 📌 Bulk Action chỉ áp dụng cho dòng đã CHỌN
- Find & Replace **KHÔNG tự động** áp dụng cho tất cả dòng trong filter
- Bạn **PHẢI CHỌN** các dòng trước
- Để chọn nhiều dòng:
  - Tăng số items/page lên 50
  - Tích checkbox ở header
  - Hoặc chọn từng trang

### ✅ Best Practices
1. ✅ Áp dụng **Filter** để thu hẹp phạm vi
2. ✅ **Test** với vài dòng trước khi áp dụng hàng loạt
3. ✅ Sử dụng **"Tìm chính xác"** khi cần độ chính xác cao
4. ✅ Kiểm tra kỹ chuỗi "Tìm" và "Thay thế"
5. ✅ Chọn **cột đích khác cột nguồn** để bảo toàn dữ liệu gốc
6. ✅ Chỉ chọn **cột đích = cột nguồn** khi chắc chắn muốn ghi đè

---

## 🛠️ Thông tin kỹ thuật

### File đã chỉnh sửa:
```
app/Filament/Resources/WWMTranslationResource.php
```

### Luồng xử lý:
1. Đọc giá trị từ **cột nguồn** (source_field)
2. Tìm kiếm chuỗi trong giá trị đó
3. Thay thế chuỗi (nếu tìm thấy)
4. Lưu kết quả vào **cột đích** (target_field)
5. Cập nhật **editor_id** = người thực hiện
6. Cột nguồn **CHỈ** thay đổi nếu trùng với cột đích

### Các cột có thể chọn (nguồn hoặc đích):
1. `zh_cn` - CN (Tiếng Trung)
2. `en` - EN (Tiếng Anh)
3. `vi_en` - VI-EN (Dịch từ tiếng Anh)
4. `vi_cn` - VI-CN (Dịch từ tiếng Trung)
5. `vi_auto_edit` - VI Auto Edit (Mặc định cho cột đích)
6. `ai_translation` - AI Translation
7. `manual_translation` - Manual Translation (Mặc định cho cột nguồn)
8. `note` - Note (Ghi chú)

### Logic xử lý:
- **Case-sensitive** (Phân biệt HOA/thường): `str_contains()` + `str_replace()`
- **Case-insensitive** (Không phân biệt): `stripos()` + `str_ireplace()`
- Tự động cập nhật: `editor_id = auth()->id()`
- Hiển thị thông báo: Số lượng bản ghi đã cập nhật vào cột nào

---

## 💡 Workflow điển hình

### Quy trình 1: Copy và chỉnh sửa an toàn

1. **Filter** các bản ghi cần xử lý
2. **Chọn** các bản ghi
3. **Find & Replace**:
   - Cột nguồn: EN (hoặc VI-CN)
   - Tìm: "old text"
   - Thay thế: "new text"
   - Cột đích: VI Auto Edit (hoặc Manual Translation)
4. **Kiểm tra** kết quả trong cột đích
5. Nếu OK, có thể copy từ cột đích sang cột khác

### Quy trình 2: Sửa trực tiếp (Cẩn thận!)

1. **Filter** các bản ghi
2. **Chọn** một vài bản ghi để TEST
3. **Find & Replace**:
   - Cột nguồn: Manual Translation
   - Tìm: "old text"
   - Thay thế: "new text"
   - Cột đích: Manual Translation (GHI ĐÈ!)
4. **Kiểm tra** kết quả
5. Nếu OK, áp dụng cho phần còn lại

---

## 🎨 Use Cases

### Use Case 1: Dịch nhanh từ EN
```
Scenario: Bạn muốn dùng EN làm base, thay một vài từ sang tiếng Việt

Cột nguồn: EN
Tìm: "Settings"
Thay thế: "Cài đặt"
Cột đích: Manual Translation

→ Lưu vào Manual Translation, EN giữ nguyên
```

### Use Case 2: Chỉnh sửa hàng loạt Manual Translation
```
Scenario: Bạn đã dịch nhưng dùng sai thuật ngữ

Cột nguồn: Manual Translation
Tìm: "máy chủ"
Thay thế: "server"
Cột đích: Manual Translation

→ Ghi đè lên Manual Translation
```

### Use Case 3: Thử nghiệm với VI Auto Edit
```
Scenario: Bạn muốn thử nghiệm cách dịch mới

Cột nguồn: Manual Translation
Tìm: "game"
Thay thế: "trò chơi"
Cột đích: VI Auto Edit

→ Giữ Manual Translation, test ở VI Auto Edit
→ Nếu OK, copy từ VI Auto Edit sang Manual Translation
```

---

## 📞 Hỗ trợ
Nếu gặp vấn đề, vui lòng liên hệ team phát triển.

---

**Chúc bạn sử dụng hiệu quả! 🚀**

