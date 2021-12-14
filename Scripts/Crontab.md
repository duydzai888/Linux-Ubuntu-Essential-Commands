# Crontab
## Menu
[1. Ghi chú](#GhiChu)

[2. Các ví dụ](#CacViDu)

[3. Lệnh trợ giúp](#LenhTroGiup)




<a name="GhiChu"></a>
### 1. Ghi chú
Lệnh crontab được sử dụng để quản lý danh sách các lệnh phải chạy theo một lịch trình cụ thể.
Mỗi người dùng có thể có crontab của riêng mình.

Nếu tệp `/usr/lib/cron/cron.allow` tồn tại, thì tên người dùng phải được liệt kê trong đó, nếu không người dùng sẽ không được phép sử dụng lệnh crontab.

Nếu tệp `/usr/lib/cron/cron.deny` tồn tại, thì tên người dùng không được liệt kê trong đó, nếu không người dùng sẽ không được phép sử dụng lệnh crontab.

<a name="CacViDu"></a>
### 2. Các ví dụ
- Quản lý crontab của người dùng hiện tại.
```
$ crontab -e
this command "echo `date` >> /home/user2/crontab_test.log" will be executed every minute
* * * * * echo `date` >> /home/user1/crontab_test.log
```

Lưu và thoát. Bạn sẽ thấy các thông báo sau trong đầu ra tiêu chuẩn:
```
# crontab: no crontab for user1 - using an empty one
# crontab: installing new crontab
```

Bạn có thể kiểm tra xem crontab đã được cài đặt chưa:
```
$ crontab -l
* * * * * echo `date` >> /home/user1/crontab_test.log
```

Bạn có thể liệt kê crontab của tất cả người dùng:
```
$ sudo ls -l /usr/lib/cron/tabs
-rw-------  1 root  root  284 14 Feb 09:00 user1
```

Bạn có thể kiểm tra crontab excution:
```
$ cat /home/user1/crontab_test.log
Sun Feb 25 09:01:00 EST 2014
Sun Feb 25 09:02:00 EST 2014
Sun Feb 25 09:03:00 EST 2014
Sun Feb 25 09:04:00 EST 2014
```

- Quản lý crontab của người dùng khác:
```
$ sudo crontab -e -u user2
# this command "echo `date` >> /home/user2/crontab_test.log" will be executed every minute
* * * * * echo `date` >> /home/user2/crontab_test.log
```

- Lưu và thoát. Bạn sẽ thấy các thông báo sau trong đầu ra tiêu chuẩn:
```
crontab: không có crontab cho user2 - sử dụng một cái trống
crontab: cài đặt crontab mới
```

- Bạn có thể kiểm tra xem crontab đã được cài đặt chưa:
```
$ sudo ls -l /usr/lib/cron/tabs
-rw-------  1 root  root  285 14 Feb 09:35 user2
-rw-------  1 root  root  284 14 Feb 09:00 user1
```

<a name="LenhTroGiup"></a>
### 3. Lệnh trợ giúp ( man crontab )
- Các tùy chọn sau có thể được sử dụng:
```
-u
| Chỉ định tên của người dùng có crontab sẽ được sử dụng.
| Nếu tùy chọn này không được đưa ra, thì crontab của người dùng hiện tại sẽ được sử dụng.
| Tùy chọn này rất quan trọng khi sử dụng "su" để chạy lệnh crontab.

-l
| Hiển thị crontab hiện tại trên đầu ra tiêu chuẩn.

-r
| Xóa crontab hiện tại.

-e
| Chỉnh sửa crontab bằng trình chỉnh sửa được chỉ định bởi các biến môi trường VISUAL hoặc EDITOR.
| Sau khi thoát khỏi trình chỉnh sửa, crontab đã sửa đổi sẽ được áp dụng tự động.
```

- Thêm các mục crontab.
Mỗi mục nhập trong crontab có thể có cú pháp sau "min hour day month day_of_week" trong đó:
```
min: [0 - 59]

hour: [0 - 23]

day: [1 - 31]

month: [1 - 12]

day of week: [0 - 7] (kiểm tra hệ thống của bạn nếu 0 hoặc 7 tham chiếu Chủ nhật)
```

- Bạn cũng có thể sử dụng các mẫu sau để khớp với giá trị của lịch biểu:
```
*: khớp với bất kỳ giá trị nào trong số các giá trị được phép

-: chỉ định một phạm vi giá trị: 9-15 (có nghĩa là bất kỳ giá trị nào từ 9 đến 15)

,: chỉ định danh sách các giá trị hoặc phạm vi giá trị: 7,9-15,35 (nghĩa là 7, bất kỳ giá trị nào từ 9 đến 15 và 35)

/: chỉ định các bước trong một phạm vi giá trị: */3 (hàng giờ, 3 giờ một lần), 8/2 (hàng giờ, cứ sau 2 giờ bắt đầu từ 8 giờ)

name_of_the_day: sử dụng ba chữ cái đầu tiên trong ngày (phạm vi hoặc danh sách tên không được phép)

name_of_the_month: sử dụng ba chữ cái đầu tiên của tháng (phạm vi hoặc danh sách tên không được phép)
```