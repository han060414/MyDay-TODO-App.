# MyDay – TODO App quản lý công việc cá nhân
**Sinh viên:** Văn Ngọc Hân – **MSSV:** 31241027313

## Link bài làm
- **GitHub (source code):** [MyDay-TODO-App](https://github.com/han060414/MyDay-TODO-App.)
- **Website (GitHub Pages):** [Trải nghiệm MyDay](https://han060414.github.io/MyDay-TODO-App./)


## 1. Giới thiệu
Ứng dụng web quản lý công việc cá nhân, giao diện responsive xanh dương pastel. Công nghệ HTML5, CSS3, JavaScript thuần và IndexedDB (cơ sở dữ liệu NoSQL tích hợp trong trình duyệt).

## 2. Chức năng
- Mặc định hiển thị task ngày hôm nay; có thể xem tất cả ngày.
- Tìm kiếm tên/mô tả; lọc theo trạng thái, mức ưu tiên và ngày hôm nay/tất cả.
- Thêm, sửa, xóa (có xác nhận), đánh dấu hoàn thành; kiểm tra trường bắt buộc.
- Thống kê tổng số task, hoàn thành, chưa hoàn thành, tỷ lệ hoàn thành; biểu đồ tiến độ 7 ngày và phân bố ưu tiên.
- Dữ liệu mẫu tự khởi tạo một lần; thay đổi được lưu qua các lần tải lại trang.

## 3. Database (IndexedDB)
Database `MyDayDB`, version 1; object store `tasks`, khóa chính `id` tự tăng; index `due`, `status`.

| Trường | Kiểu | Ý nghĩa |
|---|---|---|
| id | Number | Khóa chính |
| name | String | Tên task |
| description | String | Mô tả |
| due | String | Ngày YYYY-MM-DD |
| priority | String | Cao / Trung bình / Thấp |
| status | String | open / done |

CRUD: add(), getAll(), put(), delete() trong transaction IndexedDB. Dữ liệu nằm trên trình duyệt, không đồng bộ giữa thiết bị, không có backend. Có thể kiểm tra tại DevTools → Application → IndexedDB → MyDayDB → tasks.

## 4. Chạy chương trình
Dùng VS Code Live Server mở index.html, hoặc chạy `python -m http.server 8000` tại thư mục dự án, truy cập http://localhost:8000. Có thể triển khai trực tiếp lên GitHub Pages (Settings → Pages → Deploy from a branch → main → /root). Không cần cài thư viện.

## 5. Prompt Vibe Coding
Xem [PROMPT.md](PROMPT.md) để biết prompt mô tả yêu cầu xây dựng ứng dụng.

## 6. Kịch bản kiểm thử thủ công
| Test | Thao tác | Kết quả mong đợi |
|---|---|---|
| TC01 | Mở lần đầu | Hiển thị task mẫu ngày hiện tại |
| TC02 | Thêm task ngày hôm nay | Task xuất hiện và tổng tăng |
| TC03 | Sửa tên và ưu tiên | Dữ liệu cập nhật |
| TC04 | Tick hoàn thành | Trạng thái và thống kê đổi |
| TC05 | Tìm kiếm, lọc | Chỉ hiển thị task phù hợp |
| TC06 | Xóa và xác nhận | Task biến mất |
| TC07 | Tải lại trang | Dữ liệu đã lưu vẫn tồn tại |
| TC08 | Mở thống kê | Biểu đồ và KPI phản ánh dữ liệu |
| TC09 | Thu nhỏ màn hình | Giao diện thích ứng |

## 7. Cấu trúc
`index.html` giao diện; `style.css` định dạng; `app.js` logic và database; `PROMPT.md` prompt; `README.md` tài liệu.
