# chgrp - Thay đổi nhóm
## Menu


<a name="GhiChu"></a>
### 1. Ghi chú
Các `chgrp` lệnh làm thay đổi nhóm các tập tin và thư mục.

### 2. Các ví dụ
- Thay đổi nhóm "folder1" thành "group1".
```
$ chgrp group1 folder1/
```

- Thay đổi nhóm "folder1" (và các tệp và thư mục con của nó) thành "DOMAIN \ group2".
Sử dụng ký tự thoát `\` để thoát ký tự `\`.
Bạn cũng có thể sử dụng ký tự dấu ngoặc kép `"` để phân cách đường dẫn thư mục thoát ký tự `\`
```
$ chgrp -R DOMAIN\\group2 folder1/

$ chgrp -R "DOMAIN\group2" folder1/
```

### 3. Lệnh trợ giúp
- Các tùy chọn sau có thể được sử dụng:
```
-R
| Nếu chgrp được áp dụng cho một thư mục, nó sẽ thay đổi nhóm của thư mục này và tất cả các tệp và thư mục con của nó.
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
| Vì chgrp dài dòng, hiển thị tên tệp nếu nhóm bị sửa đổi.
```