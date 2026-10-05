# StudyNest

Một ứng dụng ôn bài nhỏ dành cho người bạn đang học từ nhiều ghi chú rời rạc. Bạn có thể lưu ghi chú, hỏi đáp dựa trên ghi chú, tạo 5 câu hỏi tự luyện và tóm tắt nhanh. Giao diện dùng tiếng Việt.

## Chạy ứng dụng

1. Tạo API key tại [Groq Console](https://console.groq.com/keys).
2. Cài Groq SDK: `python -m pip install -r requirements.txt`.
3. Sao chép `config_example.py` thành `config.py`, rồi dán **key mới** vào `GROQ_API_KEY` (giữa hai dấu nháy). Trong thư mục hiện tại, `config.py` đã được tạo sẵn. Key đã chia sẻ trong chat cần được thu hồi.
4. Chạy `python app.py` rồi mở `http://127.0.0.1:8000`.

Mặc định ứng dụng dùng model mở `openai/gpt-oss-20b` qua Groq; có thể đổi `GROQ_MODEL` trong `config.py`. File `config.py` nằm trong `.gitignore` để không bị commit lên Git. **Đừng chia sẻ file này hoặc đưa key vào README hay ảnh chụp màn hình.** Ghi chú sẽ được gửi tới Groq khi bạn bấm một chức năng AI; hãy cân nhắc trước khi nhập nội dung nhạy cảm. Giá và giới hạn sử dụng phụ thuộc tài khoản Groq.

## Vì sao AI mở quan trọng

Ứng dụng dùng model trọng số mở GPT-OSS qua Groq. Ghi chú được gửi tới Groq để xử lý AI và lưu trong localStorage của trình duyệt, nên đừng xóa dữ liệu trình duyệt nếu muốn giữ chúng lâu dài.

## Giới hạn

- Cần Groq API key và kết nối mạng để dùng các tính năng AI.
- Model có thể trả lời sai; hãy đối chiếu với ghi chú gốc.
- Ghi chú chỉ lưu trong một trình duyệt, chưa có đồng bộ hoặc xuất dữ liệu.
- Đây là prototype. Chưa có câu chuyện từ người dùng thật hoặc phản hồi sau khi bàn giao.

## Hacktoberfest Weekend Challenge

Ý tưởng phù hợp chủ đề **Build for a Friend**. Trước khi nộp, cần xác nhận người nhận thực tế, cho họ dùng thử, ghi lại phản hồi thật, quay/chụp demo và viết bài DEV bằng tiếng Anh theo [mẫu nộp bài](https://dev.to/challenges/hacktoberfest-weekend-2026-10-01). Không nên tuyên bố đã bàn giao hoặc đã có phản hồi nếu chưa thực hiện.
