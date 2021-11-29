# chmod - Thay đổi ACL của tệp (Danh sách kiểm soát truy cập)
## Menu
[1. Ghi chú](#GhiChu)

[2. Các ví dụ](#ViDu)
- [2.1. Thêm mục ACL mới cấp quyền read, write, append và execute cho user1 trên tệp "file1".](#ThemMucACLMoiCapQuyen)
- [2.2. Thêm mục ACL mới từ chối quyền write, append và execute cho "user2" trên tệp "file1".](#ThemMotMucACLTuChoiQuyen)
- [2.3. Thêm mục nhập ACL mới, ở một vị trí cụ thể, cấp quyền read cho "user3" trên tệp "file1".](#ThemMucNhapACLMoi)
- [2.4. Xóa mục nhập ACL trên tệp "file1".](#XoaMucNhapACLTrenTep)
- [2.5. Sửa đổi mục nhập ACL theo chỉ mục của nó](#SuaDoiMucNhapACLTheoChiMucCuaNo)

[3. Lệnh trợ giúp ( man chmod )](#LenhTroGiup)




<a name="GhiChu"></a>
### 1. Ghi chú
Các `chmod` lệnh có thể được sử dụng để sửa đổi các Access Control Lists (ACL) gắn liền với các tập tin và thư mục.

Các `chmod` lệnh cũng có thể được sử dụng để thay đổi chế độ tập tin của tập tin và thư mục: chmod - chế độ tập sự thay đổi .

Nếu tệp / thư mục có ACL, dấu `+` sẽ được in khi sử dụng lệnh `ls -l`.

Mỗi tệp / thư mục có một ACL, chứa danh sách các mục nhập có thứ tự.
Mỗi mục nhập đề cập đến một người dùng hoặc nhóm và cấp (`allow`) hoặc từ chối (`từ chối`) một tập hợp các quyền.
Trong trường hợp người dùng và nhóm tồn tại có cùng tên, người dùng hoặc tên nhóm có thể được đặt trước bằng `người dùng:` hoặc `nhóm:`.
Nếu người dùng hoặc tên nhóm chứa khoảng trắng, bạn có thể sử dụng `:`

<a name="ViDu"></a>
### 2. Các ví dụ

<a name="ThemMucACLMoiCapQuyen"></a>
##### 2.1. Thêm mục ACL mới cấp quyền `read`, `write`, `append` và `execute` cho `user1` trên tệp "file1".
```
$ ls -le file1
-rwx------  1 mtitek  mtitek  5  7 Feb 07:45 file1

#change ACL permissions
$ chmod +a "user:user1 allow read,write,append,execute" file1

$ ls -le file1
-rwx------+ 1 mtitek  mtitek  5  7 Feb 07:45 file1
 0: user:user1 allow read,write,execute,append
 ```
 
 <a name="ThemMotMucACLTuChoiQuyen"></a>
##### 2.2. Thêm mục ACL mới từ chối quyền `write`, `append` và `execute` cho "user2" trên tệp "file1".
 ```
#change ACL permissions
$ chmod +a "user:user2 deny write,append,execute" file1

$ ls -le
-rwx------+ 1 mtitek  mtitek  5  7 Feb 07:45 file1
 0: user:user2 deny write,execute,append
 1: user:user1 allow read,write,execute,append
 ```
 
 <a name="ThemMucNhapACLMoi"></a>
##### 2.3. Thêm mục nhập ACL mới, ở một vị trí cụ thể, cấp quyền `read` cho "user3" trên tệp "file1"
 ```
#change ACL permissions
$ chmod +a# 2 "user:user3 allow read" file1

$ ls -le
-rwx------+ 1 mtitek  mtitek  5  7 Feb 07:45 file1
 0: user:user2 deny write,execute,append
 1: user:user1 allow read,write,execute,append
 2: user:user3 allow read
 ```
 
 <a name="XoaMucNhapACLTrenTep"></a>
##### 2.4. Xóa mục nhập ACL trên tệp "file1".

    - Xóa quyền ghi từ chối cho "user2" trên tệp "file1":
    ```
    #change ACL permissions
    $ chmod -a "user:user2 deny write" file1

    #Note that only the "deny write" permission is deleted for "user2"
    $ ls -le
    -rwx------+ 1 mtitek  mtitek  4  7 Feb 07:45 file1
    0: user:user2 deny execute,append
    1: user:user1 allow read,write,execute,append
    2: user:user3 allow read
    ```
    
    - Xóa từ chối thực thi và thêm quyền cho "user2" trên tệp "file1":
    ```
    $ chmod -a "user:user2 deny execute,append" file1

    #Note that "user2" has now no ACL entry
    $ ls -le
    -rwx------+ 1 mtitek  mtitek  4  7 Feb 07:45 file1
    0: user:user1 allow read,write,execute,append
    1: user:user3 allow read
    ```
    
    - Xóa mục nhập ACL theo chỉ mục của nó
    ```
    $ chmod -a# 0 file1

    #Note that "user1" has now no ACL entry
    $ ls -le
    -rwx------+ 1 mtitek  mtitek  4  7 Feb 07:45 file1
     0: user:user3 allow read
     ```

<a name="SuaDoiMucNhapACLTheoChiMucCuaNo"></a>
##### 2.5. Sửa đổi mục nhập ACL theo chỉ mục của nó
```
#change ACL permissions
$ chmod =a# 0 "group:group1 deny write,execute,append" file1

$ ls -le
-rwx------+ 1 mtitek  mtitek  5  7 Feb 07:45 file1
 0: group:group1 deny write,execute,append
 ```
 
- Đặt quyền `list`, `search`, `add_file`, `add_subdirectory` và `delete_child` thành "user1" trên thư mục "folder1".
```
$ mkdir folder1

$ ls -le
drwxr-xr-x  2 mtitek  mtitek  68  7 Feb 07:52 folder1

#change ACL permissions
$ chmod +a "user:user1 allow list,search,add_file,add_subdirectory,delete_child" folder1

$ ls -le
drwxr-xr-x+ 2 mtitek  mtitek  68  7 Feb 07:52 folder1
0: user:user1 allow list,add_file,search,add_subdirectory,delete_child
```
 
<a name="LenhTroGiup"></a>
### 3. Lệnh trợ giúp ( man chmod )
- Các tùy chọn sau có thể được sử dụng:
 ```
 +a
| Thêm mục nhập ACL.
| Nếu mục nhập ACL đề cập đến danh tính đã được liệt kê, mục nhập mới sẽ được kết hợp với danh tính hiện có.

-a
| Xóa mục nhập ACL.
| Tất cả các mục nhập khớp chính xác với mục nhập đã cung cấp sẽ bị xóa.
| Nếu mục nhập liệt kê một tập hợp con các quyền được cấp bởi mục nhập, thì chỉ những quyền được liệt kê mới bị xóa.

+a#
| Thêm mục nhập ACL bằng cách sử dụng chỉ mục để chỉ định vị trí của mục nhập.

-a#
| Xóa mục nhập ACL theo chỉ mục của nó.

= a #
| Cập nhật mục nhập ACL theo chỉ mục của nó.

-N
| Xóa các mục ACL khỏi (các) tệp được đặt tên.
```

- Các quyền sau có thể áp dụng cho các tệp:
```
read
| Quyền đọc tệp.

write
| Quyền ghi vào tệp.
| Bạn có thể cần quyền "chắp thêm" để nối dữ liệu vào tệp.

append
| Quyền nối dữ liệu vào tệp (không cho phép thay đổi dữ liệu đã ghi trước đó).

execute
| Quyền thực thi tệp.
```

- Các quyền sau được áp dụng cho các thư mục:
```
list
| Quyền liệt kê các tệp và thư mục.

search
| Quyền tìm kiếm tệp theo tên.

add_file
| Quyền thêm tệp.

add_subdirectory
| Quyền thêm một thư mục con.

delete_child
| Quyền xóa nội dung của thư mục.
| Bạn cũng có thể cần quyền "tìm kiếm".
```

- Các quyền sau có thể áp dụng cho các tệp và thư mục:
```
chown
| Quyền thay đổi quyền sở hữu tệp và thư mục.

delete
| Quyền xóa tệp và thư mục.

readattr
| Quyền đọc các thuộc tính cơ bản của tệp và thư mục.
| Điều này được cấp ngầm nếu tệp và thư mục có thể được tra cứu.

writeattr
| Quyền ghi các thuộc tính cơ bản của tệp và thư mục.

readextattr
| Quyền đọc các thuộc tính mở rộng của tệp và thư mục.

writeextattr
| Quyền ghi các thuộc tính mở rộng của tệp và thư mục.

readsecurity
| Quyền đọc thông tin bảo mật mở rộng (ACL) của tệp và thư mục.

writesecurity
| Quyền ghi thông tin bảo mật (mode, ACL) của tệp và thư mục.
```

- Kế thừa ACL được kiểm soát với các quyền sau:
```
file_inherit
| Cho phép các tệp mới tạo kế thừa các quyền ACL.

directory_inherit
| Cho phép các thư mục mới được tạo kế thừa các quyền ACL.
```
 
