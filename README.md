# TH2 – Thư viện của lớp

Cấu trúc:
- `part-a/` – JavaScript thuần (module ES, fetch + async/await, localStorage).
- `part-b/` – React + Vite (component, props, children, useState).

## Chạy Phần A
Cần chạy qua server tĩnh (vì dùng ES module và fetch), ví dụ:
```bash
cd part-a
npx serve .        # hoặc dùng Live Server của VS Code
```
Muốn dùng mockapi.io: tạo resource `books` (id, title, author, genre, year), nhập ít nhất 10 cuốn rồi dán URL vào `API_URL` trong `part-a/js/api.js`. Khi đó nút **Thêm** gửi POST và nút **Xóa** gửi DELETE. Để trống thì dùng `books.json`.

## Chạy Phần B
```bash
cd part-b
npm install
npm run dev
```

## So sánh Phần A (DOM thuần) và Phần B (React)
| Tiêu chí | DOM thuần | React |
|---|---|---|
| Cách cập nhật giao diện | Tự tạo phần tử (`createElement`, `textContent`) rồi gắn vào DOM; phải nhớ vẽ lại khi dữ liệu đổi. | Mô tả giao diện theo state; khi `setState` React tự cập nhật phần thay đổi. |
| Tái sử dụng | Chia theo hàm/module (`createBookCard`, `renderBooks`). | Chia theo component (`BookCard`, `BookList`…), truyền dữ liệu bằng props, bọc nội dung bằng `children`. |
| Xử lý sự kiện | Event delegation: một listener ở lưới, dùng `closest` và `dataset.id` để biết thẻ nào. | Gắn `onClick` trực tiếp, truyền hàm xuống qua props; không cần delegation. |
| Quản lý dữ liệu | Biến toàn cục + gọi `update()` thủ công; dễ quên đồng bộ số yêu thích trên header. | State đặt ở `App`, header và danh sách cùng đọc từ một nguồn nên luôn đồng bộ. |
| Danh sách | Xóa và vẽ lại toàn bộ (`replaceChildren`). | Dùng `key` để React nhận ra phần tử nào đổi. |
| Công cụ | Không cần cài đặt, mở bằng server tĩnh. | Cần Node, Vite, bước build. |

**Nhận xét:** DOM thuần dễ hiểu, nhẹ, giúp nắm rõ trình duyệt hoạt động thế nào nhưng code dài và dễ lệch giữa dữ liệu với giao diện khi ứng dụng lớn. React cần học thêm khái niệm (component, state, JSX) nhưng code ngắn gọn, dễ chia nhỏ và bảo trì hơn.

## Yêu cầu nâng cao đã làm
- Nút Xóa gọi `DELETE` lên mockapi (Phần A, khi đặt `API_URL`).
- Chế độ sáng/tối ở cả hai phần.
- Chưa làm: viết Phần A bằng TypeScript.
