# Reflection — Anti-pattern: coi vector index bên ngoài là nguồn sự thật

Anti-pattern tôi dễ gặp nhất là coi vector database là nơi lưu chính của embeddings mà
không đồng bộ sự kiện xóa. Tôi chủ yếu làm ứng dụng RAG: pipeline thường chỉ embed rồi
upsert vào vector DB, còn luồng delete không ai chịu trách nhiệm.

NB7 cho thấy hậu quả: sau khi xóa `user_042`, lakehouse trả 0 dòng nhưng index cũ vẫn
trả 8 tài liệu. Prompt RAG vẫn có thể lộ dữ liệu đã yêu cầu xóa, và sync upsert một chiều
không bao giờ tự sửa được. NB8 bổ sung: xóa ở version hiện tại chưa xóa version cũ cho đến
khi chạy retention + VACUUM.

Cách phòng tránh:
1. Bảng lakehouse (text, embedding, provenance) là system of record; vector DB chỉ là
   index dẫn xuất, dựng lại được.
2. Bật Change Data Feed để index nhận cả sự kiện delete.
3. Ghi `embedding_model` và table version vào index; định kỳ đối soát vector mồ côi.
4. Erasure end-to-end: delete → VACUUM → xóa khỏi index → audit.

Phạm vi dùng AI: xem [AI_USAGE.md](AI_USAGE.md).
