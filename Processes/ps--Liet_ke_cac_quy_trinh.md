# ps - Liệt kê các quy trình
## Menu
[1. Ghi chú](#GhiChu)

[2. Các ví dụ](#CacViDu)

[3. Lệnh trợ giúp ( man ps )](#LenhTroGiup)



<a name="GhiChu"></a>
### 1. Ghi chú
Đối với các quy trình đã được chọn để hiển thị, thông tin mặc định để hiển thị bao gồm: ID quy trình (PID), thiết bị đầu cuối điều khiển (TTY), thời gian CPU mà quy trình đã sử dụng và lệnh liên quan.

Lệnh `ps` hỗ trợ 3 tùy chọn khác nhau:
- Tùy chọn kiểu `Unix` : chúng được đặt trước bởi một ký tự gạch ngang ( -f , ...).
- Tùy chọn kiểu `BSD` : chúng không đứng trước ký tự gạch ngang ( x , ...).
- Các tùy chọn dài `GNU` : chúng được đặt trước bởi các ký tự gạch ngang kép ( --forest , ...).

Đây là danh sách một số tiêu đề được hiển thị bằng lệnh `ps`:
- `UID` : người dùng đã bắt đầu quá trình.
- `PID` : ID quy trình.
- `PPID` : ID tiến trình của tiến trình gốc.
- `C` : việc sử dụng bộ xử lý.
- `STIME` : thời gian hệ thống bắt đầu quá trình.
- `TTY` : thiết bị đầu cuối bắt đầu quá trình.
- `TIME` : tổng thời gian cần thiết để chạy quy trình.
- `CMD` : lệnh bắt đầu quá trình.

 Các     tiêu đề có thể được hiển thị bổ sung bởi tùy chọn `-l`:
- `F` : cờ hệ thống được hạt nhân gán cho tiến trình.
- `S` : trạng thái của tiến trình (O: đang chạy, S: đang ngủ, R: có thể chạy được, Z: zombie, T: đã dừng lại).
- `PRI` : mức độ ưu tiên của quá trình (số thấp hơn có nghĩa là mức độ ưu tiên cao hơn).
- `NI` : giá trị tốt đẹp.
- `ADDR` : địa chỉ bộ nhớ của tiến trình.
- `SZ` : không gian hoán đổi theo yêu cầu của quy trình.
- `WCHAN` : địa chỉ của hạt nhân nơi tiến trình đang ngủ.

Các BSD-style tùy chọn `l` hiển thị một tiêu đề đặc biệt `STAT` hiển thị trạng thái của quá trình sử dụng hai nhân vật:
- Ký tự đầu tiên hiển thị trạng thái của quá trình (`O`: đang chạy, `S`: đang ngủ, `R`: có thể chạy được, `Z`: zombie, `T`: đã dừng lại).
- Ký tự thứ hai hiển thị trạng thái của quá trình:
    - `<`: quá trình đang chạy ở mức ưu tiên cao.
    - `N`: tiến trình đang chạy ở mức ưu tiên thấp.
    - `L`: tiến trình có các trang bị khóa trong bộ nhớ.
    - `s`: tiến trình là một người dẫn đầu phiên.
    - `l`: quy trình đa luồng.
    - `+`: tiến trình đang chạy ở phía trước.
    
    

<a name="CacViDu"></a>
### 2. Các ví dụ
- Liệt kê các quy trình thuộc về người dùng hiện tại và đang chạy trên thiết bị đầu cuối hiện tại:
    - Đầu ra mặc định:
    ```
    $ ps
     PID TTY          TIME CMD
    5355 pts/0    00:00:00 bash
    7719 pts/0    00:00:00 ps
    ```
    
    - Định dạng đầy đủ:
    ```
    $ ps -f
    UID        PID  PPID  C STIME TTY          TIME CMD
    mtitek    5355  5354  0 14:57 pts/0    00:00:00 -bash
    mtitek    7706  5355  0 18:51 pts/0    00:00:00 ps -f
    ```
    
    - Định dạng dài ( tùy chọn kiểu `Unix` ):
    ```
    $ ps -l
    F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
    0 S  1000  5355  5354  0  80   0 -  5732 wait   pts/0    00:00:00 bash
    0 R  1000  7708  5355  0  80   0 -  7230 -      pts/0    00:00:00 ps
    ```
    
    - Định dạng dài ( tùy chọn kiểu `BSD` ):
    ```
    $ ps l
    F   UID   PID  PPID PRI  NI    VSZ   RSS WCHAN  STAT TTY        TIME COMMAND
    0  1000  5355  5354  20   0  22928  5512 wait   Ss   pts/0      0:00 -bash
    0  1000  9642  5355  20   0  28920  1484 -      R+   pts/0      0:00 ps l
    ```
    
- Liệt kê các quy trình thuộc về người dùng hiện tại bao gồm các quy trình không có thiết bị đầu cuối được chỉ định:
```
$ ps x
 PID TTY      STAT   TIME COMMAND
5258 ?        Ss     0:00 /lib/systemd/systemd --user
5259 ?        S      0:00 (sd-pam)
5354 ?        R      0:00 sshd: mtitek@pts/0
5355 pts/0    Ss     0:00 -bash
7980 pts/0    R+     0:00 ps x
```

- Hiển thị hệ thống phân cấp các quy trình (mối quan hệ giữa các quy trình được vẽ bằng các ký tự ASCII):
```
$ ps x --forest
 PID TTY      STAT   TIME COMMAND
5354 ?        S      0:00 sshd: mtitek@pts/0
5355 pts/0    Ss     0:00  \_ -bash
8128 pts/0    R+     0:00      \_ ps x --forest
5258 ?        Ss     0:00 /lib/systemd/systemd --user
5259 ?        S      0:00  \_ (sd-pam)
```

- Liệt kê tất cả các quy trình:
```
$ ps -e
```

```
$ ps -A
```

- Liệt kê các quy trình `PID`:
```
$ ps | grep bash | grep -v grep | awk '{print $1}'
```

```
$ ps | grep bash | grep -v grep | awk {'print $1 " " $2 " " $3 " " $4 " " $5 '}
17190 pts/0 00:00:00 bash
```

```
$ ps | grep bash | grep -v grep | colrm 6
17190
```

```
$ for pid in `ps -e -f | grep mongodb | grep -v grep | awk '{print $2}'`; do echo "PID: $pid"; done
PID: 19034
```

- Hủy các quy trình
```
$ for pid in `ps -e -f | grep mongodb | grep -v grep | awk '{print $2}'`; do kill -9 $pid; done
```

<a name="lenhTroGiup"></a>
### 3. Lệnh trợ giúp ( man ps )
- Các tùy chọn cơ bản:
```
-A, -e               tất cả các quy trình
-a                   tất cả đều có tty, ngoại trừ các nhà lãnh đạo phiên
 a                   tất cả với tty, bao gồm cả những người dùng khác
-d                   tất cả ngoại trừ các nhà lãnh đạo phiên họp
-N, --deselect       phủ định lựa chọn
 r                   chỉ các quy trình đang chạy
 T                   tất cả các quy trình trên thiết bị đầu cuối này
 x                   quy trình mà không cần kiểm soát ttys
```

- Lựa chọn theo danh sách:
```
-C <command>         tên lệnh
-G, --Group <GID>    id hoặc tên nhóm thực
-g, --group <group>  phiên hoặc tên nhóm hiệu quả
-p, p, --pid <PID>   xử lý ID
       --ppid <PID>  id quy trình mẹ
-q, q, --quick-pid <PID> process id (quick mode)
-s, --sid <session>  phiên id
-t, t, --tty <tty>   phần cuối
-u, U, --user <UID>  id hoặc tên người dùng hiệu quả
-U, --User <UID>     id hoặc tên người dùng thực
```

- Các tùy chọn lựa chọn có thể coi là đối số của chúng:
    - Danh sách được phân tách bằng dấu phẩy, ví dụ: `-u root, none`
    - Hoặc danh sách được phân tách bằng trống, ví dụ: `-p 123 4567` 

- Các định dạng đầu ra:
```
-F                   thêm đầy
-f                   định dạng đầy đủ, bao gồm các dòng lệnh
 f, --forest         cây quy trình nghệ thuật ascii
-H                   hiển thị phân cấp quy trình
-j                   định dạng công việc
 j                   Định dạng điều khiển công việc BSD
-l                   định dạng dài
 l                   BSD định dạng dài
-M, Z                thêm dữ liệu bảo mật (cho SELinux)
-O <format>          tải trước với các cột mặc định
 O <format>          như -O, với tính cách BSD
-o, o, --format <format> định dạng do người dùng xác định
 s                   định dạng tín hiệu
 u                   định dạng hướng người dùng
 v                   định dạng bộ nhớ ảo
 X                   định dạng đăng ký
-y                   không hiển thị cờ, hiển thị rss so với addr (được sử dụng với -l)
    --context        hiển thị ngữ cảnh bảo mật (dành cho SELinux)
    --headers        lặp lại các dòng tiêu đề, một dòng trên mỗi trang
    --no-headers     hoàn toàn không in tiêu đề
    --cols, --columns, --width <num> đặt chiều rộng màn hình
     --rows, --lines <num> đặt chiều cao màn hình
```

- Hiển thị chủ đề:
```
H                    như thể chúng là quá trình
-L                   có thể với các cột LWP và NLWP
-m, m                sau quá trình
-T                   có thể với cột SPID
```   
- Sự lựa chọn hỗn hợp:
```
-c                   hiển thị lớp lập lịch với tùy chọn -l
 c                   hiển thị tên lệnh đúng
 e                   hiển thị môi trường sau khi lệnh
 k,    --sort        chỉ định thứ tự sắp xếp là: [+ | -] key [, [+ | -] key [, ...]]
 L                   hiển thị thông số định dạng
 n                   hiển thị uid số và wchan
 S,    --cumulative  bao gồm một số dữ liệu quy trình con đã chết
-y                   không hiển thị cờ, hiển thị rss (chỉ với -l)
-V, V, --version     thông tin phiên bản màn hình và thoát
-w, w                chiều rộng đầu ra không giới hạn

       --help <simple|list|output|threads|misc|all> hiển thị trợ giúp và thoát
```