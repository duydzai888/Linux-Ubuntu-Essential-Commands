# ls - Liệt kê nội dung thư mục





### 1. Ghi chú
- Đối với tệp, `ls` hiển thị tên và thông tin của từng tệp.

- Đối với thư mục, ls hiển thị tên và thông tin của tệp / thư mục chứa trong mỗi thư mục.

- Nếu không có tệp / thư mục nào được cung cấp, nội dung của thư mục hiện tại sẽ được hiển thị.

- Nếu có nhiều tệp / thư mục, các tệp sẽ được hiển thị trước tiên.

### 2. Các ví dụ
- (Tùy chọn -1 ) Liệt kê tên của từng tệp và thư mục trong một dòng:
![thư mục](https://user-images.githubusercontent.com/84270045/142849147-bf88dfbb-cce9-4a97-8a3a-3a0b810ef218.png)

- Liệt kê tên và thông tin của từng tệp và thư mục (bao gồm " . ", " .. " và các tệp và thư mục bắt đầu bằng " . "):
![-al](https://user-images.githubusercontent.com/84270045/142849377-4c893b71-e999-4e6d-8075-a20f812d3c57.png)

Lưu ý : đối với một thư mục, số byte (ví dụ: 4096) thể hiện kích thước của tệp meta chứa thông tin về thư mục. Nó không cung cấp bất kỳ thông tin nào về kích thước thực của các tệp và thư mục trong thư mục đó.

- Liệt kê các tệp và thông tin thư mục con với nội dung của chúng (bao gồm " . ", " .. " và các tệp và thư mục bắt đầu bằng " . "):
![thư mục](https://user-images.githubusercontent.com/84270045/142849639-b159cc4c-9d90-47a4-b7f4-4b482c318c07.png)

- (Tùy chọn -d ) Liệt kê các tệp và thông tin thư mục con mà không có nội dung của chúng (ngoại trừ " . ", " .. " và các tệp và thư mục bắt đầu bằng " . "):
![-d](https://user-images.githubusercontent.com/84270045/142849825-5ee8c5db-998b-41f2-9619-de8c9d70b799.png)

- (Tùy chọn -S ) Sắp xếp tệp và thư mục theo kích thước: `thư mục $ls -alS ~ /`
- (Tùy chọn -t ) Sắp xếp tệp và thư mục theo thời gian sửa đổi: `thư mục $ls -alt ~ /`

### 3. Lệnh trợ giúp (man ls)
- Các tùy chọn sau có thể được sử dụng:
```
-1
| Buộc đầu ra là một mục nhập trên mỗi dòng.

-R
| Liệt kê đệ quy các thư mục con gặp phải.

-l
| Liệt kê các tệp / thư mục ở định dạng dài.

-a
| Liệt kê tất cả các tệp / thư mục bao gồm cả "." và ".."

-A
| Liệt kê tất cả các tệp / thư mục ngoại trừ "." và ".."

-h
| Khi được sử dụng với tùy chọn -l, hãy sử dụng các hậu tố đơn vị:
| Byte, Kilobyte, Megabyte, Gigabyte, Terabyte và Petabyte để giảm số chữ số xuống còn ba hoặc ít hơn bằng cách sử dụng cơ số 2 cho các kích thước.

-e
| In Danh sách Kiểm soát Truy cập (ACL) được liên kết với tệp, nếu có, ở đầu ra dài (-l).

-S
| Sắp xếp tệp theo kích thước.

-t
| Sắp xếp theo thời gian được sửa đổi (lần sửa đổi gần đây nhất trước) trước khi sắp xếp các toán hạng theo thứ tự từ vựng.

-u
| Sử dụng thời gian của lần truy cập cuối cùng, thay vì lần sửa đổi cuối cùng của tệp để sắp xếp (-t) hoặc in lâu (-l).

-U
| Sử dụng thời gian tạo tệp, thay vì sửa đổi cuối cùng để sắp xếp (-t) hoặc đầu ra dài (-l).

-r
| Đảo ngược thứ tự sắp xếp để có được thứ tự từ vựng ngược lại hoặc các mục nhập cũ nhất trước tiên (hoặc các tệp lớn nhất sau cùng, nếu được kết hợp với sắp xếp theo kích thước.

-T
| Khi được sử dụng với tùy chọn -l, hiển thị thông tin thời gian đầy đủ cho tệp, bao gồm tháng, ngày, giờ, phút, giây.

-F
| Hiển thị dấu gạch chéo ('/') ngay sau mỗi tên đường dẫn là một thư mục,
| dấu hoa thị ('*') sau mỗi tệp có thể thực thi,
| một dấu ('@') sau mỗi liên kết tượng trưng,
| một dấu bằng ('=') sau mỗi ổ cắm,
| một dấu phần trăm ('%') sau mỗi dấu trắng,
| và một thanh dọc ('|') sau mỗi tệp là FIFO.

-i
| Đối với mỗi tệp, in số sê-ri tệp của tệp (số inode).

-n
| Hiển thị ID người dùng và nhóm dưới dạng số, thay vì chuyển đổi thành tên người dùng hoặc nhóm trong đầu ra dài (-l).
| Tùy chọn này bật tùy chọn -l.

-O
| Bao gồm các cờ tệp trong đầu ra dài (-l).

-G
| Bật đầu ra được tô màu.
```

Tùy chọn " -l " (hiển thị dài):
" -l " cung cấp thêm thông tin về tệp và thư mục.
Dòng đầu tiên của kết quả hiển thị tổng số khối có trong thư mục.
Các dòng sau liệt kê chi tiết của từng tệp và thư mục.
Mỗi dòng cung cấp các thông tin sau:

    - Loại tệp.
    
    - Quyền của tệp.
    
    - Số lượng liên kết cứng của tệp.
    
    - Tên người dùng của chủ sở hữu tệp.
    
    - Tên nhóm của nhóm chính của tệp.
    
    - Kích thước byte của tệp.
    
    - Lần cuối cùng tệp đã được sửa đổi.
    
    - Tên tệp.
    
- Tùy chọn `-l` hiển thị các ký tự sau cho loại tệp:
![tệp thông thường](https://user-images.githubusercontent.com/84270045/142851281-c24bc7d3-a773-4375-8bf7-548868d2eaba.png)

- Tùy chọn " -l " hiển thị các ký tự sau cho các quyền của tệp:
![sau](https://user-images.githubusercontent.com/84270045/142851472-200c108f-4241-4216-ae04-c8653cb7956f.png)

Đối với một tệp lệnh cụ thể, bạn có thể thấy ký tự `s` thay vì ký tự `x` ( -rwsrwsr-- ). Ký tự s có thể được đặt cho quyền của người dùng (setuid: đặt id người dùng khi thực thi) hoặc / và quyền nhóm (setgid: đặt id nhóm khi thực thi). Điều này cho phép người dùng thực thi lệnh nhưng quyền sở hữu lệnh đang chạy sẽ do người dùng hoặc nhóm sở hữu lệnh đó nắm giữ.

Đối với một số thư mục, bạn có thể thấy ký tự `t` thay vì ký tự `x` trong các quyền khác ( drwxrwxr-t). Điều này cho thấy rằng bit dính đã được bật cho chúng, có nghĩa là người dùng có thể thêm hoặc xóa các tệp trong các thư mục đó nhưng họ không thể xóa các tệp của nhau.

Đối với một số tệp và thư mục, bạn có thể thấy ký tự `+`` ở cuối các bit quyền ( -rwsrwsr - + ). Điều này có nghĩa là các tệp và thư mục đó có các thuộc tính bổ sung được gán cho chúng (tức là ACL).

