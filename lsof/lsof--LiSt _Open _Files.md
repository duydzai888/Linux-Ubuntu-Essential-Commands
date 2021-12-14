# lsof (LiSt Open Files)
## Menu
[1. Liệt kê các tệp đang mở](#LietKeCacTepDangMo)

[2. Liệt kê các kết nối mạng](#LietKeCacKetNoiMang)

[3. Liệt kê các tệp đang mở của một người dùng cụ thể](#LietKeCacTepDangMoCUaMotNguoiDungCuThe)

[4. Liệt kê các tệp đang mở của một quy trình cụ thể](#LietKeCacTepDangMoCuaMotQuyTrinhCuThe)

[5. Liệt kê các quy trình đang lắng nghe trên một cổng cụ thể](#LietKeCacQuyTrinhDangLangNgheTrenMotCongCuThe)

[6. Hủy quy trình của một người dùng cụ thể](#HuyQuyTrinhCuaMotNguoiDungCuThe)






<a name="LietKeCacTepDangMo"></a>
### 1. Liệt kê các tệp đang mở
```
$ lsof
```

<a name="LietKeCacKetNoiMang"></a>
### 2. Liệt kê các kết nối mạng
```
$ lsof -i
```

<a name="LietKeCacTepDangMoCUaMotNguoiDungCuThe"></a>
### 3. Liệt kê các tệp đang mở của một người dùng cụ thể
```
$ lsof -u mtitek
```

<a name="LietKeCacTepDangMoCuaMotQuyTrinhCuThe"></a>
### 4. Liệt kê các tệp đang mở của một quy trình cụ thể
```
$ lsof -p 896
```

<a name="LietKeCacQuyTrinhDangLangNgheTrenMotCongCuThe"></a>
### 5. Liệt kê các quy trình đang lắng nghe trên một cổng cụ thể
```
$ lsof -i TCP:8080
```

<a name="HuyQuyTrinhCuaMotNguoiDungCuThe"></a>
### 6. Hủy quy trình của một người dùng cụ thể
```
$ kill -9 `lsof -t -u mtitek`
```
