# chmod - Thay đổi chế độ tệp
## Menu
[1. Ghi chú](#GhiChu)

[2. Các ví dụ](#ViDu)

[3. Lệnh trợ giúp](#LenhTroGiup)




<a name="GhiChu"></a>
### 1. Ghi chú
Các `chmod` lệnh có thể được sử dụng để thay đổi chế độ tập tin của tập tin và thư mục.

Các `chmod` lệnh cũng có thể được sử dụng để sửa đổi các Access Control Lists (ACL) gắn liền với các tập tin và thư mục: chmod - thay đổi ACL tập tin (Access Control Lists) .

Tệp (và thư mục) có quyền sở hữu được đặt cho người dùng, nhóm hoặc những người khác. Mỗi người trong số họ có thể xác định ba loại quyền thông thường: đọc `r`, ghi (w) và thực thi `x`. Ký tự gạch ngang `-` được sử dụng khi không đặt quyền. Quyền đối với tệp (hoặc thư mục) được đặt bằng cách sử dụng 9 bit `rwxrwxrwx` xác định quyền đọc, ghi và thực thi cho người dùng, nhóm và những người khác. 3 bit đầu tiên xác định quyền đọc, ghi và thực thi cho người dùng, 3 bit tiếp theo cho nhóm và 3 bit cuối cùng cho những người khác.

Theo mặc định, quyền của một tệp (hoặc thư mục) mới tạo được đặt bằng giá trị `umask`(mặc định `002`). Để đặt quyền của tệp (hoặc thư mục) được tạo mới, giá trị của umask 002được kết hợp với quyền mặc định của tệp là `666`(hoặc thư mục `777`). Vì vậy, theo mặc định, một tệp được tạo mới có quyền `rw-rw-r--`( `664` ) và thư mục được tạo mới có quyền `rwxrwxr-x`( `775` ).

<a name="ViDu"></a>
### 2. Các ví dụ
- Đặt quyền `read`, `write` và `execute` thành `user`, `group` và `others` trên tệp "file1".

    Sử dụng bất kỳ lệnh nào sau đây:
```
$ chmod 777 file1

$ chmod ugo+rwx file1

$ chmod ugo=rwx file1

$ chmod a=rwx file1
```

- Đặt quyền `read`, `write` và `execute` thành `user` và đặt quyền `read` và `execute` thành `group` và `others` trên tệp "file1".

    Sử dụng bất kỳ lệnh nào sau đây:
```
$ chmod 755 file1

$ chmod u=rwx,go=rx file1

$ chmod u=rwx,go=u-w file1
```

- Thêm quyền `read` và `write` vào `user` và `group` trên tệp "file1".
Nếu người dùng hoặc nhóm đã có quyền thực thi, họ sẽ giữ quyền này.
```
$ chmod ug+rw file1
```

- Từ chối quyền `read` và `write` đối với `user` và `group` trên tệp "file1".
Nếu người dùng hoặc nhóm đã có quyền thực thi, họ sẽ giữ quyền này.
```
$ chmod ug-rw file1
```

- Từ chối tất cả quyền đối với `group` và `others` trên tệp "file1".

Sử dụng bất kỳ lệnh nào sau đây:
```
$ chmod go-rwx file1

$ chmod go= file1
```

- Đặt quyền `read`, `write` và `search/execute` thành `user`, `group` và `others` trên thư mục "folder1" và tất cả các tệp và thư mục con của nó.

Sử dụng bất kỳ lệnh nào sau đây:
```
$ chmod -R 777 folder1/

$ chmod -R ugo+rwx folder1/

$ chmod -R ugo=rwx folder1/

$ chmod -R a=rwx folder1/
```

<a name="LenhTroGiup"></a>
### 3. Lệnh trợ giúp ( man chmod )
- Các tùy chọn sau có thể được sử dụng:
```
-R
| Nếu chmod được áp dụng cho một thư mục, nó sẽ thay đổi chế độ của thư mục này và tất cả các tệp và thư mục con của nó.
| Theo mặc định, các tệp được liên kết của các liên kết tượng trưng sẽ không bị thay đổi.

-L
| Nếu tùy chọn -R được chỉ định, các tệp được liên kết của các liên kết tượng trưng sẽ bị thay đổi

-v
| Vì chmod dài dòng, hiển thị tên tệp nếu chế độ được sửa đổi.
| Nếu cờ -v được chỉ định hai lần, chế độ cũ và mới của tệp cũng sẽ được in, ở cả ký hiệu bát phân và ký hiệu tượng trưng.
```

- Chế độ biểu tượng có thể được mô tả bằng một trong các ngữ pháp sau.

Cú pháp ngắn gọn:
```
[ugoa]*([-+=]([rwx]*|[ugo]))+
```

- Biểu tượng ai chỉ định:
```
u: người dùng
g: nhóm
o: những người khác
a: all (tương đương với "ugo")
```

- Các ký hiệu quyền chỉ định:
```
r: quyền đọc.
w: quyền ghi.
x: quyền thực thi (tệp) | quyền tìm kiếm (thư mục).
```

- Các biểu tượng quyền có thể được biểu diễn bằng các giá trị số như sau:
```
r (đọc) = 4
w (ghi) = 2
x (thực hiện) = 1

r + w (đọc và ghi) = 6
r + x (đọc và thực thi) = 5
w + x (viết và thực thi) = 3

r + w + x (đọc, ghi và thực thi) = 7
```

- Các ký hiệu hoạt động chỉ định:
```
+
| Nếu không có giá trị nào được cung cấp cho quyền, phép toán "+" không có hiệu lực.
| Nếu không có giá trị nào được cung cấp cho ai, thì mỗi quyền được liệt kê sẽ được đặt cho chủ sở hữu.
| Nếu không, chế độ của giá trị ai và quyền được chỉ định được đặt.

-
| Nếu không có giá trị nào được cung cấp cho quyền, phép toán "-" không có hiệu lực.
| Nếu không có giá trị nào được cung cấp cho ai, thì mỗi quyền được liệt kê sẽ bị xóa cho chủ sở hữu, nhóm và những người khác.
| Nếu không, chế độ của giá trị ai và quyền được chỉ định sẽ bị xóa.

=
| Nếu không có giá trị nào được cung cấp cho quyền, tất cả các quyền sẽ bị xóa đối với các giá trị được liệt kê của ai.
| Nếu không có giá trị nào được cung cấp cho ai, thì mỗi quyền được liệt kê sẽ được đặt và quyền không được liệt kê sẽ bị xóa đối với chủ sở hữu, nhóm và những người khác.
| Nếu không có giá trị nào được cung cấp cho cả quyền và ai, tất cả các quyền sẽ bị xóa cho chủ sở hữu, nhóm và những người khác.
| Nếu không, mỗi quyền được liệt kê được đặt và quyền không được liệt kê sẽ bị xóa, đối với các giá trị được liệt kê của ai.
```

