# df -- Display free disk space
# Menu
[1. Ghi chú](#GhiChu)

[2. Các ví dụ](#ViDu)

[3. Lệnh trợ giúp](#LenhTroGiup)


<a name="GhiChu"></a>
### 1. Ghi chú
- Đối với mỗi hệ thống tệp được chỉ định, lệnh `df` hiển thị số liệu thống kê về dung lượng ổ đĩa trống trên hệ thống tệp được chỉ định.

- Đối với mỗi tệp hoặc thư mục được chỉ định, lệnh `df` hiển thị số liệu thống kê về dung lượng ổ đĩa trống trên hệ thống tệp mà tệp hoặc thư mục là một phần.

- Nếu không có lệnh nào được chỉ định, lệnh `df` sẽ hiển thị số liệu thống kê cho tất cả các hệ thống tệp được gắn kết.

Giá trị dung lượng ổ đĩa được hiển thị trong 512 byte cho mỗi số khối.

<a name="ViDu"></a>
### 2. Các ví dụ
- Hiển thị thống kê cho tất cả các hệ thống tệp ở đầu ra `con người có thể đọc được`
```
$ df -H
Filesystem      Size   Used  Avail  Capacity  iused     ifree     %iused  Mounted on
/dev/disk1      1000G  500G  500G   50%       -         -         50%     /disk1
devfs           500k   500k  0B     100%      -         0         100%    /dev1
foofs           0B     0B    0B     100%      0         0         100%    /foo1
barfs           0B     0B    0B     100%      0         0         100%    /bar1
```

- Chỉ hiển thị thống kê cho các hệ thống tệp thuộc các loại được chỉ định
```
$ df -HT devfs,hfs
Filesystem      Size   Used  Avail  Capacity  iused     ifree     %iused  Mounted on
/dev/disk1      1000G  500G  500G   50%       -         -         50%     /disk1
devfs           500k   500k  0B     100%      -         0         100%    /dev1
```

- Hiển thị thống kê cho tất cả các hệ thống tệp ngoại trừ các loại được chỉ định.
```
$ df -HT nodevfs,hfs
foofs           0B     0B    0B     100%      0         0         100%    /foo1
barfs           0B     0B    0B     100%      0         0         100%    /bar1
```

- (OS X) Hiển thị các hệ thống tập tin có sẵn trên hệ thống
```
$ lsvfs
Filesystem
----------
nfs
hfs
devfs
CoreStorage
autofs
```

<a name="LenhTroGiup"></a>
### 3. Lệnh trợ giúp ( man df )
```
-a
| Hiển thị tất cả các hệ thống tệp được gắn kết.

-l
| Chỉ hiển thị thông tin về hệ thống tệp được gắn cục bộ.

-i
| Bao gồm thống kê về số lượng inodes miễn phí.
| Tùy chọn này hiện là mặc định để tuân theo Phiên bản 3 của Thông số UNIX Đơn (`` SUSv3 '')
| Sử dụng -P để chặn đầu ra này.

-T
| Chỉ hiển thị số liệu thống kê cho các hệ thống tệp thuộc các loại được chỉ định.
| Có thể chỉ định nhiều loại trong danh sách được phân tách bằng dấu phẩy.
| Danh sách các loại hệ thống tệp có thể được bắt đầu bằng "không" để chỉ định các loại hệ thống tệp không nên thực hiện hành động nào.
| Lệnh lsvfs có thể được sử dụng để hiển thị các hệ thống tệp có sẵn trên hệ thống.

-H
| Đầu ra "có thể đọc được của con người".
| Sử dụng các hậu tố đơn vị: Byte (-b), Kilobyte (-k), Megabyte (-m), Gigabyte (-g) để giảm số chữ số xuống còn ba hoặc ít hơn bằng cách sử dụng cơ số 10 cho các kích thước.

-h
| Đầu ra "có thể đọc được của con người".
| Sử dụng các hậu tố đơn vị: Byte (-b), Kilobyte (-k), Megabyte (-m), Gigabyte (-g) để giảm số chữ số xuống còn ba hoặc ít hơn bằng cách sử dụng cơ số 2 cho các kích thước.

-b (mặc định)
| Sử dụng khối 512 byte.
| Điều này chỉ hữu ích như một cách để ghi đè thông số BLOCKSIZE khỏi môi trường.

-k
| Sử dụng các khối 1024 byte (1-Kbyte).
| Lưu ý rằng điều này ghi đè thông số kỹ thuật BLOCKSIZE từ môi trường.

-m
| Sử dụng khối 1048576 byte (1-Mbyte).
| Lưu ý rằng điều này ghi đè thông số kỹ thuật BLOCKSIZE từ môi trường.

-g
| Sử dụng blockst 1073741824 byte (1-Gbyte).
| Lưu ý rằng điều này ghi đè thông số kỹ thuật BLOCKSIZE từ môi trường.
```