# 🎮 WWM Translation Wiki

> Hướng dẫn sử dụng Web App dịch game **Where Winds Meet** (Yến Vân Đài)

---

## 📖 Giới thiệu

Web App WWM Translation là công cụ hỗ trợ dịch thuật game **Where Winds Meet** (逆水寒 - Yến Vân Đài). Hệ thống cho phép:

- 📝 Quản lý và chỉnh sửa bản dịch tiếng Việt
- 🔍 Tìm kiếm và thay thế hàng loạt
- 📥 Import file ngôn ngữ gốc từ game
- 📤 Export file đã dịch để sử dụng

---

## 📚 Mục lục hướng dẫn

### 🔄 Import & Export

| Tài liệu | Mô tả |
|----------|-------|
| [📥 Hướng dẫn Import](<HUONG_DAN_IMPORT.md>) | Cách nhập file ngôn ngữ `translate_words_map` vào hệ thống |
| [📤 Hướng dẫn Export](<HUONG_DAN_EXPORT.md>) | Cách xuất file ngôn ngữ đã dịch để sử dụng trong game |

### 🔍 Find & Replace

| Tài liệu | Mô tả |
|----------|-------|
| [🎯 Quick Guide](<FIND_REPLACE_QUICK_GUIDE.md>) | Hướng dẫn nhanh sử dụng Find & Replace |
| [📖 Hướng dẫn chi tiết](<HUONG_DAN_FIND_REPLACE.md>) | Hướng dẫn đầy đủ với các ví dụ thực tế |

---

## 🚀 Bắt đầu nhanh

### 1️⃣ Đăng nhập
- Truy cập web app và đăng nhập bằng tài khoản được cấp
- Vai trò: **Admin**, **SMod**, hoặc **Translator**

### 2️⃣ Dịch thuật cơ bản
1. Vào menu **Where Winds Meet** → **WWM Trans**
2. Sử dụng **Filter** để lọc các dòng cần dịch
3. Chọn dòng và chỉnh sửa trực tiếp hoặc sử dụng **Bulk Actions**

### 3️⃣ Các cột dữ liệu chính

| Cột | Ký hiệu | Mô tả |
|-----|---------|-------|
| CN | `zh_cn` | Văn bản gốc tiếng Trung |
| EN | `en` | Văn bản gốc tiếng Anh |
| VI-EN | `vi_en` | Bản dịch Việt từ tiếng Anh |
| VI-CN | `vi_cn` | Bản dịch Việt từ tiếng Trung |
| VI Auto Edit | `vi_auto_edit` | Bản dịch tự động đã chỉnh sửa |
| AI Translation | `ai_translation` | Bản dịch từ AI |
| Manual Translation | `manual_translation` | Bản dịch thủ công (ưu tiên cao nhất) |
| Note | `note` | Ghi chú |

---

## ⭐ Tính năng chính

### 🔍 Find & Replace
Tìm kiếm và thay thế hàng loạt với các tùy chọn:
- ✅ Chọn cột nguồn để tìm kiếm
- ✅ Chọn cột đích để lưu kết quả
- ✅ Tùy chọn phân biệt chữ hoa/thường
- ✅ Áp dụng cho các dòng đã chọn sau khi filter

👉 [Xem hướng dẫn chi tiết](<HUONG_DAN_FIND_REPLACE.md>)

### 📥 Import
Nhập file ngôn ngữ từ game vào hệ thống:
- Hỗ trợ file `translate_words_map`
- Tự động phát hiện và cập nhật dữ liệu mới

👉 [Xem hướng dẫn Import](<HUONG_DAN_IMPORT.md>)

### 📤 Export
Xuất file ngôn ngữ đã dịch:
- Xuất file đầy đủ hoặc chỉ phần thay đổi (diff)
- Tự động đóng gói sẵn sàng sử dụng

👉 [Xem hướng dẫn Export](<HUONG_DAN_EXPORT.md>)

---

## 🔐 Phân quyền

| Vai trò | Quyền hạn |
|---------|-----------|
| **Admin** | Toàn quyền: Import, Export, xóa lock, quản lý user |
| **SMod** | Import, Export, Find & Replace, chỉnh sửa dịch |
| **Translator** | Chỉnh sửa bản dịch, Find & Replace |

---

## 📌 Thứ tự ưu tiên khi Export

Khi xuất file, hệ thống sẽ lấy bản dịch theo thứ tự ưu tiên:

1. 🥇 `manual_translation` - Bản dịch thủ công
2. 🥈 `vi_auto_edit` - Bản dịch tự động đã chỉnh sửa
3. 🥉 `vi_cn` - Bản dịch Việt từ tiếng Trung
4. 4️⃣ `vi_en` - Bản dịch Việt từ tiếng Anh
5. 5️⃣ `ai_translation` - Bản dịch AI

> 💡 Nếu tất cả đều trống, giữ nguyên giá trị gốc.

---

## ⚠️ Lưu ý quan trọng

- ⏱️ **Chỉ 1 job Import/Export** có thể chạy đồng thời trên toàn hệ thống
- 🔄 **Không đóng trình duyệt** khi đang có job chạy
- 💾 **Lưu thường xuyên** khi chỉnh sửa dịch
- ⚡ **Sử dụng Filter** để làm việc hiệu quả hơn

---

## 🆘 Hỗ trợ

Nếu gặp vấn đề hoặc cần hỗ trợ, vui lòng liên hệ:
- 📧 Admin hoặc SMod của hệ thống
- 💬 Group chat dự án

---

**© WWM Translation Team**
