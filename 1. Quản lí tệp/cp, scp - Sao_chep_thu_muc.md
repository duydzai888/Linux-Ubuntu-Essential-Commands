# cp / scp - sao chép tệp / thư mục
## Menu
[1. Ghi chú](#GhiChu)

[2. Các ví dụ](#ViDu)
- [2.1. Đang sao chép tệp](#SaoChepTep)
- [2.2. Sao chép thư mục](#SaoChepThuMuc)
- [2.3. Sao chép an toàn tệp / thư mục](#SaoChepAnToan)

[3. Lệnh trợ giúp ( man cp )](#LenhTroGiup)

<a name="GhiChu"></a>
### 1. Ghi chú
![cp](https://user-images.githubusercontent.com/84270045/143012122-eb3034ec-7854-4e48-bd71-ebb14f9b4c5c.png)

<a name="ViDu"></a>
### 2. Các ví dụ

<a name="SaoChepTep"></a>
##### 2.1. Đang sao chép tệp
- Tạo một bản sao mới của `file1` và đổi tên thành `file2` (xem bên dưới các tùy chọn `-i` và `-n` để kiểm tra xem tệp đích đã tồn tại chưa):
    ```
    [root@Sever ~]# cp file1 file2
    ```

- Sao chép tệp1 từ thư mục1 sang thư mục2 (bạn nên sử dụng dấu gạch chéo ở phía sau để rõ ràng về thư mục đích).
    ```
    [root@Sever ~]# cp folder1/file1 folder2/
    ```
    
- Tùy chọn, bạn cũng có thể chỉ định tên tệp sẽ được sử dụng cho thư mục đích
    ```
    [root@Sever ~]# cp folder1/file1 folder2/file1
    ```
    
- Sao chép file1 (đổi tên thành file2) từ folder1 sang folder2:
     ```
    [root@Sever ~]# cp folder1/file1 folder2/file2
    ```
    
- Sao chép tất cả các tệp (không bao gồm các thư mục con và các tệp bắt đầu bằng dấu chấm `.`) Trong `folder1` vào `folder2`:
    ```
    [root@Sever ~]# cp folder1/* folder2/
    ```
    
    Nó có thể pthông báo rằng có các thư mục con trong folder2 `cp: omitting directory ...`
- Sao chép tất cả các tệp bắt đầu bằng dấu chấm `.` (Không bao gồm các thư mục con) trong folder1 vào folder2:
    ```
    [root@Sever ~]# cp folder1/.* folder2/
    ```
    Nó có thể thông báo rằng có các thư mục con trong folder2 `cp: omitting directory ...`


<a name="SaoChepThuMuc"></a>
##### 2.2. Sao chép thư mục
- Sao chép thư mục folder1 trong folder2:
    ```
    [root@Sever ~]# cp -R folder1 folder2/
    ```
    
- Sao chép nội dung (tệp và thư mục con) của thư mục folder1 vào folder2:
    ```
    [root@Sever ~]# cp -R folder1/ folder2/
    ```
    
- Sao chép nội dung (tệp và thư mục con ngoại trừ tệp bắt đầu bằng dấu chấm `.`) Của thư mục folder1 sang folder2:
    ```
    [root@Sever ~]# cp -R folder1/* folder2/
    ```

<a name="SaoChepAnToan"></a>
##### 2.3. Sao chép an toàn tệp / thư mục:
- Sao chép tệp từ xa vào thư mục cục bộ:
    ```
    [root@Sever ~]# scp user1@my-remote-host.com:/folder1/folder2/index.php ~/
    ```
    
- Sao chép một thư mục từ xa vào một thư mục cục bộ:
    ```
    [root@Sever ~]# scp -r user1@my-remote-host.com:/folder1/folder2/ ~/
    ```
    
- Sao chép một tệp cục bộ vào một thư mục từ xa:
    ```
    [root@Sever ~]# scp ~/file1 user1@my-remote-host.com:/folder1/folder2/
    ```
    
- Sao chép một thư mục cục bộ vào một thư mục từ xa:
    ```
    [root@Sever ~]# scp -r ~/folder user1@my-remote-host.com:/folder1/folder2/
    ```

<a name="LenhTroGiup"></a>
### 3. Lệnh trợ giúp ( man cp )
- Các tùy chọn sau có thể được sử dụng:

![man cp](https://user-images.githubusercontent.com/84270045/143018077-217aaab7-cd12-45ff-b008-089f506a8947.png)
    
    