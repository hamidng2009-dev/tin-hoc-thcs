# Hướng dẫn quản lí trang Tin học THCS

## 1. Cấu trúc thư mục

```
tin-hoc-thcs/
├── index.html          (giao diện, ít khi phải sửa)
├── HUONG-DAN.md        (tệp này)
└── du-lieu/
    ├── lop6.json
    ├── lop7.json
    ├── lop8.json
    └── lop9.json
```

## 2. Cách cập nhật nội dung

1. Mở repo trên GitHub, vào tệp cần sửa (ví dụ `du-lieu/lop6.json`).
2. Bấm biểu tượng cây bút, sửa nội dung, bấm **Commit changes**.
3. Đợi Vercel khoảng nửa phút, mở trang và bấm Ctrl+F5.

Nếu tệp quá lớn để sửa trên web, dùng **Add file → Upload files** để tải tệp mới lên (tệp cùng tên sẽ được thay).

## 3. Cấu trúc tệp `lopN.json`

Mỗi tệp có hai phần: `chude` (các chủ đề và bài học) và `de` (các đề tham khảo).

### Một bài học

```json
{"so":1,"ten":"Tên bài",
 "tt":["Ý tóm tắt 1","Ý tóm tắt 2"],
 "kn":"Khái niệm cần nhớ",
 "vd":"Ví dụ minh hoạ",
 "tn":[{"q":"Câu hỏi?","o":["Đáp án ĐÚNG","Sai 1","Sai 2","Sai 3"],"a":0,"g":"Giải thích ngắn"}],
 "tl":[["Đề tự luận","Gợi ý đáp án"]]}
```

- `tn`: trắc nghiệm. **Luôn đặt đáp án đúng đầu tiên trong `o` và để `"a":0`**; trang tự xáo trộn thứ tự khi hiển thị.
- `so` có thể là số (`5`) hoặc chữ (`"8a"`).

### Một đề tham khảo (trong mảng `de`)

```json
{"ten":"Tên đề","tg":"Mô tả ngắn",
 "tn":[ ...câu trắc nghiệm như trên... ],
 "ds":[{"de":"Về chủ đề...","y":[["Phát biểu a",true,"Giải thích"],["Phát biểu b",false,"Giải thích"]]}],
 "tln":[{"q":"Câu hỏi?","a":"đáp án","k":["đáp án khác chấp nhận được"],"g":"Giải thích"}],
 "tl":[["Đề tự luận","Gợi ý"]]}
```

- `ds` (đúng/sai) và `tln` (trả lời ngắn) là tuỳ chọn; có thể bỏ nếu không cần.
- Trong `tln`, trang so khớp không phân biệt hoa thường và khoảng trắng.

## 4. Lỗi thường gặp khi sửa tệp JSON

- Thiếu hoặc thừa dấu phẩy giữa các phần tử (không có dấu phẩy sau phần tử cuối).
- Dùng dấu nháy kép `"` bên trong nội dung: phải viết `\"`.
- Sau khi sửa, có thể dán nội dung vào một trang kiểm tra JSON trực tuyến (tìm "JSON validator") để xem có lỗi không.
- Nếu trang báo "đang được cập nhật" cho một lớp, thường là tệp JSON của lớp đó bị lỗi cú pháp.
