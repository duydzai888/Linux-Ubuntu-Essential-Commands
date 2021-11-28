# User
## Menu
[1. Người giới thiệu](#NguoiGioiThieu)

[2. Ai đang đăng nhập ( Users )](#Users)

[3. Thêm người dùng mới ( Useradd )](#Useradd)

[4. Thay đổi tài khoản người dùng ( Usermod )](#Usermod)

[5. Xóa tài khoản người dùng ( Userdel )](#Userdel)

[6. Ẩn người dùng khỏi màn hình đăng nhập](#AnNguoiDung)

[7. Bật / Tắt đăng nhập SSH từ xa cho một người dùng cụ thể](#BatTatDangNhapSSH)



<a name="NguoiGioiThieu"></a>
### 1. Người giới thiệu
 Xem thông tin chi tiết về quản lí người dùng tại [Ubuntu Server Guide](https://help.ubuntu.com/ctures/serverguide/user-management.html)

<a name="Users"></a>
### 2. Ai đang đăng nhập ( Users )
In người dùng hiện đang đăng nhập:
```
$ users
mtitek admin
```

<a name="Useradd"></a>
### 3. Thêm người dùng mới ( useradd )
Sử dụng lệnh useradd để thêm người dùng mới ( man useradd ):
```
Cách sử dụng: useradd [tùy chọn] USER

Tùy chọn:
-b, --base-dir BASE_DIR       thư mục cơ sở cho thư mục chính của tài khoản mới (mặc định "/home") account (default "/home")
-d, --home-dir HOME_DIR       thư mục chính của tài khoản mới (mặc định: "/{BASE_DIR}/{USER}")
-m, --create-home             tạo thư mục chính của người dùng
-G, --groups GROUPS           danh sách các nhóm bổ sung của tài khoản mới
-s, --shell SHELL             vỏ đăng nhập của tài khoản mới (/bin/false để dừng đăng nhập SSH)
-c, --comment COMMENT         bình luận
-e, --expiredate EXPIRE_DATE  ngày hết hạn của tài khoản mới
-f, --inactive INACTIVE       thời gian không hoạt động của mật khẩu của tài khoản mới
```

Lệnh `useradd` ảnh hưởng đến hai tệp `/etc/passwd` và `/etc/group`.
Đây là cách dữ liệu được cấu trúc trong các tệp này:
- /etc/passwd
```
$ cat /etc/passwd | grep mtitek
mtitek:x:1000:1000:mtitek:/home/mtitek:/bin/bash
```
    
- Ở đâu:

    - `mtitek`: tên tài khoản.
    
    - `x`: Trình giữ chỗ cho mật khẩu. Mật khẩu được lấy từ tệp `/etc/shadow`.
    
    - `1000`: Tên người dùng.
    
    - `1000`: Id nhóm.
    
    - `mtitek`: Bình luận.
    
    - `/home/mtitek`: Thư mục chính.
    
    - `/bin/bash`: Vỏ người dùng.
    

- /etc/group
```
$ cat /etc/group | grep mtitek
mtitek:x:1000:mtitek
```
- Ở đâu:

    - `mtitek`: tên nhóm.
    
    - `x`: Trình giữ chỗ cho thông tin mật khẩu. Mật khẩu được lấy từ tệp `/etc/gshadow`.
    
    - `1000`: Id nhóm.
    
    - `mtitek`: Danh sách người dùng thuộc nhóm được phân tách bằng dấu phẩy.
    
Ví dụ
- Tạo người dùng có tên `mtitek1` với nhóm mặc định có tên "mtitek1"
```
$ sudo useradd mtitek1

$ cat /etc/passwd | grep mtitek1
mtitek1:x:1003:1004::/home/mtitek1:/bin/sh

$ cat /etc/group | grep mtitek1
mtitek1:x:1004:
```

- Tạo người dùng có tên `mtitek1` với nhóm mặc định có tên `mtitek1`.
    + Tạo thư mục chính `/home/mtitek1`.
    + Đặt `/bin/bash` làm trình bao mặc định cho người dùng.
```
$ sudo useradd -m -s /bin/bash mtitek1

$ cat /etc/passwd | grep mtitek1
mtitek1:x:1003:1004::/home/mtitek1:/bin/bash

$ cat /etc/group | grep mtitek1
mtitek1:x:1004:
```

- Tạo người dùng có tên `mtitek1` với nhóm mặc định có tên "mtitek1".
    + Tạo thư mục chính `/home/mtitek1`.
    + Gán người dùng vào nhóm `group1` và `group2`.
    + Đặt "/bin/bash" làm trình bao mặc định cho người dùng.
```
$ sudo useradd -m -G group1,group2 -s /bin/bash mtitek1

$ cat /etc/passwd | grep mtitek1
mtitek1:x:1003:1004::/home/mtitek1:/bin/bash

$ cat /etc/group | grep mtitek1
mtitek1:x:1004:
group1:x:1001:mtitek1
group2:x:1002:mtitek1
```

- Tạo người dùng có tên `mtitek1` với nhóm mặc định có tên `mtitek1`.
    + Đặt thư mục chính cơ sở thành `/mtitek1_home_dir`.
    + Tạo thư mục chính cơ sở `/mtitek1_home_dir`.
```
$ sudo useradd -m -d /mtitek1_home_dir mtitek1

$ cat /etc/passwd | grep mtitek1
mtitek1:x:1003:1004::/mtitek1_home_dir:/bin/sh

$ cat /etc/group | grep mtitek1
mtitek1:x:1004:

$ ls -al /mtitek1_home_dir
drwxr-xr-x  4 mtitek1 mtitek1 4096 Nov 27 12:51 .
drwxr-xr-x 26 root root 4096 Nov 27 12:51 ..
-rw-r--r--  2 mtitek1 mtitek1 4096 Nov 27 12:51 .profile
-rw-r--r--  2 mtitek1 mtitek1 4096 Nov 27 12:51 .bashrc
-rw-r--r--  2 mtitek1 mtitek1 4096 Nov 27 12:51 .bash_logout
```

- Tạo người dùng có tên `mtitek1` với nhóm mặc định có tên "mtitek1".
    + Đặt thư mục cơ sở thành `/user_base_dir`.
    + Tạo thư mục chính cơ sở `/user_base_dir/mtitek1`.
```
$ sudo mkdir /user_base_dir
$ sudo useradd -m -b /user_base_dir mtitek1

$ cat /etc/passwd | grep mtitek1
mtitek1:x:1003:1004::/user_base_dir/mtitek1:/bin/sh

$ cat /etc/group | grep mtitek1
mtitek1:x:1004:

$ ls -al /user_base_dir
drwxr-xr-x  4 root root 4096 Nov 27 12:51 .
drwxr-xr-x 26 root root 4096 Nov 27 12:51 ..
drwxr-xr-x  2 mtitek1 mtitek1 4096 Nov 27 12:51 mtitek1

$ ls -al /user_base_dir/mtitek1
drwxr-xr-x  4 mtitek1 mtitek1 4096 Nov 27 12:51 .
drwxr-xr-x 26 root root 4096 Nov 27 12:51 ..
-rw-r--r--  2 mtitek1 mtitek1 4096 Nov 27 12:51 .profile
-rw-r--r--  2 mtitek1 mtitek1 4096 Nov 27 12:51 .bashrc
-rw-r--r--  2 mtitek1 mtitek1 4096 Nov 27 12:51 .bash_logout
```

<a name="Usermod"></a>
### 4. Thay đổi tài khoản người dùng ( usermod )
Cập nhật thông tin tài khoản của người dùng ( man usermod ):
```
Sử dụng: usermod [options] USER

Tùy chọn:
  -d, --home HOME_DIR           thư mục chính mới cho tài khoản người dùng
  -s, --shell SHELL             vỏ đăng nhập mới cho tài khoản người dùng
  -G, --groups GROUPS           danh sách mới các NHÓM bổ sung
  -a, --append                  nối người dùng vào NHÓM bổ sung được đề cập bởi tùy chọn -G mà không xóa họ khỏi các nhóm khác
  -c, --comment COMMENT         bình luận
  -L, --lock                    khóa tài khoản người dùng
  -U, --unlock                  mở khóa tài khoản người dùng
  -e, --expiredate EXPIRE_DATE  đặt ngày hết hạn tài khoản thành EXPIRE_DATE
  -f, --inactive INACTIVE       đặt mật khẩu không hoạt động sau khi hết hạn thành INACTIVE
```
  
Ví dụ
    - Thay đổi thư mục chính của người dùng và giao diện người dùng:
 ```
 $ sudo usermod --home /home/mtitek1_new_home_directory/ --shell /bin/bash mtitek1
 ```
 
    - Hạn chế người dùng truy cập tài khoản của mình:
```
$ sudo usermod --shell /usr/sbin/nologin mtitek1
```

<a name="Userdel"></a>
### 5. Xóa tài khoản người dùng ( userdel )
Xóa người dùng ( man userdel ):
```
Sử dụng: userdel [options] USER

Options:
  -r, --loại bỏ     loại bỏ thư mục chính và thư mục
  -f, --hiệu lục    buộc xóa tệp, ngay cả khi người dùng không sở hữu
```

Ví dụ:
    - Xóa người dùng `mtitek1`:
```
$ sudo userdel -r mtitek1
userdel: mtitek1 mail spool (/var/mail/mtitek1) not found
userdel: mtitek1 home directory (/home/mtitek1) not found
```

<a name="AnNguoiDung"></a>
### 6. Ẩn người dùng khỏi màn hình đăng nhập
Bạn cần cấu hình AccountsService.
Để ẩn người dùng có tên `admin1`, hãy tạo tệp có tên `/var/lib/AccountsService/users/admin1` và thêm thông tin sau.
```
$ sudo vi /var/lib/AccountsService/users/admin1
[User]
SystemAccount=true
```

<a name="BatTatDangNhapSSH"></a>
### 7. Bật / Tắt đăng nhập SSH từ xa cho một người dùng cụ thể
Bạn có thể cần chỉnh sửa tệp `/etc/ssh/sshd_config` và thực hiện một trong những thao tác sau:
```
$ sudo vi /etc/ssh/sshd_config
# permit root login: yes/no
PermitRootLogin no

# allow some users
AllowUsers user2

# deny some users
DenyUsers user1
```

Tải lại cấu hình SSH:
```
$ sudo /etc/init.d/ssh reload
```