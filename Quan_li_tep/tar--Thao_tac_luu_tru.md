# tar - Thao tác lưu trữ băng
## Menu
[1. Ghi chú](#GhiChu)

[2. Các ví dụ](#ViDu)
- [2.1. Tạo tệp lưu trữ](#TaoTepLuuTru)
- [2.2. Liệt kê nội dung kho lưu trữ](#LietKeNoiDungKhoLuuTru)
- [2.3. Giải nén nội dung lưu trữ vào đĩa](#GiaiNenNoiDungLuuTruVaoDia)
- [2.4. Lưu trữ tệp và nén tệp bằng tùy chọn `-z`](#LuuTruTepVaNenTep)
- [2.5. Giải nén tệp và giải nén tệp lưu trữ bằng tùy chọn `-z`](#GiaiNenTep)

[3. Lệnh trợ giúp](#LenhTroGiup)
- [3.1. Các tùy chọn sau quyết định chế độ tar lệnh sẽ sử dụng](#CacTuyChon)
- [3.2. Các tùy chọn bổ sung sau có thể được sử dụng](#TuyChonBoSung)


<a name="GhiChu"></a>
### 1. Ghi chú.
Bạn có thể sử dụng các tùy chọn `-z` hoặc `-j` để chuyển hướng đầu ra đến các lệnh **gzip** hoặc **bzip2** để nén.

Bạn có thể sử dụng `gzip` và `gunzip` để nén và giải nén các tệp lưu trữ: gzip - nén / giải nén.

<a name="ViDu"></a>
### 2. Các ví dụ.

<a name="TaoTepLuuTru"></a>
##### 2.1. Tạo tệp lưu trữ.
- Lưu trữ một thư mục
```
$ tar -cf archive1.tar folder1

#Danh sách nội dung lưu trữ
$ tar -tf archive1.tar
folder1/
folder1/file1
```

- Chỉ lưu trữ nội dung của thư mục
```
$ tar -cf archive1.tar folder1/*
#Danh sách nội dung lưu trữ
$ tar -tf archive1.tar
```

<a name="LietKeNoiDungKhoLuuTru"></a>
##### 2.2. Liệt kê nội dung kho lưu trữ.
- Liệt kê nội dung lưu trữ thành đầu ra tiêu chuẩn
```
$ tar -tf archive1.tar
folder1/
folder1/file1
```

- Sử dụng `-v` tùy chọn để hiển thị chi tiết bổ sung về nội dung lưu trữ
```
$ tar -tvf archive1.tar
drwxr-xr-x 0 mtitek mtitek 0 1 tháng 2 20:44 thư mục1 /
-rw-r - r-- 0 mtitek mtitek 4 3 tháng 2 19:56 folder1 / file1
```

<a name="GiaiNenNoiDungLuuTruVaoDia"></a>
##### 2.3. Giải nén nội dung lưu trữ vào đĩa.
- Nội dung lưu trữ sẽ được giải nén vào thư mục `folder1`
```
$ tar -xf archive1.tar
$ ls -al folder1/
-rw-r - r-- 1 mtitek mtitek 4 3 tháng 2 19:56 file1
```

- Sử dụng `-m` tùy chọn để không trích xuất thời gian sửa đổi
```
$ tar -xmf archive1.tar
$ ls -al folder1/
-rw-r - r-- 1 mtitek mtitek 4 3 tháng 2 20:39 file1
```

<a name="LuuTruTepVaNenTep"></a>
##### 2.4. Lưu trữ tệp và nén tệp bằng tùy chọn `-z`.
```
$ tar -cvzf archive1.gz file1
file1
```

<a name="GiaiNenTep"></a>
##### 2.5. Giải nén tệp và giải nén tệp lưu trữ bằng tùy chọn `-z`.
```
$ tar -xvzf archive1.gz -C archive1
file1
```

<a name="LenhTroGiup"></a>
### 3. Lệnh trợ giúp ( man tar )

<a name="CacTuyChon"></a>
##### 3.1. Các tùy chọn sau quyết định chế độ tar lệnh sẽ sử dụng
```
-NS
| Tạo một kho lưu trữ mới chứa các tệp / thư mục được chỉ định.

-NS
| Giống như -c, nhưng các tệp / thư mục mới được thêm vào kho lưu trữ.
| Lưu ý rằng điều này chỉ hoạt động trên các tệp lưu trữ không nén được lưu trữ trong các tệp thông thường.
| Tùy chọn -f là bắt buộc.

-u
| Giống như -r, nhưng các tệp / thư mục mới chỉ được thêm vào nếu chúng có ngày sửa đổi mới hơn so với tệp / thư mục tương ứng trong kho lưu trữ.
| Lưu ý rằng điều này chỉ hoạt động trên các tệp lưu trữ không nén được lưu trữ trong các tệp thông thường.
| Tùy chọn -f là bắt buộc.

-NS
| Liệt kê nội dung lưu trữ thành đầu ra tiêu chuẩn.

-NS
| Giải nén vào đĩa từ kho lưu trữ.
| Nếu một tệp có cùng tên xuất hiện nhiều lần trong kho lưu trữ, mỗi bản sao sẽ được trích xuất, với các bản sao sau sẽ ghi đè (thay thế) các bản sao trước đó.
```

<a name="TuyChonBoSung"></a>
##### 3.2. Các tùy chọn bổ sung sau có thể được sử dụng:
```
-f file
| Đọc / ghi kho lưu trữ từ / vào tệp được chỉ định.
| Tên tệp có thể là - cho đầu vào tiêu chuẩn hoặc đầu ra tiêu chuẩn.

-C Directory
| Thay đổi kết quả đầu ra thành thư mục được chỉ định.

-z
| Chuyển hướng đầu ra đến lệnh gzip để nén.

-j
| Chuyển hướng đầu ra đến lệnh bgzip2 để nén.

-m
| (chỉ chế độ x)
| Không trích xuất thời gian sửa đổi.
| Theo mặc định, thời gian sửa đổi được đặt thành thời gian được lưu trữ trong kho lưu trữ.

-w
| Yêu cầu xác nhận cho mọi hành động.

-v
| Sản xuất đầu ra dài dòng.
| Trong chế độ tạo và giải nén, tar sẽ liệt kê từng tên tệp khi nó được đọc hoặc ghi vào kho lưu trữ.
| Trong chế độ danh sách, tar sẽ tạo ra đầu ra tương tự như của ls.
```
