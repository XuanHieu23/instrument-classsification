# instrument-classsification
D# 🎵 Instrument Classification Project (3 instruments)
link dataset : https://www.kaggle.com/datasets/soumendraprasad/musical-instruments-sound-dataset

## Thành viên nhóm
- **Hiếu**
- **Khang**
- **Nobita**
- **Dương**
- **Onip**
- | Thành viên | Branch                       | Phần chính phụ trách                          |
| ---------- | ---------------------------- | --------------------------------------------- |
| **Hiếu**   | `feature-train-pipeline`     | Pipeline huấn luyện và tinh chỉnh mô hình     |
| **Khang**  | `feature-model-eval`         | Mô hình CNN + đánh giá + demo                 |
| **Nobita** | `feature-data-preprocessing` | Tiền xử lý và trích xuất đặc trưng            |
| **Dương**  | `feature-sample-test`        | Dữ liệu mẫu và kiểm thử                       |
| **Onip**   | `feature-visualization`      | Vẽ biểu đồ, confusion matrix và trực quan hóa |


---

## 🗓️ KẾ HOẠCH 6 NGÀY

### 🧩 Ngày 1 – Chuẩn bị dự án và dữ liệu
**Hiếu**
- Tạo khung thư mục dự án: `src/`, `data/`, `results/`, `docs/`, `notebooks/`, `saved_models/`.
- Tạo các file cơ bản: `README.md`, `.gitignore`, `requirements.txt`.

**Khang**
- Kiểm tra môi trường Python và cài các thư viện cần thiết (`librosa`, `tensorflow`, `numpy`, `matplotlib`).
- Lưu thông tin môi trường vào `env_check.txt`.

**Nobita**
- Tải dataset từ Kaggle và giải nén vào `data/raw/`.
- Thống kê số lượng file của từng nhạc cụ vào `data_status.md`.

**Dương**
- Chọn 3 file âm thanh mẫu (guitar, piano, violin) và lưu vào `data/sample/`.

**Onip**
- Tạo notebook `notebooks/exploration.ipynb`, load 1 file `.wav`, hiển thị waveform.

---

### 🧠 Ngày 2 – Tiền xử lý và trích xuất đặc trưng
**Nobita**
- Viết `src/data_preprocessing.py` để:
  - Đọc từng file âm thanh.
  - Trích xuất MFCC bằng `librosa.feature.mfcc()`.
  - Lưu `features.npy`, `labels.npy`, `labels.txt` vào `data/processed/`.

**Dương**
- Làm sạch dữ liệu, đổi tên file cho thống nhất, xóa file hỏng hoặc trùng.

**Onip**
- Vẽ spectrogram cho 3 loại nhạc cụ và lưu vào `results/`.

**Hiếu và Khang**
- Kiểm tra kết quả trích xuất, xác minh kích thước và định dạng dữ liệu.
- Lưu thông tin vào `data_shapes.txt`.

---

### ⚙️ Ngày 3 – Xây dựng mô hình cơ bản và pipeline huấn luyện
**Hiếu**
- Viết `src/model.py` để xây dựng mô hình MLP:
  - Dense(256, relu) → Dropout → Dense(128, relu) → Dense(3, softmax).

**Khang**
- Viết `src/train.py` (phiên bản thử) để:
  - Load dữ liệu từ `data/processed/`.
  - Chia train/test.
  - Train model 2 epochs để kiểm tra pipeline.
  - Lưu model tạm `saved_models/temp_model.h5`.

**Nobita**
- Kiểm tra đầu vào MFCC và đầu ra model có tương thích.

**Dương và Onip**
- Chạy thử huấn luyện và báo lỗi nếu có.

---

### 🚀 Ngày 4 – Huấn luyện đầy đủ và tinh chỉnh
**Khang**
- Cập nhật `train.py` để huấn luyện hoàn chỉnh:
  - Thêm EarlyStopping, ModelCheckpoint.
  - Train 40–50 epochs.
  - Lưu model tốt nhất `saved_models/best_model.h5`.

**Hiếu**
- Thử nghiệm tuning (batch_size, learning rate) và chọn cấu hình tốt nhất.
- Ghi kết quả tuning vào `tuning_log.md`.

**Nobita**
- Cập nhật tiền xử lý (chuẩn hóa dữ liệu, thêm augmentation nếu cần).

**Dương và Onip**
- Theo dõi quá trình huấn luyện và ghi nhận tình trạng overfitting.

---

### 📊 Ngày 5 – Đánh giá và trực quan hóa kết quả
**Khang**
- Viết `src/evaluate.py` để:
  - Load model tốt nhất.
  - In classification report.
  - Vẽ confusion matrix.

**Onip**
- Viết `src/visualization.py` để:
  - Vẽ biểu đồ accuracy và loss theo epochs.
  - Lưu `results/accuracy_loss.png` và `results/confusion_matrix.png`.

**Hiếu**
- Phân tích lỗi model, mô tả các loại nhạc cụ bị nhầm lẫn và nguyên nhân.

**Nobita**
- Thực hiện cross-validation đơn giản và ghi kết quả vào `validation_log.txt`.

**Dương**
- Chạy model trên các file trong `data/sample/` và lưu kết quả dự đoán.

---

### 🎬 Ngày 6 – Demo và hoàn thiện báo cáo
**Khang**
- Viết `src/demo.py` để dự đoán file âm thanh mới:

