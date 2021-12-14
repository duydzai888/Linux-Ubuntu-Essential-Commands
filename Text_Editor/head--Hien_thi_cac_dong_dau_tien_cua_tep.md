# head - Hiển thị các dòng đầu tiên của tệp
## Menu
[1. Ghi chú](#GhiChu)

[2. Các ví dụ](#CacViDu)

[3. Lệnh trợ giúp ( man head )](#LenhTroGiup)



  
<a name="GhiChu"></a>
### 1. Ghi chú
In 10 dòng đầu tiên của mỗi tệp ở đầu ra tiêu chuẩn.

Với nhiều tệp, hãy đặt trước mỗi tệp một tiêu đề cho tên tệp.

Khi không có tệp hoặc khi có tệp - , hãy đọc đầu vào chuẩn.

<a name="CacViDu"></a>
### 2. Các ví dụ
```
$ head -f file1
```

```
$ head -n 20 file1
```

<a name="LenhTroGiup"></a>
### 3. Lệnh trợ giúp ( man head )
Các tùy chọn sau có thể được sử dụng:
```
-c, --bytes=[-]NUM       in NUM byte đầu tiên của mỗi tệp; với '-' ở đầu, in tất cả trừ NUM                           byte cuối cùng của mỗi tệp
-n, --lines=[-]NUM       in NUM dòng đầu tiên thay vì 10 dòng đầu tiên; với '-' ở đầu, in tất                          cả trừ NUM dòng cuối cùng của mỗi tệp
-q, --quiet, --silent    không bao giờ in tiêu đề cho tên tệp
-v, --verbose            luôn in tiêu đề cho tên tệp
-z, --zero-terminated    dấu phân cách dòng là NUL, không phải dòng mới
    --help               hiển thị trợ giúp này và thoát
    --version            xuất thông tin phiên bản và thoát.
```
NUM có thể có hậu tố cấp số nhân:
b 512

kB 1000

K 1024

MB 1000 * 1000

M 1024 * 1024

GB 1000 * 1000 * 1000

G 1024 * 1024 * 1024

, v.v. đối với T, P, E, Z, Y.