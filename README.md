# 📊 Dự báo Lưu lượng Mạng Internet theo Chu kỳ Giờ/Ngày  

## 🚀 Giới thiệu  
Trong thời đại số, lưu lượng truy cập Internet biến động mạnh theo giờ và ngày trong tuần. Việc dự báo chính xác các chu kỳ cao điểm giúp:  
- Tối ưu hóa phân bổ tài nguyên hệ thống.  
- Tránh tình trạng quá tải hoặc gián đoạn dịch vụ.  
- Hỗ trợ lập kế hoạch bảo trì và mở rộng hệ thống.  

Dự án này sử dụng **Biến đổi Fourier nhanh (FFT)** để phân tích chu kỳ và dự báo lưu lượng mạng trong tương lai.  

---

## 🎯 Mục tiêu  
- Phân tích chu kỳ cao điểm/lặp lại trong dữ liệu.  
- Dự báo lưu lượng truy cập trong tương lai gần.  
- Trực quan hóa dữ liệu để hiểu hành vi sử dụng Internet theo giờ/ngày.  

---

## 📂 Dữ liệu  
Nguồn dữ liệu: [Web Traffic Time Series Dataset](https://www.kaggle.com/datasets/raminhuseyn/web-traffic-time-series-dataset)  

- **Timestamp**: Thời gian ghi nhận lưu lượng.  
- **TrafficCount**: Số lượt truy cập tại thời điểm đó.  

---

## ⚙️ Các bước thực hiện  

### 1. Tiền xử lý dữ liệu  
- Chuyển cột thời gian về dạng `datetime`.  
- Tạo thêm cột `hour`, `weekday` để phân tích.  

### 2. Trực quan hóa dữ liệu  
- Lưu lượng trung bình theo giờ trong ngày.  
- Lưu lượng trung bình theo ngày trong tuần.  

### 3. Phân tích chu kỳ bằng FFT  
- Tìm tần số trội (dominant frequency).  
- Xác định chu kỳ lặp lại trong dữ liệu.  

### 4. Dự báo  
- Xây dựng mô hình **hàm sin** khớp với dữ liệu.  
- Dự báo lưu lượng cho **48 giờ tiếp theo**.  

---

## 📈 Kết quả  
- Xác định được các chu kỳ rõ ràng:  
  - Lưu lượng **cao** vào buổi trưa (11h–12h) và giờ hành chính.  
  - Lưu lượng **giảm mạnh** vào cuối tuần.  
- Mô hình hàm sin dự báo được xu hướng cho tương lai ngắn hạn.  

---

## 🔮 Hướng phát triển  
- Thử nghiệm với các mô hình tiên tiến hơn: **ARIMA, LSTM, Transformer**.  
- Kết hợp thêm yếu tố **thời tiết, sự kiện, kỳ nghỉ lễ** để tăng độ chính xác.  
- Xây dựng hệ thống **cảnh báo lưu lượng theo thời gian thực**.  

---

## 🛠️ Công nghệ sử dụng  
- Python (`pandas`, `numpy`, `matplotlib`, `scipy`)  
- **FFT (Fast Fourier Transform)**  
- **Curve fitting** (`scipy.optimize.curve_fit`)  

---

## 📌 Cách chạy dự án  

```bash
# Clone repo
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>

# Cài đặt thư viện
pip install -r requirements.txt

# Chạy phân tích & dự báo
python main.py
