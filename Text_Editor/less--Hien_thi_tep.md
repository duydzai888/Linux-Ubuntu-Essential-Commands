# less - Hiển thị tệp
## Menu
[1. Ghi chú](#GhiChu)

[2. VÍ dụ](#ViDu)

[3. Lệnh trợ giúp ( man less)](#LenhTroGiup)




<a name="GhiChu"></a>
### 1. Ghi chú
Các `less` lệnh có một danh sách tên tập tin cho các đối số của nó và hiển thị nội dung của nó màn hình bởi màn hình.

► Nhấn `q` để thoát.

► Bấm `e` để cuộn về phía trước một dòng.

► Bấm `y` để cuộn lùi một dòng.

► Nhấn `f` để cuộn về phía trước một cửa sổ (hoặc nhấn phím cách).

► Bấm `b` để cuộn lùi một cửa sổ.

► Bấm `d` để cuộn về phía trước một nửa cửa sổ.

► Bấm `u` để cuộn lùi một nửa cửa sổ.

► Nhấn `g` để chuyển đến dòng đầu tiên trong tệp hiện tại.

► Nhấn `G` để chuyển đến dòng cuối cùng trong tệp hiện tại.

► Nhấn `:n` để chuyển sang tệp tiếp theo ().

► Nhấn `:q` để chuyển đến tệp trước đó.

► Nhấn `Ctrl+g`(hoặc `Ctrl+G`) để hiển thị tên tệp hiện tại, số dòng bắt đầu/kết thúc được hiển thị, số byte đã đọc và phần trăm dữ liệu được hiển thị. Ví dụ: file1 dòng 52-102/118 byte 6992/8145 85% (nhấn RETURN)

<a name="ViDu"></a>
### 2. Ví dụ
```
$ less file1 file2 file3
```

<a name="LenhTroGiup"></a>
### 3. Lệnh trợ giúp ( man less )
- Các lệnh sau có thể được sử dụng để cuộn tiến/lùi:
```
enter
<control> n
| Cuộn tới {n} dòng, mặc định 1 dòng.
| Toàn bộ {n} dòng được hiển thị, ngay cả khi {n} lớn hơn kích thước màn hình.

y
k
| Cuộn lùi {n} dòng, mặc định 1 dòng.
| Toàn bộ {n} dòng được hiển thị, ngay cả khi {n} lớn hơn kích thước màn hình.

#-- ------------------------------------

d
<control> d
| Cuộn về phía trước {n} dòng, mặc định là một nửa kích thước màn hình.
| Nếu {n} được chỉ định, nó sẽ trở thành giá trị mặc định mới cho các lệnh "d" và "u" tiếp theo.

u
<control> u
| Cuộn lùi {n} dòng, mặc định là một nửa kích thước màn hình.
| Nếu {n} được chỉ định, nó sẽ trở thành giá trị mặc định mới cho các lệnh "d" và "u" tiếp theo.

#-- ------------------------------------

f
<spacebar>
| Cuộn tới {n} dòng, mặc định là một cửa sổ.
| Nếu {n} lớn hơn kích thước màn hình, chỉ màn hình cuối cùng được hiển thị.

b
<control> b
| Cuộn lùi {n} dòng, mặc định là một cửa sổ.
| Nếu {n} lớn hơn kích thước màn hình, chỉ màn hình cuối cùng được hiển thị.

#-- ------------------------------------

g
<
| Chuyển đến dòng {n} trong tệp, đặt mặc định là đầu tệp.

G
>
| Chuyển đến dòng {n} trong tệp, mặc định là cuối tệp.

#-- ------------------------------------

m
| Theo sau là bất kỳ ký tự viết thường nào, đánh dấu vị trí hiện tại bằng ký tự đó.

'
| (Trích dẫn duy nhất)
| Theo sau là bất kỳ chữ cái thường nào, trở về vị trí đã được đánh dấu trước đó bằng chữ cái đó.
| Theo sau là ký tự "^" nhảy về đầu tệp.
| Theo sau là ký tự "$" nhảy đến cuối tệp.

#-- ------------------------------------

:n
| Chuyển đến tệp tiếp theo (từ danh sách các tệp được đưa ra trong dòng lệnh).
| Nếu một số {n} được chỉ định, tệp tiếp theo thứ {n} sẽ được kiểm tra.

:p
| Chuyển đến tệp trước đó trong danh sách dòng lệnh.
| Nếu một số {n} được chỉ định, thì tệp trước đó thứ {n} sẽ được kiểm tra.

:x
| Chuyển đến tệp đầu tiên trong danh sách dòng lệnh.
| Nếu một số {n} được chỉ định, tệp thứ {n} trong danh sách sẽ được kiểm tra.

:d
| Xóa tệp hiện tại khỏi danh sách tệp.

q
Q
:q
:Q
ZZ
| Thoát less.
```

- Các lệnh sau có thể được sử dụng để tìm kiếm tiến/lùi:
```
/pattern
| Tìm kiếm dòng thứ {n} chứa mẫu trong tệp.
| {n} mặc định là 1.

?pattern
| Tìm kiếm ngược trong tệp để tìm dòng thứ {n} chứa mẫu.
| Tìm kiếm bắt đầu ở dòng ngay trước khi dòng trên cùng được hiển thị.

&pattern
| Chỉ hiển thị các dòng phù hợp với mẫu; các dòng không khớp với mẫu sẽ không được hiển thị.
| Nếu bạn nhập "&" theo sau là <enter>, bất kỳ bộ lọc nào sẽ bị tắt và tất cả các dòng sẽ được hiển thị.
| Trong khi có hiệu lực lọc, dấu "&" được hiển thị ở đầu lời nhắc, như một lời nhắc nhở rằng một số dòng trong tệp có thể bị ẩn.

n
| Lặp lại tìm kiếm trước đó, cho dòng thứ {n} chứa mẫu cuối cùng.
| Nếu tìm kiếm trước đó được sửa đổi bởi "<control> N", thì tìm kiếm được thực hiện cho dòng thứ {n} KHÔNG chứa mẫu.
| Nếu tìm kiếm trước đó được sửa đổi bởi "<control> E", tìm kiếm sẽ tiếp tục trong tệp tiếp theo (hoặc trước đó) nếu không được thỏa mãn trong tệp hiện tại.

N
Lặp lại tìm kiếm trước đó, nhưng theo hướng ngược lại.
```

Mẫu là một biểu thức chính quy, được nhận dạng bởi thư viện biểu thức chính quy do hệ thống của bạn cung cấp.
Tìm kiếm bắt đầu từ dòng đầu tiên được hiển thị.

Một số ký tự đặc biệt nếu được nhập ở đầu mẫu; chúng sửa đổi loại tìm kiếm thay vì trở thành một phần của mẫu (xem bên dưới).

- Các lệnh sau có thể được sử dụng để tìm kiếm tiến/lùi:
```
<control> N
!
| Tìm kiếm các dòng KHÔNG phù hợp với mẫu.

<control> E
*
| Tìm kiếm nhiều tệp.
| Nghĩa là, nếu tìm kiếm đến END / đầu của tệp hiện tại mà không tìm thấy kết quả phù hợp,
| tiếp tục tìm kiếm trong tệp tiếp theo / trước đó trong danh sách dòng lệnh.

<control> F
@
| Bắt đầu tìm kiếm ở dòng đầu tiên / cuối cùng của tệp đầu tiên / cuối cùng trong danh sách dòng lệnh,
| bất kể những gì hiện đang hiển thị trên màn hình hoặc cài đặt của các tùy chọn -a hoặc -j.

<control> K
| Đánh dấu bất kỳ văn bản nào khớp với mẫu trên màn hình hiện tại, nhưng không di chuyển đến kết quả phù hợp đầu tiên (GIỮ vị trí hiện tại).
```