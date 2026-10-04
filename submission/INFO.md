# Submission Info

| Field | Value |
|---|---|
| Họ tên | Lê Minh Hiếu |
| MSSV | 2A202602848 |
| Mã bài | K4-Track02-Day18 |
| Repo | https://github.com/HieuLM7714/K4-Track02-Day18-LeMinhHieu-2A202602848-Lakehouse-Lab |
| Đường chạy | Lightweight (`deltalake` 1.x + `pyiceberg` + DuckDB + Polars) cho cả NB1–NB8; không dùng Spark |
| Python | 3.12.3 |
| Hệ điều hành | Windows 10 IoT Enterprise LTSC 2021 (10.0.19044), PowerShell |

## Kết quả kiểm tra

- `scripts/verify_lite.py`: 9/9 PASS
- `pytest`: 24/24 PASS
- `scripts/run_all.py`: 8/8 notebook PASS
- 8 notebook được thực thi bằng `jupyter nbconvert --execute` và lưu output tại `submission/notebooks/`
  (NB1 có thêm cell in `_delta_log/` + nội dung commit JSON; mỗi notebook có cell "Analysis" giải thích số liệu).

## Bài nộp

- Notebooks: [`notebooks/`](notebooks/)
- Screenshots: [`screenshots/`](screenshots/)
- Reflection: [`REFLECTION.md`](REFLECTION.md)
- AI usage: [`AI_USAGE.md`](AI_USAGE.md)
