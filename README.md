[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=24112713&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** lequocdai0303@gmail.com
**Name:** Phạm Văn Lợi

---

## Mo ta

Bài lab này tập trung vào việc xây dựng một đường ống dữ liệu (ETL Pipeline) tự động bằng Python. Em đã hoàn thành các bước đọc dữ liệu thô (JSON), kiểm tra và loại bỏ các dữ liệu không hợp lệ (giá trị <= 0 hoặc category trống), chuyển đổi dữ liệu (tính giá giảm 10%, chuẩn hóa category) và lưu trữ kết quả ra file CSV. Qua đó, em đã hiểu rõ tầm quan trọng của việc đảm bảo chất lượng dữ liệu trước khi cung cấp cho hệ thống AI phân tích và ra quyết định.

---

## Cach chay (How to Run)

### Prerequisites
Cài đặt thư viện pandas trước khi chạy:
```bash
pip install pandas
```

### Chay ETL Pipeline
Chạy file script để thực thi quy trình làm sạch dữ liệu:
```bash
python solution.py
```
Kết quả sẽ được lưu vào file `processed_data.csv`.

### Chay Agent Simulation (Stress Test)
Khởi tạo dữ liệu rác (Garbage Data) và kiểm tra ảnh hưởng của nó lên Agent so với dữ liệu chuẩn:
```bash
python generate_garbage.py
python agent_simulation.py
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- Dữ liệu thô ban đầu: 5 records
- Dữ liệu hợp lệ được xử lý thành công: 3 records
- Dữ liệu lỗi bị loại bỏ (giá âm, category rỗng): 2 records
- Hệ thống Agent Simulation cũng đã cho thấy sức mạnh của dữ liệu sạch: Agent trả lời chính xác với `processed_data.csv` nhưng lại bị đánh lừa đưa ra kết quả rác đối với `garbage_data.csv`.
