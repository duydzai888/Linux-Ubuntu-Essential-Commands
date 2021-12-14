# cat -- Nối và in các tập tin
## Menu
[1. Ghi chú](#GhiChu)




<a name="GhiChu">
### 1. Ghi chú
Các lệnh `cat` có một danh sách tên tập tin cho các đối số của nó.
Nó xuất nội dung của những tệp đó trực tiếp ra đầu ra tiêu chuẩn, theo mặc định, được dẫn đến màn hình.


### 2. Các ví dụ
- Viết nội dung của 1 tệp:
```
$ cat file1
Ho va ten: Lai Khanh Duy 
Nam sinh: 2002
Noi o: Tuyen Quang
```
Có thể sử dụng tùy chọn `-n` để in số dòng:
```
$ cat -n file1 
     1	Ho va ten: Lai Khanh Duy
     2	Nam sinh: 2002
     3	Noi o: Tuyen Quang
```

- Viết nội dung của nhiều tệp:
```
$ cat file1 file2 file3
```

Viết nội dung của nhiều tệp lần lượt ( `enter EOF character ('^D') for each file` ):
```
$ cat file1 - file2 - file3
```


### 3. Lệnh trợ giúp ( man cat )
Các tùy chọn sau có thể được sử dụng:
```
-n
| Đánh số các dòng đầu ra, bắt đầu từ 1.

-b
| Đánh số các dòng đầu ra không trống, bắt đầu từ 1.

-v
| Hiển thị các ký tự không in để chúng có thể nhìn thấy được.
| Các ký tự điều khiển in ra dưới dạng "^ X" cho control-X; ký tự xóa (bát phân 0177) in ra dưới dạng "^?".
| Các ký tự không phải ASCII (với bộ bit cao) được in dưới dạng "M-" (cho meta), theo sau là ký tự cho 7 bit thấp.
```