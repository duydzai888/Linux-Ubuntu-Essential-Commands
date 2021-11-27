# rm - Xóa tệp / thư mục
## Menu
[1. Ghi chú](#GhiChu)

[2. Các ví dụ](#ViDu)

[3. Lệnh trợ giúp ( man rm )](#LenhTroGiup)


<a name="GhiChu"></a>
### 1. Ghi chú
- Lệnh rm không thể đảo ngược. Trình bao không cung cấp Thùng rác nơi có thể khôi phục các tệp và thư mục đã xóa.
- Tùy chọn -i có thể được sử dụng để yêu cầu xác nhận trước khi xóa tệp hoặc thư mục.

<a name="ViDu"></a>
### 2. Các ví dụ
- Xóa tệp (xem tùy chọn dưới đây -i để yêu cầu xác nhận trước khi xóa tệp):
```
[root@Sever ~]# rm file1
```

- Xóa tất cả các tệp (không bao gồm các thư mục con và các tệp bắt đầu bằng dấu chấm (.)) Trong thư mục:
```
[root@Sever ~]# rm file1/*
```
Nó có thể thông báo rằng có các thư mục con trong folder1: `rm: folder1/folder11: is a directory`.

- Xóa tất cả các tệp bắt đầu bằng dấu chấm `.` trong một thư mục (không bao gồm các thư mục con).
```
[root@Sever ~]# rm file1/.*
```
Nó có thể hiển thị cảnh báo này: `rm: "." and ".." may not be removed`.

- Xóa thư mục:
```
[root@Sever ~]# rm -R folder1
```

<a name="LenhTroGiup"></a>
### 3. Lệnh trợ giúp ( man rm )
- Các tùy chọn sau có thể được sử dụng:

![man rm](https://user-images.githubusercontent.com/84270045/143028826-66a46d40-2120-4751-bce4-bcfbe168c851.png)