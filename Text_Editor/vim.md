# vim
## Menu
[1. Ghi chú](#GhiChu)

[2. Lệnh vi: INSERT](#INSERT)

[3. Lệnh vi: REPLACE](#REPLACE)

[4. Lệnh vi: DELETE](#DELETE)

[5. Lệnh vi: COPY/PASTE](#COPY_PASTE)

[6. Lệnh vi: UNDO](#UNDO)

[7. Lệnh vi: SEARCH](#SEARCH)

[8. Lệnh vi: CURSOR](#CURSOR)

[9. Lệnh vi: SCREEN](#SCREEN)

[10. Lệnh vi: LINES](#LINES)

[11. Lệnh vi: READ/SAVE](#READ_SAVE)

[12. Lệnh vi: EXIT](#EXIT)



<a name="GhiChu"></a>
### 1. Ghi chú
`Vim` (Vi IMproved) là một trình soạn thảo văn bản có thể được sử dụng để chỉnh sửa tất cả các loại văn bản thuần túy.

Trước khi bạn bắt đầu chỉnh sửa văn bản, màn hình ở trạng thái chế độ bảng điều khiển. Khi bạn bắt đầu chèn văn bản, màn hình đang ở trạng thái chế độ chèn (bạn sẽ thấy `--INSERT--` ở cuối màn hình). Khi bạn hoàn tất việc chỉnh sửa văn bản, bạn có thể nhấn `Esc` phím để trở về trạng thái chế độ bảng điều khiển.

<a name="INSERT"></a>
### 2. Lệnh vi: INSERT
```
i
| chèn văn bản, trước con trỏ, cho đến khi người dùng nhấn <esc>

a
| chèn văn bản, sau con trỏ, cho đến khi người dùng nhấn <esc>

I
| chèn văn bản, ở đầu dòng hiện tại, cho đến khi người dùng nhấn <esc>

A
| chèn văn bản vào cuối dòng hiện tại cho đến khi người dùng nhấn <esc>

o
| chèn một dòng mới bên dưới dòng hiện tại, chèn văn bản, cho đến khi người dùng nhấn <esc>

O
| chèn một dòng mới phía trên dòng hiện tại, chèn văn bản, cho đến khi người dùng nhấn <esc>
```

<a name="REPLACE"></a>
### 3. Lệnh vi: REPLACE
```
r
| thay thế ký tự dưới con trỏ bằng một ký tự khác

R
| thay thế nhiều ký tự, bắt đầu bằng ký tự dưới con trỏ, cho đến khi người dùng nhấn <esc>

cw
| thay thế từ, bắt đầu bằng ký tự dưới con trỏ, cho đến khi người dùng nhấn <esc>

c{n}w
| thay thế {n} từ, bắt đầu bằng ký tự dưới con trỏ, cho đến khi người dùng nhấn <esc> (c3w: thay thế 3 từ)

C
| thay thế phần còn lại của dòng, bắt đầu bằng ký tự dưới con trỏ, cho đến khi người dùng nhấn <esc>

cc
| thay thế dòng hiện tại, cho đến khi người dùng nhấn <esc>

{n}cc
c{n}c
| thay thế {n} dòng, bắt đầu bằng dòng hiện tại, cho đến khi người dùng nhấn <esc>
```

<a name="DELETE"></a>
### 4. Lệnh vi: DELETE
```
x
| xóa ký tự dưới con trỏ

{n}x
| xóa {n} ký tự, bắt đầu bằng ký tự dưới con trỏ (3x: xóa 3 ký tự)

dw
| xóa từ, bắt đầu bằng ký tự dưới con trỏ

d{n}w
| xóa {n} từ, bắt đầu bằng ký tự dưới con trỏ (d3w: xóa 3 từ)

D
|delete the remainder of the line, starting with the character under cursor

dd
| xóa dòng hiện tại

{n}dd
d{n}d
| xóa {n} dòng, bắt đầu bằng dòng hiện tại (3dd: xóa 3 dòng)
```

<a name="COPY_PASTE"></a>
### 5. Lệnh vi: COPY/PASTE
```
yy
| sao chép dòng hiện tại vào khay nhớ tạm

{n}yy
y{n}y
| sao chép {n} dòng, bao gồm cả dòng hiện tại, vào khay nhớ tạm (3yy: sao chép 3 dòng)

p
| chèn văn bản từ khay nhớ tạm vào sau dòng hiện tại
```

<a name="UNDO"></a>
### 6. Lệnh vi: UNDO
```
u
| hoàn tác sửa đổi cuối cùng
```

<a name="SEARCH"></a>
### 7. Lệnh vi: SEARCH
```
/{pattern}
| Tìm kiếm chuyển tiếp trong tệp để biết sự xuất hiện của chuỗi (/ foo: tìm kiếm chuỗi "foo")

?{pattern}
| Tìm kiếm ngược trong tệp để biết sự xuất hiện của chuỗi

n
| Tìm kiếm về phía trước trong tệp để biết lần xuất hiện tiếp theo của chuỗi

N
| Tìm kiếm ngược trong tệp để tìm lần xuất hiện trước đó của chuỗi
```

<a name="CURSOR"></a>
### 8. Lệnh vi: CURSOR
```
j
<return>
<down arrow>
| di chuyển con trỏ xuống một dòng

k
<up arrow>
| di chuyển con trỏ lên một dòng

h
<delete>
<left arrow>
| di chuyển con trỏ sang trái một ký tự

l
<space>
<right arrow>
| di chuyển con trỏ sang phải một ký tự

0
| di chuyển con trỏ đến đầu dòng hiện tại

$
| di chuyển con trỏ đến cuối dòng hiện tại

w
| di chuyển con trỏ tới đầu từ tiếp theo

b
| di chuyển con trỏ về đầu từ trước đó

:0 <return>
1G
| di chuyển con trỏ đến dòng đầu tiên

:n <return>
{n}G
| di chuyển con trỏ đến dòng {n}

:$ <return>
G
| di chuyển con trỏ đến dòng đầu tiên
```

<a name="SCREEN"></a>
### 9. Lệnh vi: SCREEN
```
<control>f
| di chuyển xuống một màn hình

<control>b
| di chuyển lên một màn hình

<control>d
| di chuyển xuống một nửa màn hình

<control>u
| di chuyển lên một nửa màn hình

<control>l
| vẽ lại màn hình

<control>r
| vẽ lại màn hình, xóa các dòng đã xóa
```

<a name="LINES"></a>
### 10. Lệnh vi: LINES
```
:.= <return>
| hiển thị số dòng hiện tại ở cuối màn hình

:= <return>
| hiển thị tổng số dòng ở cuối màn hình

<control>g
| hiển thị thông tin chi tiết (số dòng hiện tại, tổng số dòng, ...) ở cuối màn hình
| ví dụ: "file1" [Đã sửa đổi] dòng 4 trên 11 --36% - cột 5
```

<a name="READ_SAVE"></a>
### 11. Lệnh vi: READ/SAVE
```
:r <return>
| đọc tệp hiện tại và chèn nội dung của nó sau dòng hiện tại

:r {filename} <return>
| đọc tệp hiện tại và chèn nội dung của nó sau dòng hiện tại

:w <return>
| lưu tệp hiện tại

:w {filename} <return>
| lưu nội dung vào tệp "tên tệp"
| Nó sẽ khiếu nại nếu tệp "tên tệp" đã tồn tại: "Tệp tồn tại (thêm! Để ghi đè)"

:w! {filename} <return>
| buộc lưu nội dung vào tệp "tên tệp", ngay cả khi tệp đã tồn tại

:{n},{m}w {filename} <return>
| lưu vào tệp "tên tệp" nội dung của các dòng được đánh số từ {n} đến {m}
| Nó sẽ khiếu nại nếu tệp "tên tệp" đã tồn tại: "Tệp tồn tại (thêm! Để ghi đè)"

:{n},{m}w! <return>
| lưu vào tệp hiện tại nội dung của các dòng được đánh số từ {n} đến {m}

:{n},{m}w! {filename} <return>
| lưu vào tệp "tên tệp" nội dung của các dòng được đánh số từ {n} đến {m}
```

<a name="EXIT"></a>
### 12. Lệnh vi: EXIT
```
:x <return>
:wq <return>
| thoát vim + lưu tệp đã sửa đổi

:q <return>
| exit vim (sẽ khiếu nại nếu tệp đã bị thay đổi: "Không ghi kể từ lần thay đổi cuối cùng (thêm! để ghi đè)")

:q! <return>
| thoát vim + loại bỏ tất cả các sửa đổi
```