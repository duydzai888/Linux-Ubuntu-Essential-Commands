#  chown - Thay đổi chủ sở hữu tệp và nhóm
## Menu
[1. Ghi chú](#GhiChu)

[2. Các ví dụ](#ViDu)

[3. Lệnh trợ giúp ( man chown )](#LenhTroGiup)

<a name="GhiChu"></a>
### 1. Ghi chú
Các `chown` lệnh thay đổi chủ sở hữu và / hoặc nhóm các tập tin và thư mục.

<a name="ViDu"></a>
### 2. Các ví dụ
- Thay đổi chủ sở hữu của "folder1" thành "user1"
```
$ chown user1 folder1/
```

- Thay đổi chủ sở hữu của "folder1" (và các tệp và thư mục con của nó) thành "DOMAIN \ user2".
Sử dụng ký tự thoát `\` để thoát ký tự `\`.
Bạn cũng có thể sử dụng ký tự dấu ngoặc kép `"` để phân cách đường dẫn thư mục thoát ký tự `\`.
```
$ chown -R DOMAIN\\user2 folder1/

$ chown -R "DOMAIN\user2" folder1/
```

- Thay đổi chủ sở hữu của "folder1" thành "user3" và nhóm của nó thành "group3"
```
$ chown user3:group3 folder1/
```

- Thay đổi nhóm "folder1" thành "group4".
```
$ chown :group4 folder1/
```

<a name="LenhTroGiup"></a>
### 3. Lệnh trợ giúp
- Các tùy chọn sau có thể được sử dụng:
```
-R
| Nếu chown được áp dụng cho một thư mục, nó sẽ thay đổi chủ sở hữu / nhóm của thư mục này và tất cả các tệp và thư mục con của nó.
| Theo mặc định, các liên kết tượng trưng sẽ được thay đổi.
| Nhưng các tệp được liên kết của các liên kết tượng trưng sẽ không bị thay đổi.

-L
| Nếu tùy chọn -R được chỉ định, các liên kết tượng trưng sẽ không bị thay đổi.
| Nhưng các tệp được liên kết của các liên kết tượng trưng sẽ bị thay đổi.
| Tùy chọn -L ghi đè bất kỳ tùy chọn -P nào trước đó.
| Tùy chọn -L bị bỏ qua trừ khi tùy chọn -R được chỉ định.

-P
| Nếu tùy chọn -R được chỉ định, các liên kết tượng trưng sẽ được thay đổi.
| Nhưng các tệp được liên kết của các liên kết tượng trưng sẽ không bị thay đổi.
| Tùy chọn -P ghi đè bất kỳ tùy chọn -L nào trước đó.
| Tùy chọn -P bị bỏ qua trừ khi tùy chọn -R được chỉ định.

-v
| Vì chown là dài dòng, hiển thị tên tệp nếu chủ sở hữu / nhóm bị sửa đổi.
```
