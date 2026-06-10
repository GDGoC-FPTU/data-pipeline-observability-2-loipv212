# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600784
**Name:** Phạm Văn Lợi
**Date:** 10/06/2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 10 | Agent trả về kết quả đúng với sản phẩm phù hợp. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 1 | Agent bị đánh lừa bởi dữ liệu lỗi do outlier giá. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi chạy với bộ dữ liệu Garbage Data (dữ liệu rác/bị nhiễm độc), Agent đã đưa ra một câu trả lời hoàn toàn vô lý là "Nuclear Reactor" thay vì một sản phẩm thông thường. Điều này xảy ra do hệ thống logic của Agent phụ thuộc hoàn toàn vào dữ liệu đầu vào. Dữ liệu rác chứa các giá trị outliers cực đoan (giá lên tới $999999) và phân loại sai lệch. Khi Agent áp dụng logic "tìm sản phẩm có giá cao nhất", nó đã tự động bị dẫn dắt bởi bản ghi nhiễu này. Nếu không có bước ETL để lọc bỏ outlier và làm sạch dữ liệu từ đầu, Agent RAG sẽ trở nên vô dụng hoặc thậm chí đưa ra các quyết định nguy hiểm trong môi trường thực tế, vì bản thân LLM/Agent không thể tự biết đâu là dữ liệu rác nếu chúng ta không có Data Pipeline chuẩn.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Đồng ý hoàn toàn.

Dù prompt của bạn có tinh vi đến đâu, nếu dữ liệu truyền vào hệ thống (context/knowledge base) bị sai lệch (Garbage in), kết quả trả ra chắc chắn sẽ là sai lệch (Garbage out). Dữ liệu chất lượng cao là nền tảng cốt lõi không thể thay thế cho bất kỳ hệ thống AI nào.
