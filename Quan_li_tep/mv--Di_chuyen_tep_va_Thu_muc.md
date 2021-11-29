#  mv - Di chuyển tệp / thư mục
## Menu
[1. Ghi chú](#GhiChu)

[2. Các ví dụ](#ViDu)
- [2.1. Đang di chuyển tệp](#DiChuyenTep)
- [2.2. Đổi tên tệp](#DoiTenTep)
- [2.3. Di chuyển thư mục](#DiChuyenThuMuc)
- [2.4. Đổi tên thư mục](#DoiTenThuMuc)

[3. Lệnh trợ giúp ( man mv )](#LenhTroGiup)



<a name="GhiChu"></a>
### 1. Ghi chú
![mv](https://user-images.githubusercontent.com/84270045/143021674-36ca6e2e-9f60-47cc-a824-1bd6b519a34b.png)

`target_file` có thể là tên tệp, thư mục (trong trường hợp này tệp sẽ được chuyển đến thư mục khác), hoặc tên thư mục / tệp (trong trường hợp này tệp sẽ được chuyển đến thư mục khác và được đổi tên).

- Di chuyển một thư mục, sẽ di chuyển thư mục và tất cả nội dung của nó.
- Khi di chuyển tệp và thư mục, số inode và dấu thời gian của các tệp và thư mục này không bị thay đổi.

<a name="ViDu"></a>
### 2. Các ví dụ

<a name="DiChuyenTep"></a>
##### 2.1. Đang di chuyển tệp
- Di chuyển file1 từ folder1 sang folder2 (xem bên dưới các tùy chọn `-i` và `-n` để kiểm tra xem tệp đích đã tồn tại chưa).
```
[root@Sever ~]# mv folder1/file1 folder2
```
 Tùy chọn, bạn cũng có thể chỉ định tên tệp sẽ được sử dụng cho thư mục đích
```
[root@Sever ~]# mv folder1/file1 folder2/file1
```

- Di chuyển file1 từ folder1 sang folder2 (đổi tên file1 thành file2):
```
[root@Sever ~]# mv folder1/file1 folder2/file2
```

<a name="DoiTenTep"></a>
##### 2.2. Đổi tên tệp
```
[root@Sever ~]# mv file1 file2
```

<a name="DiChuyenThuMuc"></a>
##### 2.3. Di chuyển thư mục
```
[root@Sever ~]# mv folder1/ folder2/
```

<a name="DoiTenThuMuc"></a>
##### 2.4. Đổi tên thư mục
```
[root@Sever ~]# mv folder1 folder2
```

Bạn có thể sử dụng cả hai lệnh `cp` và `rm` lệnh để di chuyển tệp.
Đầu tiên sao chép file1 từ folder1 sang folder2 và sau đó xóa file1 trong folder1:
```
[root@Sever ~]# cp folder1/file1 folder2/; rm folder1/file1
```

<a name="LenhTroGiup"</a>
### 3. Lệnh trợ giúp ( man mv )
- Các tùy chọn sau có thể được sử dụng:

![man mv](https://user-images.githubusercontent.com/84270045/143023182-bc066e8d-dd52-49b2-81eb-784ef1841101.png)
