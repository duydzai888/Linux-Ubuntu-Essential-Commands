# du - Hiển thị thống kê sử dụng đĩa
## Menu





<a name="GhiChu"></a>
### 1. Ghi chú
Đối với mỗi tệp được chỉ định, lệnh `du` hiển thị việc sử dụng khối hệ thống tệp.

Đối với mỗi thư mục được chỉ định, lệnh `du` hiển thị việc sử dụng khối hệ thống tệp cho tất cả các thư mục con của nó.

Nếu không có lệnh nào được chỉ định, lệnh `du` sẽ hiển thị việc sử dụng khối hệ thống tệp cho tất cả các thư mục con của thư mục hiện tại.

### 2. Các ví dụ
- Hiển thị mức sử dụng khối hệ thống tệp cho tất cả các tệp và thư mục:
```
$ du -ah folder1/
 12K    folder1/
4.0K    folder1//file1
4.0K    folder1//file2
4.0K    folder1//file3
  0B    folder1//folder2
  0B    folder1//folder2/folder3
```

- Hiển thị mức sử dụng khối hệ thống tệp cho tất cả các tệp và thư mục, ngoại trừ thư mục được chỉ định khỏi danh sách:
```
$ du -h folder1/*
4.0K    folder1//file1
4.0K    folder1//file2
4.0K    folder1//file3
  0B    folder1//folder2
  0B    folder1//folder2/folder3
```

- Hiển thị việc sử dụng khối hệ thống tệp cho tất cả các thư mục con của một thư mục:
```
$ du -h folder1/
 12K    folder1/
  0B    folder1//folder2
  0B    folder1//folder2/folder3
```

- Hiển thị việc sử dụng khối hệ thống tệp cho các thư mục con của thư mục sâu thư mục "n":
```
$ du -hd 1 folder1/
 12K    folder1/
  0B    folder1//folder2
```

### 3. Lệnh trợ giúp ( man du )
- Các tùy chọn sau có thể được sử dụng:
```
-a
| Đối với mỗi thư mục được chỉ định, hiển thị việc sử dụng khối hệ thống tệp cho thư mục được chỉ định và tất cả các tệp và thư mục con của nó.

-d <depth>
| Đối với mỗi thư mục được chỉ định, hiển thị việc sử dụng khối hệ thống tệp cho tất cả các thư mục con sâu các thư mục <depth> của nó.

-s
| Hiển thị việc sử dụng khối hệ thống tệp cho từng tệp hoặc thư mục được chỉ định.
| Tương đương với "-d 0"

-c
| Hiển thị tổng mức sử dụng khối hệ thống tệp của tất cả các tệp được liệt kê.

-h
| Đầu ra "có thể đọc được của con người".
| Sử dụng các hậu tố đơn vị: Byte (-b), Kilobyte (-k), Megabyte (-m), Gigabyte (-g).

-k
| Số khối hiển thị trong các khối 1024 byte (1-Kbyte).

-m
| Số khối hiển thị trong các khối 1048576 byte (1-Mbyte).

-g
| Số khối hiển thị trong các khối 1073741824 byte (1-Gbyte).
```
