# K26CNTT2_IT108_Session14_Ex05

# 🏢 Báo cáo Bài tập: Thiết kế Hệ thống Cộng tác Đám mây Doanh nghiệp
**Môn học:** Nhập Môn Công Nghệ Thông Tin (Buổi 15: Không gian cộng tác đám mây)  
**Học viên:** Lê Hồ Thanh Thảo (N26DTCN030)  
**Repository:** `K26CNTT2_IT108_Session14_Ex05`

---

## 1. Mục tiêu
- Tự thiết kế kiến trúc cộng tác đám mây toàn diện cho một Startup mở với 10 thành viên làm việc từ xa tại nhiều khu vực (Hà Nội, Đà Nẵng, TP.HCM).
- Vận dụng tư duy **Asynchronous Communication** (Làm việc bất đồng bộ) và thiết lập văn hóa số văn minh, bảo mật.

---

## 2. Bối cảnh & Bài toán
> **Tình huống:** Startup **Smart-Home** cần triển khai một không gian làm việc số cho đội ngũ phân tán tại 3 miền. 
> 
> **Yêu cầu:** Thiết kế (1) Cấu trúc thư mục Cloud an toàn, (2) Quy trình phân quyền cho các phòng ban, và (3) Văn hóa giao tiếp qua chat để bảo vệ thời gian riêng tư của nhân sự.

---

## 3. Thiết kế Kiến trúc Cloud & Phân quyền

### 3.1. Danh sách Channel & Thư mục tiêu chuẩn (Cloud Workspace Architecture)
Hệ thống được phân chia rõ ràng theo từng phòng ban và chức năng chuyên môn để kiểm soát quyền truy cập (`Least Privilege`):

```text
📁 Smart_Home_Enterprise_Workspace/
│
├── 📁 00_Company_General/             <-- Tài liệu chung toàn công ty (Viewer cho tất cả)
│   ├── 📄 Company_Handbook.pdf
│   └── 📄 Onboarding_Guide.docx
│
├── 📁 01_Board_Of_Directors/          <-- Khu vực bảo mật của Ban Giám Đốc (Restricted)
│   ├── 📊 Financial_Reports.xlsx
│   └── 📝 Strategy_2026.docx
│
├── 📁 02_Product_Dev_Department/      <-- Thư mục kỹ thuật & R&D (Chỉ Team Dev truy cập)
│   ├── 📁 01_Source_Code/             <-- Đồng bộ mã nguồn (Đã loại trừ node_modules)
│   ├── 📁 02_Architecture_Specs/      <-- Sơ đồ hệ thống, tài liệu đặc tả SRS
│   └── 📁 03_Testing_Reports/
│
├── 📁 03_Marketing_Sales/             <-- Tài liệu kinh doanh, tài nguyên thiết kế
│   ├── 🖼️ Brand_Assets_Logo/
│   └── 📊 Customer_Data_CRM/          <-- Giới hạn quyền nghiêm ngặt
│
└── 📁 04_HR_Operations/               <-- Quản lý nhân sự, chấm công, hợp đồng
