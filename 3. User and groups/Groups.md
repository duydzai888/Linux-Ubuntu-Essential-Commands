# Groups
## Menu
[1. Người giới thiệu](#NguoiGioiThieu)

[2. Liệt kê các nhóm của quy trình hiện tại ( groups )](#LietKeCacNhom)

[3. Thêm nhóm mới ( groupadd )](#ThemNhomMoi)

[4. Xóa một nhóm ( groupdel )](#XoaNhom)



<a name="NguoiGioiThieu"></a>
### 1. Người giới thiệu
Xem trang [Ubuntu Server Guide](https://ubuntu.com/server/docs) để xem thông tin chi tiết về quản lí nhóm.

<a name="LietKeCacNhom"></a>
### 2. Liệt kê các nhóm của quy trình hiện tại ( groups )
- In các nhóm cho quy trình hiện tại:
```
$ groups
mtitek group1 group2
```

- Bạn có thể in các nhóm của một người dùng cụ thể:
```
$ groups mtitek mtitek1
mtitek : mtitek group1 group2
mtitek1 : mtitek1
```

<a name="ThemNhomMoi"></a>
### 3. Thêm nhóm mới ( groupadd )
- Sử dụng lệnh `groupadd` để thêm một nhóm mới ( man groupadd ):
```
Cách sử dụng: groupadd [options] GROUP

Options:
  -f, --force  thoát thành công nếu nhóm đã tồn tại
```

Ví dụ: Tạo 1 nhóm mới có tên `newgroup`
```
$ sudo groupadd newgroup

$ cat /etc/group | grep newgroup
newgroup:x:1005:
```

<a name="XoaNhom"></a>
### 4. Xóa một nhóm ( groupdel )
Ví dụ: Xóa nhóm `newgroup`:
```
$ sudo groupdel newgroup
```