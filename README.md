##  BÀI TOÁN 1: HỒI QUY - DỰ ĐOÁN GIÁ NHÀ (HOUSE PRICES)

### 1. Quy trình thực hiện (Pipeline)
* **Tiền xử lý:** Điền khuyết dữ liệu bằng thống kê (`median`, `mode`); Sử dụng Box plot lọc nhiễu Outliers; Áp dụng **Log Transform (`np.log1p`)** đưa biến mục tiêu `SalePrice` về phân phối chuẩn.
* **Mã hóa & Chuẩn hóa:** Sử dụng One-Hot Encoding chuyển đổi biến định tính; Áp dụng `StandardScaler` đưa các biến về cùng thang đo (Phân chia tỉ lệ Train/Val: 80/20, chống rò rỉ dữ liệu).
* **EDA:** Trực quan hóa ma trận tương quan bằng **Heatmap** và kiểm tra giả định tuyến tính bằng **Scatter Plot**.

### 2. Mô hình & Siêu tham số (Hyperparameters)
* **Thuật toán:** **Ridge Regression** (Hồi quy tuyến tính có điều chuẩn L2).
* **Siêu tham số lựa chọn:** `alpha = 10.0` (Giúp phạt các hệ số hồi quy của biến nhiễu, chống hiện tượng Overfitting).
* **Đầu ra toán học:** Trích xuất chi tiết Hệ số chặn (`Intercept`) và Hệ số hồi quy (`Coefficients`) giải thích tác động kinh tế.

### 3. Đánh giá kết quả
* Chuyển đổi ngược dữ liệu dự đoán về lại thang đo tiền tệ thực tế bằng `np.expm1()`.
* **Chỉ số định lượng:** Đánh giá qua bộ chỉ số hồi quy chuẩn mực: `MAE`, `MSE`, `RMSE`, và `R-squared (R² Score)`.
* **Trực quan hóa:** Sử dụng **Residual Plot** để chứng minh tính ngẫu nhiên của sai số (thỏa mãn giả định phương sai đồng nhất).

---

##  BÀI TOÁN 2: PHÂN LOẠI - DỰ ĐOÁN SỐNG SÓT TITANIC

### 1. Quy trình thực hiện (Pipeline)
* **Tiền xử lý:** Điền khuyết cột `Age` bằng trung vị, cột `Embarked` bằng yếu vị `mode`; Loại bỏ các hành khách có giá vé dị biệt (`Fare > 300`); Giữ nguyên phân phối nhị phân của biến mục tiêu `Survived`.
* **Mã hóa & Chuẩn hóa:** Áp dụng One-Hot Encoding cho các thuộc tính chữ (`Sex`, `Embarked`) và chuẩn hóa dữ liệu bằng `StandardScaler` nghiêm ngặt (chỉ `fit` trên tập Train).
* **EDA:** Vẽ ma trận tương quan Heatmap; Trực quan hóa tỉ lệ sống sót rời rạc bằng biểu đồ cột **Bar Plot** và biểu đồ mật độ phân phối **KDE Plot**.

### 2. Mô hình & Siêu tham số (Hyperparameters)
* **Thuật toán:** **Logistic Regression** (Hồi quy Logistic phân loại nhị phân).
* **Siêu tham số lựa chọn:** Hệ số nghịch đảo điều chuẩn cường độ **`C = 1.0`** nhằm tối ưu hóa hàm chi phí Log-Loss, tìm ra ranh giới phân lớp có khả năng khái quát hóa tốt nhất.
* **Đầu ra toán học:** In ra Hệ số chặn (`Intercept`) và các Hệ số hồi quy (`Coefficients`) nhằm đo lường mức độ đóng góp của từng đặc trưng vào cơ hội sống sót của hành khách.

### 3. Đánh giá kết quả
* **Chỉ số định lượng:** Đánh giá năng lực phân tách ranh giới toàn diện bằng bộ chỉ số chuyên dụng: `Accuracy`, `Precision`, `Recall`, và `F1-Score`.
* **Trực quan hóa:** Sử dụng **Confusion Matrix (Ma trận nhầm lẫn)** hiển thị chi tiết số lượng mẫu phân loại đúng/sai giữa hai nhóm (Sống sót và Không sống sót).

---

##  Cấu trúc thư mục kho lưu trữ
* `Dự_đoán_giá_nhà.ipynb` - File chứa toàn bộ code, biểu đồ và nhận xét của Bài toán 1.
* `Phân_loại_Titanic.ipynb` - File chứa toàn bộ code, biểu đồ và nhận xét của Bài toán 2.
* `README.md` - File hướng dẫn và tóm tắt dự án (file này).
