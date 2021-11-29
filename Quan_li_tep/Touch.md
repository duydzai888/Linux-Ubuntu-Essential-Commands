# Touch - Thay đổi thời gian truy cập và sửa đổi tệp
## Menu
[1. Ghi chú](#GhiChu)

[2. Các ví dụ](#ViDu)

[3. Lệnh trợ giúp ( man touch )](#LenhTroGiup)

<a name="GhiChu"></a>
### 1. Ghi chú
- Theo mặc định, `touch` lệnh thay đổi thời gian sửa đổi và truy cập của tệp.

- Nếu tệp không tồn tại, nó sẽ được tạo (tệp trống) với quyền mặc định (tên người dùng và tên nhóm của người dùng sẽ được sử dụng làm chủ sở hữu tệp).

<a name="ViDu"></a>
### 2. Các ví dụ
- Tạo tệp nếu nó không tồn tại: 
```
[root@Sever ~]# touch file1
[root@Sever ~]# ls -l file1
-rw-r--r--. 1 root root 0 Nov 19 03:30 file1
```

- Không tạo tệp nếu nó không tồn tại:
```
[root@Sever ~]# touch -c file2
[root@Sever ~]# ls file2
ls: cannot access file2: No such file or directory
```

<a name="LenhTroGiup"></a>
### 3. Lệnh trợ giúp ( man touch )
- Các tùy chọn sau có thể được sử dụng:

![touch](https://user-images.githubusercontent.com/84270045/143009907-b44af025-f65f-45e4-b382-62e65e9b9e50.png)


