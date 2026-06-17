# 🚀 BÁO CÁO NGHIÊN CỨU VÀ THỰC HÀNH KIỂM THỬ API BẰNG CÔNG CỤ POSTMAN

## 📌 1. THÔNG TIN CHUNG
- **Môn học**: Đánh giá và kiểm thủ chất lượng phần mềm
- **Tên bài tập**: Bài tập thực hành Postman & API Testing basic
- **Sinh viên thực hiện**: Nguyễn Anh Đức
- **Mã sinh viên**: 23010650
- **Thời gian hoàn thành**: Tháng 06/2026

---

## 📚 2. CƠ SỞ LÝ THUYẾT (THEORETICAL BACKGROUND)

### 2.1. API và RESTful API là gì?
- **API (Application Programming Interface)**: Là giao diện lập trình ứng dụng, đóng vai trò như một cầu nối trung gian cho phép hai ứng dụng hoặc hệ thống khác nhau có thể "nói chuyện" và trao đổi dữ liệu với nhau.
- **RESTful API**: Là một tiêu chuẩn thiết kế API phổ biến dựa trên kiến trúc REST (Representational State Transfer). Hệ thống này sử dụng các phương thức HTTP tiêu chuẩn để quản lý và thao tác dữ liệu.

### 2.2. Các thành phần chính của một HTTP Request
Để giao tiếp với một API, người kiểm thử cần cấu hình một Request gồm các thành phần:
1. **HTTP Methods (Phương thức)**: 
   - `GET`: Lấy/đọc dữ liệu từ hệ thống (Phương thức được sử dụng trong bài tập này).
   - `POST`: Tạo mới dữ liệu.
   - `PUT`/`PATCH`: Cập nhật dữ liệu đã có.
   - `DELETE`: Xóa dữ liệu.
2. **URL / Endpoint**: Địa chỉ định danh của tài nguyên trên máy chủ (Server).
3. **Headers**: Chứa siêu dữ liệu (Metadata) như định dạng dữ liệu (`Content-Type: application/json`).
4. **Body**: Phần dữ liệu gửi kèm lên Server (thường dùng cho POST/PUT).

### 2.3. Công cụ kiểm thử Postman
Postman là một trong những API Client phổ biến nhất thế giới dành cho Developer và QA/Tester. Công cụ này hỗ trợ:
- Gửi các HTTP Request nhanh chóng và trực quan.
- Quản lý các Request theo cấu trúc **Collection** (thư mục).
- Viết mã kiểm thử tự động (Automation Testing) bằng ngôn ngữ **JavaScript**.
- Chạy kiểm thử hàng loạt bằng **Collection Runner**.

---

## 🛠️ 3. MÔI TRƯỜNG VÀ KỊCH BẢN KIỂM THỬ (TEST SCENARIOS)

### 3.1. Thông tin API thử nghiệm
Trong bài tập này, hệ thống sử dụng một Mock API chuẩn dữ liệu cộng đồng để thực hành:
- **Base URL**: `https://jsonplaceholder.typicode.com`
- **Endpoint**: `/users`
- **Phương thức**: `GET`
- **Chức năng**: Trả về danh sách thông tin chi tiết của 10 người dùng dưới định dạng dữ liệu JSON.

### 3.2. Kịch bản kiểm thử (Test Cases)
Bài tập thiết lập 02 kịch bản kiểm thử tự động chính để đánh giá chất lượng phản hồi từ hệ thống:

| Mã TC | Tên Kịch Bản | Mục Tiêu Kiểm Thử | Kết Quả Mong Đợi (Expected) |
| :--- | :--- | :--- | :--- |
| **TC-01** | Check Status Code | Xác thực phản hồi từ hệ thống có thành công hay không. | API phải trả về HTTP Status Code `200 OK`. |
| **TC-02** | Check Response Time | Đánh giá hiệu năng và tốc độ xử lý của Server. | Thời gian phản hồi của hệ thống phải nhỏ hơn `500ms`. |

---

## 📊 4. QUY TRÌNH THỰC HIỆN VÀ KẾT QUẢ MINH HỌA

### 4.1. Khởi tạo và Thiết lập Request
- Tiến hành cài đặt phần mềm Postman Desktop và đăng nhập đồng bộ bằng tài khoản Google.
- Khởi tạo cấu trúc dữ liệu gồm một thư mục Collection lớn mang tên `My Collection`. Bên trong chứa Request có tên `BaiTap_Postman` cấu hình theo phương thức `GET` và đường dẫn Endpoint đã chọn.

*Hình ảnh minh họa kết quả khi gửi Request thành công và nhận về dữ liệu JSON:*
![Kết quả Request](01_request.png)

### 4.2. Xây dựng mã kiểm thử tự động (Test Scripts)
Mã kiểm thử được lập trình bằng ngôn ngữ JavaScript đặt tại thẻ **Post-res** (chạy ngay sau khi nhận được phản hồi). Đoạn code cụ thể như sau:

```javascript
// Kiểm tra mã trạng thái HTTP trả về
pm.test("Kiểm tra mã trạng thái là 200", function () {
    pm.response.to.have.status(200);
});

// Kiểm tra hiệu năng xử lý (Thời gian phản hồi)
pm.test("Thời gian phản hồi dưới 500ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(500);
});
4.3. Kiểm thử tự động hàng loạt với Collection Runner
Để đảm bảo tất cả các kịch bản kiểm thử đều hoạt động ổn định và không phát sinh lỗi bất ngờ khi chạy liên tục, tính năng Collection Runner đã được kích hoạt để quét toàn bộ thư mục bài tập.

Hình ảnh minh họa báo cáo tổng hợp từ Collection Runner (Errors = 0):

💾 5. HƯỚNG DẪN REVIEW BÀI TẬP (DÀNH CHO NGƯỜI CHẤM BÀI)
Để kiểm tra trực tiếp các cấu hình và kịch bản test trên máy tính cá nhân, thầy/cô có thể thực hiện theo các bước sau:

Tải file file dữ liệu gốc My Collection.postman_collection.json đính kèm trong Repository này về máy.

Mở ứng dụng Postman, chọn nút Import ở góc trên cùng bên trái và tải file .json vừa download lên.

Toàn bộ cấu trúc thư mục, đường dẫn API và mã nguồn Test Scripts sẽ tự động được phục hồi chính xác 100%.

📝 6. KẾT LUẬN VÀ BÀI HỌC KINH NGHIỆM
Qua bài tập thực hành này, sinh viên đã đạt được các mục tiêu sau:

Sử dụng thành thạo giao diện và các tính năng cốt lõi của công cụ Postman.

Hiểu sâu hơn về cấu trúc của giao thức HTTP, cách đọc dữ liệu trả về kiểu JSON và ý nghĩa của các mã Status Code.

Bước đầu làm quen với tư duy viết Code kiểm thử tự động (Automation Testing), giúp tối ưu hóa thời gian và nâng cao độ chính xác so với việc kiểm thử thủ công (Manual Testing).
