# Ảnh còn cần chụp

Pipeline đạt 27/27 và DAG `lab_fail_retry_2A202602524` đạt 37 task success. Công cụ UI của phiên làm bài không có trình duyệt được kết nối nên chưa lưu được ảnh giao diện.

- Airflow http://localhost:8081, admin/admin: mở DAG day09_video_pipeline, run lab_fail_retry_2A202602524, Graph; lưu screenshots/airflow_graph.png và screenshots/airflow_retry_graph.png.
- Log silver_frames map index 18, attempt 1: có `simulated crash while extracting trip-06667`; lưu screenshots/fail_task_log.png. Log thật cũng được lưu tại evidence/airflow_fail_task.log.
- MinIO http://localhost:9001, minioadmin/minioadmin: mở bucket lake, lưu screenshots/minio_lake.png.
- Metabase http://localhost:3000/dashboard/2, lab@example.com / Day9-lab-pass!: lưu screenshots/metabase_dashboard.png, có câu SQL riêng ở cuối dashboard.

Compose Windows hiện dùng `docker compose -f docker-compose.yml -f work/compose.local.yml --profile orchestrate up -d --no-build`. Override trong work đổi cổng 8081, dùng script entrypoint bản LF và tắt LAB_FAIL_ONCE. File gốc của đề không đổi logic.

Trip được chọn tạm bằng cách bỏ chữ A, giữ toàn bộ chữ số trong MSSV: 2202602524 % 26 = 18, lấy phần tử 18 trong danh sách trip sắp xếp. MSSV đầy đủ vẫn được dùng trong split và JSON. Hướng dẫn gốc không định nghĩa cách xử lý MSSV chữ.
