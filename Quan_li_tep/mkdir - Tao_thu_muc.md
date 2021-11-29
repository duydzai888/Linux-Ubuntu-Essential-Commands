# mkdir - Tạo thư mục
## Menu
[1. Ghi chú](#GhiChu)

[2. Các ví dụ](#ViDu)
- [2.1. Tạo 1 thư mục](#TaoMotThuMuc)
- [2.2. Tạo nhiều thư mục và tùy chọn các thư mục con của chúng](#TaoNhieuThuMuc)
- [2.3. Sử dụng tùy chọn -p để tạo một thư mục con và thư mục cha của nó nếu chúng không tồn tại](#SuDungTuyChon)
- [2.4. Tạo một thư mục với một quyền cụ thể](#TaoThuMucVoiQuyenCuThe)

[3. Lệnh trợ giúp ( man mkdir )](#LenhTroGiup)

<a name="GhiChu"></a>
### 1. Ghi chú
Người dùng phải có quyền ghi trong thư mục mẹ.

<a name="ViDu"></a>
### 2. Các ví dụ

<a name="TaoMotThuMuc"></a>
##### 2.1. Tạo 1 thư mục
```
[root@Sever ~]# mkdir folder
```

<a name="TaoNhieuThuMuc"></a>
##### 2.2. Tạo nhiều thư mục và tùy chọn các thư mục con của chúng:
```
[root@Sever ~]# mkdir folder folder/folder1 folder/folder2
```

<a name="SuDungTuyChon"></a>
##### 2.3 Sử dụng tùy chọn -p để tạo một thư mục con và thư mục cha của nó nếu chúng không tồn tại:
```
[root@Sever ~]# mkdir -p folder/folder2
```

<a name="TaoThuMucVoiQuyenCuThe"></a>
##### 2.4 Tạo một thư mục với một quyền cụ thể:
```
[root@Sever ~]# mkdir -m 777 folder
```

<a name="LenhTroGiup"></a>
### 3. Lệnh trợ giúp ( man mkdir )
Các tùy chọn sau có thể được sử dụng:
```
-m <mode>
| Đặt chế độ cho phép tệp của thư mục đã tạo.
| Đối số mode có thể ở bất kỳ định dạng nào được chỉ định bởi lệnh chmod.
| Nếu một chế độ tượng trưng được chỉ định, các ký tự hoạt động "+" và "-" được diễn giải liên quan đến chế độ ban đầu của "a = rwx".

-P
| Tạo các thư mục trung gian theo yêu cầu.
| Nếu tùy chọn này không được chỉ định, tiền tố đường dẫn đầy đủ của mỗi toán hạng phải đã tồn tại.
| Mặt khác, với tùy chọn này được chỉ định, sẽ không có lỗi nào được báo cáo nếu một thư mục được cung cấp dưới dạng toán hạng đã tồn tại.
| Các thư mục trung gian được tạo với các bit quyền của rwxrwxrwx (0777) như được sửa đổi bởi umask hiện tại, cộng với quyền ghi và tìm kiếm cho chủ sở hữu.

-v
| Vì mkdir dài dòng, hiển thị các tệp khi chúng được tạo.
```