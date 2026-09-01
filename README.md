# Rắn Mực — mô tả game

**Thể loại:** arcade cổ điển (biến thể Snake) · **Nền tảng:** web, chạy trực tiếp trên trình duyệt · **Chế độ:** chơi đơn, một người

## Ý tưởng

Snake cổ điển được kể lại bằng ngôn ngữ **mực và giấy**: con rắn là một vệt mực đen thon dần trườn trên trang giấy kẻ ô, thức ăn là những **chấm son đỏ**. Ăn được mồi thì vệt mực dài thêm; chết thì cả thân tan thành vết mực loang trên giấy — như một nét bút vừa bị đứt giữa dòng.

## Luật chơi

- Điều khiển con rắn di chuyển liên tục trên lưới vuông **22×22 ô**.
- **Ăn chấm son** → dài thêm một đốt, **+1 điểm**, mực son văng tung tóe kèm vòng tròn đỏ nở ra.
- **Thua** khi cắn vào thân mình hoặc trườn ra ngoài mép trang giấy.
- **Độ khó tăng dần:** mỗi chấm son ăn được, tốc độ tăng một chút — từ **×1.0** lúc mở màn lên tối đa khoảng **×2.3** (bước di chuyển rút ngắn từ 150ms xuống 64ms).
- Ô đuôi được tính là an toàn nếu không ăn mồi trong bước đó (luật Snake chuẩn, tránh chết oan).

## Điều khiển

| Hành động | Desktop | Mobile |
|---|---|---|
| Di chuyển | Mũi tên / WASD | Vuốt theo 4 hướng |
| Bắt đầu / tạm dừng / chơi lại | `Space` hoặc `Enter` | Chạm nhẹ vào bàn chơi |
| Tắt / bật âm thanh | `M` | — |

Có **hàng đợi hướng** (tối đa 3 lệnh): bấm nhanh hai ba phím liên tiếp vẫn rẽ đúng, không nuốt phím. Rời tab thì game tự tạm dừng.

## Nét riêng

- **Chuyển động mượt thật:** logic chạy theo tick trên lưới nhưng render nội suy giữa các bước — rắn trượt liên tục như nét mực chứ không nhảy từng ô.
- **Con rắn có biểu cảm:** thân vẽ như nét bút lông đậm ở đầu thon dần về đuôi; mắt là hai hạt giấy; **thè lưỡi son chẻ hai** khi mồi nằm ngay phía trước; khi chết mắt quay thành dấu **×** trước khi tan thành mực.
- **Âm thanh tự sinh** bằng WebAudio oscillator, không cần file — nốt ăn leo thang nhẹ theo chuỗi mồi liên tiếp.

## Giao diện & điểm số

Trang trình bày kiểu **một tờ báo in**: nền giấy kem có vân nhiễu, khung kẻ đôi, con dấu son đỏ "mực" cạnh tiêu đề, cặp chữ Fraunces + Space Grotesk. Bảng điểm gồm: **điểm hiện tại, kỷ lục, tốc độ, số ván đã chơi** — kỷ lục và số ván được lưu lại bằng `localStorage` (kỷ lục mới sẽ được đóng dấu "— kỷ lục mới —").

## Kỹ thuật

Toàn bộ nằm trong **một file HTML duy nhất**, không cần cài đặt hay server: Canvas 2D cho đồ họa, WebAudio cho âm thanh, không dùng file ảnh hay âm thanh ngoài. Chạy được cả trên desktop lẫn điện thoại.

---

Nếu bạn cần mô tả này cho mục đích cụ thể — README trên GitHub, trang giới thiệu trên itch.io, bài nộp môn học, hay bản rút gọn 2–3 câu — nói tôi, tôi viết lại theo đúng format đó.
