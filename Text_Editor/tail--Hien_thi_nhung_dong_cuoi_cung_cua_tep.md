# tail - Hiển thị những dòng cuối cùng của tệp
## Menu
[1. Ghi chú](#GhiChu)

[2. Các ví dụ](#CacViDu)

[3. Lệnh trợ giúp](#LenhTroGiup)



<a name="GhiChu"></a>
### 1. Ghi chú
- Sử dụng
```
tail file ...
```
In 10 dòng cuối cùng của mỗi tệp ở đầu ra tiêu chuẩn.

Với nhiều tệp, hãy đặt trước mỗi tệp một tiêu đề cho tên tệp.

Khi không có tệp hoặc khi có tệp - , hãy đọc đầu vào chuẩn.

<a name="CacViDu"></a>
### 2. Các ví dụ
```
$ tail-f file1
```

```
$ tail -n 30 file1
```

<a name="LenhTroGiup"></a>
### 3. Lệnh trợ giúp ( man tail )
- Các tùy chọn sau có thể được sử dụng:
```
-c, --bytes=[+]NUM                xuất NUM byte cuối cùng; hoặc sử dụng -c + NUM để xuất bắt đầu bằng NUM byte của mỗi tệp
-f, --follow[={name|descriptor}]  xuất dữ liệu nối khi tệp phát triển; một đối số tùy chọn vắng mặt có nghĩa là 'bộ mô tả'
-F                                giống như --follow = name --retry
-n, --lines=[+]NUM                xuất NUM dòng cuối cùng, thay vì 10 dòng cuối cùng; hoặc sử dụng -n + NUM để xuất ra bắt đầu bằng dòng NUM
    --max-unchanged-stats=N       với --follow = name, mở lại FILE không thay đổi kích thước sau N (mặc định 5) lần lặp để xem nó đã được hủy liên kết hoặc đổi tên hay chưa
                                  (đây là trường hợp thông thường của các tệp nhật ký được xoay);
                                  với inotify, tùy chọn này hiếm khi hữu ích
    --pid=PID                     với -f, chấm dứt sau ID quy trình, PID chết
-q, --quiet, --silent             never output headers giving file names
    --retry                       tiếp tục cố gắng mở một tệp nếu nó không thể truy cập được
-s, --sleep-interval=N            với -f, ngủ khoảng N giây (mặc định là 1,0) giữa các lần lặp;
                                  với inotify và --pid = P, kiểm tra quá trình P ít nhất một lần sau N giây
-v, --verbose                     luôn xuất tiêu đề cho tên tệp
-z, --zero-terminated             dấu phân cách dòng là NUL, không phải dòng mới
    --help                        hiển thị trợ giúp này và thoát
    --version                     xuất thông tin phiên bản và thoát
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

Với **-follow ( -f )**, **tail** mặc định theo sau bộ mô tả tệp, có nghĩa là ngay cả khi một tệp riêng được đổi tên, **tail** sẽ tiếp tục theo dõi phần cuối của nó.

Hành vi mặc định này không được mong muốn khi bạn thực sự muốn theo dõi tên thực của tệp, không phải bộ mô tả tệp (ví dụ: xoay bản ghi).

Sử dụng **--follow=name** trong trường hợp đó.

Điều đó gây ra **tail** để theo dõi tệp được đặt tên theo cách phù hợp với việc đổi tên, xóa và tạo.
