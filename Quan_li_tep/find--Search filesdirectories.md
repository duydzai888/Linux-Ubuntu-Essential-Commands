# find -- Search files/directories
## Menu
[1. Ghi chú](#GhiChu)

[2. Các ví dụ](#CacViDu)
- [2.1. Tìm file](#TimFile)
- [2.2. Tìm kiếm thư mục](#TimKiemThuMuc)
- [2.3. Tìm kiếm tệp / thư mục với một tên cụ thể](#TimKiemTepThuMuc)
- [2.4. Tìm kiếm tệp / thư mục trong đó tên của tệp / thư mục chứa một mẫu cụ thể](#TimKiemTepChuaMotMauCuThe)
- [2.5. Tìm kiếm các tệp có chứa một từ cụ thể](#TimKiemTepCoChuaMotTuCuThe)
- [2.6. Tìm kiếm tệp và sử dụng lệnh `-exec` để thực hiện các lệnh cụ thể](#TimKiemVaSuDungLenhCuThe)
- [2.7. Tìm kiếm và xóa các tệp / thư mục](#TimKiemVaXoaTep)
- [2.8. Tìm kiếm tệp và thay thế văn bản trong các tệp này](#TimKiemVaThayTheVanBan)
- [2.9. Tìm kiếm và đổi tên thư mục](#TimKiemVaDoiTen)
- [2.10. Dọn dẹp dự án nhật thực](#DonDepDuAn)

[3. Lệnh trợ giúp ( man find )](#LenhTroGiup)

[4. Giá trị có thể có của các tùy chọn tìm](#GiaTriCoTheCo)
- [4.1. Tất cả các tùy chọn có đối số là số (n) cho phép số đứng trước dấu cộng (+) hoặc dấu trừ (-)](#TuyChonDoiSo)
- [4.2. Đơn vị thời gian có thể có [smhdw]](#DonViThoiGian)
- [4.3. Các đơn vị kích thước có thể có [ckMGTP]](#CacDonViKichThuoc)
- [4.4. Các loại tệp có thể có ](#CacLoaiTep)



<a name="GhiChu"></a>
### 1. Ghi chú
- Bạn có thể muốn bỏ qua lỗi quyền truy cập và chuyển hướng chúng đến `/dev/null` bằng cách sử dụng toán tử chuyển hướng STDERR: `find path ... 2> /dev/null`
- Để lọc ra các kết quả tìm kiếm, bạn có thể sử dụng các tùy chọn sau: -or, -o, -and, -not
để kết hợp các tùy chọn này và tạo một biểu thức, bạn có thể sử dụng cú pháp sau: `\( expression \)`(chú ý không gian trước và sau khi biểu hiện)
```
$ find . \( -name file1 -or -name folder1 \) -ls
```

```
$ find . \( -name file1 -o -name folder1 \) -ls
```

```
$ find . \( -name file1 -and -name folder1 \) -ls
```

```
$ find . \( -name file1 -not -name folder1 \) -ls
```

- Bạn có thể thực hiện một lệnh trên kết quả tìm kiếm bằng cách sử dụng các tùy chọn sau: `-exec`, `-ok`
Các `-exec` tùy chọn thực thi lệnh trên mỗi tập tin được tìm thấy (hoặc thư mục), mà không yêu cầu xác nhận.
- Các `-ok` tùy chọn yêu cầu xác nhận trước khi thực hiện lệnh trên mỗi tìm thấy file (hoặc thư mục). Bạn có thể xác nhận việc thực hiện lệnh bằng cách gõ y và nhấn Enter, nếu không nhấn Enter để bỏ qua việc thực hiện lệnh. Cú pháp cho cả hai tùy chọn như sau:
```
$ find . -exec command {} \;
```

```
$ find . -ok command {} \;
```

Lưu ý việc sử dụng dấu ngoặc nhọn đóng vai trò giữ chỗ cho tên tệp (hoặc thư mục) được tìm thấy.
Dòng lệnh phải kết thúc bằng dấu chấm phẩy `;` hoặc ký tự dấu cộng `+`.
Ký tự dấu chấm phẩy `;` buộc thực hiện lệnh cho mỗi tệp được tìm thấy.
Ký tự dấu cộng `+` cho phép thực hiện lệnh trên một nhóm tệp được tìm thấy.

Ký tự dấu chấm phẩy `;` nên được thoát bằng ký tự gạch chéo ngược `\` để tránh việc shell diễn giải dấu chấm phẩy như một ký tự đặc biệt (dấu phân tách lệnh shell). Bạn cũng có thể thoát khỏi ký tự dấu chấm phẩy `;` bằng cách đặt nó trong dấu ngoặc kép `";"` hoặc dấu ngoặc kép `;`. Bạn cũng có thể muốn thoát khỏi ký tự dấu cộng (+) bằng ký tự gạch chéo ngược `\`.

```
$ find . -exec echo {} \;
./folder1
./folder2
```

```
$ find . -exec echo {} \+
./folder1 ./folder2
```

<a name="CacViDu"></a>
### 2. Các ví dụ

<a name="TimFile"></a>
##### 2.1. Tìm file
```
$ find . -type f
```

<a name="TimKiemThuMuc"></a>
##### 2.2. Tìm kiếm thư mục
```
$ find . -type d
```

<a name="TimKiemTepThuMuc"></a>
##### 2.3. Tìm kiếm tệp / thư mục với một tên cụ thể
- Tìm kiếm tệp với một tên cụ thể:
```
$ find . -type f -name 'file1'
```

- Tìm kiếm thư mục với một tên cụ thể:
```
$ find . -type d -name 'folder1'
```

- Tìm kiếm các tệp có tên không kết thúc bằng .c:
```
$ find . -type f \! -name "*.c"
```

- Tìm kiếm các tệp / thư mục không phải là cả tệp và tên của chúng kết thúc bằng .c:
```
$ find . \! \( -type f -name "*.c" \)
```

- Tìm kiếm tệp / thư mục là thư mục hoặc tên của chúng kết thúc bằng .c:
```
$ find . \( -type d -or -name "*.c" \)
```

<a name="TimKiemTepChuaMotMauCuThe"></a>
##### 2.4. Tìm kiếm tệp / thư mục trong đó tên của tệp / thư mục chứa một mẫu cụ thể.
- Tìm kiếm các tệp trong đó tên của tệp chứa một mẫu cụ thể:
```
$ find . -type f -name '*file*'

$ find . -type f | grep "file"
```

- Tìm kiếm thư mục trong đó tên của thư mục chứa một mẫu cụ thể:
```
$ find . -type d -name '*folder*'

$ find . -type d | grep "folder"
```

<a name="TimKiemTepCoChuaMotTuCuThe"></a>
##### 2.5. Tìm kiếm các tệp có chứa một từ cụ thể.

- Tìm kiếm các tệp trong đó tên của tệp chứa một mẫu cụ thể:
```
$ find . -type f | xargs grep -l "bar"
```

- Tìm kiếm thư mục trong đó tên của thư mục chứa một mẫu cụ thể:
```
$ find . -type d -name '*folder*'

$ find . -type d | grep "folder"
```

<a name="TimKiemVaSuDungLenhCuThe"></a>
##### 2.6. Tìm kiếm tệp và sử dụng lệnh `-exec` để thực hiện các lệnh cụ thể.
- Tìm kiếm các tệp trong đó tên của tệp chứa một mẫu cụ thể:
```
$ find . -type f -exec ls -al {} \; | grep foo
```

- Tìm kiếm tệp bên trong tệp jar:
```
$ find . -type f -name "*.jar" -exec jar -tf {} \; | grep "MANIFEST.MF"
```

- Tìm kiếm tệp bên trong tệp jar:
```
$ for i in `find . -type f -name "*.jar"`; do echo $i; jar -tf $i | grep "MANIFEST.MF"; done
```

<a name="TimKiemVaXoaTep"></a>
##### 2.7. Tìm kiếm và xóa các tệp / thư mục.
```
$ find . -type f -delete

$ find . -type f -exec rm -f {} \;

$ find . -type d -exec rm -rf {} \;

$ find . -type f -print0 | xargs -0 rm
```

<a name="TimKiemVaThayTheVanBan"></a>
##### 2.8. Tìm kiếm tệp và thay thế văn bản trong các tệp này.
```
$ find . -type f -exec sed -i 's/bar/foo/g' {} \;

$ find . -type f -exec sed -i 's/\#\!\/bin\/sh/\#\!\/bin\/bash/g' {} \;
```

<a name="TimKiemVaDoiTen"></a>
##### 2.9. Tìm kiếm và đổi tên thư mục.
```
for i in `find . -type d -name "foo"`; do folderName=$(dirname "$i"); mv $folderName/foo $folderName/bar; done
```

<a name="DonDepDuAn"></a>
##### 2.10. Dọn dẹp dự án nhật thực.
```
$ find . -type d -name "target" -exec rm -rf {} \;

$ find . -type d -name ".settings" -exec rm -rf {} \;

$ find . -type f -name ".classpath" -exec rm {} \;
$ find . -type f -name ".project" -exec rm {} \;
#$ find . -type f \( -name ".classpath" -o -name ".project" \) -exec rm -rf {} \;

$ find . -type f -name "*~" -exec rm {} \;
$ find . -type f -name ".directory" -exec rm {} \;
#$ find . -type f \( -name "*~" -o -name ".directory" \) -exec rm -rf {} \;

$ find . -type d -name ".svn" -exec rm -rf {} \;
```

<a name="LenhTroGiup"></a>
### 3. Lệnh trợ giúp ( man find )
Các tùy chọn sau có thể được sử dụng:
- Để tìm kiếm tệp theo loại / tên / đường dẫn, hãy sử dụng các tùy chọn sau:
```
-type t
| Đúng nếu tệp thuộc loại t được chỉ định.

-name pattern
| Đúng nếu thành phần cuối cùng của tên đường dẫn đang được kiểm tra khớp với mẫu.
| Các ký tự khớp với mẫu khung đặc biệt ("[", "]", "*" và "?") Có thể được sử dụng như một phần của mẫu.
| Các ký tự này có thể được đối sánh rõ ràng bằng cách thoát chúng bằng dấu gạch chéo ngược ("\").

-iname pattern
| Giống như -name, nhưng đối sánh không phân biệt chữ hoa chữ thường.

-path pattern
| Đúng nếu tên đường dẫn đang được kiểm tra khớp với mẫu.
| Các ký tự khớp với mẫu khung đặc biệt ("[", "]", "*" và "?") Có thể được sử dụng như một phần của mẫu.
| Các ký tự này có thể được đối sánh rõ ràng bằng cách thoát chúng bằng dấu gạch chéo ngược ("\").
| Dấu gạch chéo ("/") được coi như các ký tự bình thường và không cần phải khớp một cách rõ ràng.

-ipath pattern
| Giống như -path, nhưng đối sánh không phân biệt chữ hoa chữ thường.

-regex pattern
| Đúng nếu toàn bộ đường dẫn của tệp khớp với mẫu sử dụng biểu thức chính quy.
| Để đối sánh tệp có tên "./foo/xyzzy", bạn có thể sử dụng biểu thức chính quy ". * / [Xyz] *" hoặc ". * / Foo /.*", nhưng không phải "xyzzy" hoặc "/ foo / ".

-iregex pattern
| Giống như -regex, nhưng đối sánh không phân biệt chữ hoa chữ thường.

-empty
| Đúng nếu tệp hoặc thư mục hiện tại trống.

-depth n
| Đúng nếu độ sâu của tệp so với điểm bắt đầu của đường truyền là n.
| 1 có nghĩa là thư mục bắt đầu.
```

- Để tìm kiếm tệp theo thời gian, hãy sử dụng các tùy chọn sau:
```
-mmin n
| Đúng nếu tệp được sửa đổi lần cuối cách đây đúng n phút (sử dụng +/- trong nhiều hơn / ít hơn n phút).

-mtime [+ -] n [smhdw]
| Đúng nếu tệp được sửa đổi lần cuối cùng cách đây đúng n đơn vị (sử dụng +/- cho nhiều hơn / ít hơn n đơn vị).
| Bất kỳ số lượng đơn vị nào cũng có thể được kết hợp trong đối số một -mtime, -time, -atime hoặc -ctime, ví dụ: '-1h30 phút'.

-Bmin [+ -] n
| Đúng nếu tệp được tạo cách đây đúng n phút (sử dụng +/- trong hơn / dưới n phút).

-Btime [+-]n[smhdw]
| Đúng nếu tệp được tạo cách đây đúng n đơn vị (sử dụng +/- cho nhiều hơn / ít hơn n đơn vị).

-amin [+ -] n
| Đúng nếu tệp được truy cập lần cuối cách đây đúng n phút (sử dụng +/- trong hơn / dưới n phút).

-atime [+ -] n [smhdw]
| Đúng nếu tệp được truy cập lần cuối cách đây đúng n đơn vị (sử dụng +/- cho nhiều hơn / ít hơn n đơn vị).

-cmin [+ -] n
| Đúng nếu tệp được thay đổi lần cuối chính xác n phút trước (sử dụng +/- trong hơn / dưới n phút).

-ctime [+ -] n [smhdw]
| Đúng nếu tệp được thay đổi lần cuối đúng n đơn vị (sử dụng +/- cho nhiều hơn / ít hơn n đơn vị).
```

- Để tìm kiếm tệp theo kích thước, hãy sử dụng các tùy chọn sau:
```
-size [+-]n[ckMGTP]
| Đúng nếu kích thước của tệp chính xác là n đơn vị (sử dụng +/- cho nhiều hơn / ít hơn n đơn vị).
| Nếu không có đơn vị nào được chỉ định, kích thước của tệp, sẽ được làm tròn lên, theo khối 512 byte.
```

- Để tìm kiếm tệp theo người dùng / nhóm, hãy sử dụng các tùy chọn sau:
```
| Đúng nếu tệp thuộc về uname của người dùng.
| Nếu uname là số và không có tên người dùng như vậy, thì uname được coi như một ID người dùng.
| Nếu người dùng không tồn tại, bạn sẽ gặp lỗi này: "find: -user: uname: không có người dùng như vậy".

-group gname
| Đúng nếu tệp thuộc tên nhóm.
| Nếu gname là số và không có tên nhóm như vậy, thì gname được coi như một ID nhóm.
| Nếu nhóm không tồn tại, bạn sẽ gặp lỗi này: "find: -group: gname: no such group".

-nouser
| Đúng nếu tệp thuộc về người dùng không xác định.

-nogroup
| Đúng nếu tệp thuộc một nhóm không xác định.
```

- Các tùy chọn sau có thể được sử dụng để thực hiện các hành động cụ thể:
```
-l
| Luôn trả về true.
| Thông tin sau cho tệp hiện tại được ghi vào đầu ra tiêu chuẩn:
| số inode của nó, kích thước trong khối 512 byte, quyền truy cập tệp, số liên kết cứng, chủ sở hữu, nhóm, kích thước tính bằng byte, thời gian sửa đổi lần cuối và tên đường dẫn.
| Nếu tệp là một khối hoặc tệp ký tự đặc biệt, số thiết bị sẽ được hiển thị thay vì kích thước tính bằng byte.
| Nếu tệp là một liên kết tượng trưng, ​​tên đường dẫn của tệp được liên kết đến sẽ được hiển thị trước "->".
| Định dạng giống với định dạng được tạo bởi "ls -dgils".

-in
| Luôn trả về true.
| Nó in tên đường dẫn của tệp hiện tại ra đầu ra tiêu chuẩn.

-print0
| Luôn trả về true.
| Nó in tên đường dẫn của tệp hiện tại ra đầu ra tiêu chuẩn, theo sau là ký tự ASCII NUL (mã ký tự 0).

-delete
| Xóa các tệp và / hoặc thư mục được tìm thấy.
| Luôn trả về true.
| Điều này thực thi từ thư mục làm việc hiện tại khi tìm thấy đệ quy xuống cây.
| Nó sẽ không cố xóa tên tệp có ký tự "/" trong tên đường dẫn liên quan đến "." vì lý do bảo mật.
| Nếu bạn chỉ tìm kiếm các thư mục, hành động xóa sẽ không xóa một thư mục nếu thư mục đó không trống.

-exec tiện ích [đối số ...];
| Đúng nếu chương trình có tên tiện ích trả về giá trị 0 làm trạng thái thoát của nó.
| Các đối số tùy chọn có thể được chuyển cho tiện ích.
| Biểu thức phải được kết thúc bằng dấu chấm phẩy (";").
| Nếu bạn gọi find từ một shell, bạn có thể cần phải trích dẫn dấu chấm phẩy nếu shell sẽ coi nó như một toán tử điều khiển.
| Nếu chuỗi "{}" xuất hiện ở bất kỳ đâu trong tên tiện ích hoặc các đối số, nó được thay thế bằng tên đường dẫn của tệp hiện tại.
| Tiện ích sẽ được thực thi từ thư mục mà từ đó tìm thấy đã được thực thi.
| Tiện ích và đối số không phụ thuộc vào việc mở rộng thêm các mẫu và cấu trúc shell.

-exec tiện ích [đối số ...] {} +
| Tương tự như -exec, ngoại trừ việc "{}" được thay thế bằng nhiều tên đường dẫn nhất có thể cho mỗi lệnh gọi tiện ích.
| Hành vi này tương tự như hành vi của xargs.

-ok tiện ích [đối số ...];
| Tương tự như -exec, ngoại trừ việc tìm thấy yêu cầu xác nhận của người dùng đối với việc thực thi tiện ích bằng cách in thông báo tới thiết bị đầu cuối và đọc phản hồi.
| Nếu phản hồi không phải là khẳng định ('y'), lệnh không được thực thi và giá trị của biểu thức -ok là sai.
```

- Các toán tử sau (được liệt kê theo thứ tự ưu tiên giảm dần) có thể được kết hợp với các tùy chọn:
```
| Giá trị này là true nếu biểu thức trong ngoặc cho kết quả là true.

! biểu hiện
-không phải biểu thức
| Đây là toán tử NOT một bậc.
| Nó đánh giá là true nếu biểu thức là false.

-false
| Luôn luôn sai.

-true
| Luôn luôn đúng.

expression -and expression
biểu cảm
| Toán tử -and là toán tử logic AND.
| Vì nó được ngụ ý bởi sự đặt cạnh nhau của hai biểu thức, nó không cần phải được chỉ định.
| Biểu thức cho giá trị true nếu cả hai biểu thức đều đúng.
| Biểu thức thứ hai không được ước lượng nếu biểu thức đầu tiên là sai.

expression -or expression
| Toán tử -or là toán tử OR logic.
| Biểu thức cho giá trị true nếu biểu thức thứ nhất hoặc thứ hai là true.
| Biểu thức thứ hai không được ước lượng nếu biểu thức đầu tiên là đúng.
```

<a name="GiaTriCoTheCo"></a>
### 4. Giá trị có thể có của các tùy chọn tìm.

<a name="TuyChonDoiSo"></a>
##### 4.1. Tất cả các tùy chọn có đối số là số (n) cho phép số đứng trước dấu cộng (+) hoặc dấu trừ (-):
```
+ {n}: dấu cộng (+) có nghĩa là 'nhiều hơn n' (+3: nhiều hơn 3)
- {n}: dấu trừ (-) có nghĩa là `nhỏ hơn n '(-3: nhỏ hơn 3)
{n}: có nghĩa là 'chính xác n' (3: chính xác 3)
```

<a name="DonViThoiGian"></a>
##### 4.2. Đơn vị thời gian có thể có [smhdw] như sau:
```
m: phút (60 giây)
h: giờ (60 phút)
d: ngày (24 giờ) (mặc định)
w: tuần (7 ngày)
```

<a name="CacDonViKichThuoc"></a>
##### 4.3. Các đơn vị kích thước có thể có [ckMGTP] như sau:
```
k: kilobytes (1024 bytes)
M: megabytes (1024 kilobytes)
G: gigabytes (1024 megabytes)
T: terabytes (1024 gigabytes)
P: petabytes (1024 terabytes)
```

<a name="CacLoaiTep"></a>
##### 4.4. Các loại tệp có thể có như sau:
```
d: thư mục
l: liên kết tượng trưng
c: ký tự đặc biệt
b: khối đặc biệt
p: FIFO
s: ổ cắm
```
