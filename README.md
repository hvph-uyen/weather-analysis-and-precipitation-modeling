# Phân Tích và Dự Báo Lượng Mưa Tại Huế (Dữ liệu Lịch sử & Sự kiện 2025)

### 1. Thành viên nhóm 20

| Thành viên           | MSSV     |
| :-----------------   | :--------|
| Phạm Hương Trà       | 23120177 |
| Hàn Vũ Phương Uyên   | 23120106 |
| Trần Minh Trọng      | 23120100 |
| Bạch Trương Tấn Phát | 23120316 |

---

### 2. Tổng quan Đồ án

Dự án này tập trung vào việc thu thập, xử lý và phân tích dữ liệu thời tiết tại khu vực Huế, Việt Nam. Động lực chính của dự án xuất phát từ sự kiện mưa lũ lịch sử vào cuối tháng 10 và đầu tháng 11 năm 2025, gây thiệt hại nghiêm trọng.

Mục tiêu của dự án là tìm hiểu các quy luật khí tượng, các yếu tố tác động đến lượng mưa và xây dựng mô hình dự báo để hỗ trợ công tác cảnh báo sớm.

---
### 3. Tổng quan dataset
#### 3.1. Thu thập dữ liệu
Dữ liệu được thu thập từ **Meteostat API**, các đặc trưng gồm:
- latitude, longitude: cặp (vĩ độ, kinh độ)
- datetime: thời điểm dữ liệu được ghi lại theo giờ trong ngày.
- temperature_2m (độ C): nhiệt độ không khí được đo ở độ cao 2m so với mặt đất, trung bình theo giờ trong ngày.
- dewpoint_2m (độ C): nhiệt độ điểm sương, nhiệt độ hơi nước cần lạnh đi để đạt 100% độ ẩm, từ đó bắt đầu ngưng tụ.
- relativehumidity_2m (%): độ ẩm tương đối (lương hơi nước trong không khí / lượng tối đa không khí ở nhiệt độ đó có thể giữ).
- precipitation (mm): lượng mưa.
- windspeed_10m (km/h): tốc độ gió ở độ cao 10m so với mặt đất.
- winddirection_10m (độ): hướng gió.
- pressure_msl (hPa): áp suất tại mực nước biển trung bình, là chuẩn để phân biệt áp cao/thấp.

#### 3.2. Tiền xử lý
Dữ liệu có missing values, được điền bằng KNN.
---

4. GUGUGAGA
---
### 5. Cấu trúc Dự án

```
  ├── data/ 
  |   ├── raw/
  |   |    └── weather_raw.csv # Dữ liệu thô
  |   └── processed/
  |   |    ├── weather_processed.csv # Dữ liệu đã qua xử lý
  |   |    ├── test_data.csv # Tập test
  |   |    └── train_data.csv # Tập train
  ├── 01_data_collection.ipynb # Quá trình thu thập dữ liệu
  ├── 02_data_preprocessing.ipynb # Qua trình tiền xử lý
  ├── 03_data_analysis/
  |   ├── 03_Q1_data_analysis.ipynb # Các yếu tố thời tiết (nhiệt độ, độ ẩm, gió, áp suất…) có tác động và mức độ tương quan như thế nào đến lượng mưa
  |   ├── 03_Q2_data_analysis.ipynb # Cường độ, thời gian kéo dài và tần suất của các trận mưa có đặc điểm gì?
  |   ├── 03_Q3_data_analysis.ipynb # Cơ chế tương tác giữa chu kỳ thời gian (mùa/giờ) và các yếu tố hoàn lưu khí quyển (áp suất/gió) định hình quy luật và cường độ mưa như thế nào ? 
  |   └── 03_Q4_data_analysis.ipynb # Trong và trước các trận mưa lịch sử tháng 10–11/2025 vừa rồi ở Huế, những biến khí tượng nào thể hiện sự thay đổi rõ rệt nhất, có gì khác biệt so với các trận còn lại không?
  └── 04_modeling.ipynb # Xây dựng mô hình học máy (Machine Learning) để dự đoán khả năng mưa hoặc lượng mưa dựa trên các đặc trưng đã xử lý.
```

---

### 6. Yêu cầu hệ thống
Để chạy được các notebook, hệ thống cần có các thư viện Python sau:
```bash
pip install pandas numpy matplotlib seaborn plotly windrose scikit-learn
```

---

### 7. Kết luận của dự án
1. Vai trò của Độ ẩm: Độ ẩm là biến số quan trọng nhất ("nhiên liệu" cho mưa). Khi độ ẩm bão hòa kết hợp với điều kiện địa hình Huế, mưa lớn rất dễ xảy ra.

2. Cảnh báo sớm: Đối với các trận mưa lịch sử (2025), dấu hiệu nhận biết không phải là sự biến động áp suất tức thời mà là sự tích tụ độ ẩm cao trong khí quyển kéo dài nhiều ngày trước đó.

3. Tương tác Mùa: Mô hình dự báo cần đặc biệt chú ý đến biến tương tác giữa pressure (áp suất) và season (mùa) để cải thiện độ chính xác.


