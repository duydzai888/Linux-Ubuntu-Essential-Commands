# ln - Make links
## Menu
[1. Ghi chú](#GhiChu)

[2. Các ví dụ](#ViDu)
- [2.1. Liên kết tượng trưng](#LienKetTuongTrung)
- [2.2. Liên kết cứng](#LienKetCung)

[3. Lệnh trợ giúp ( man ln )](#LenhTroGiup)



<a name="GhiChu"></a>
### 1. Ghi chú
- Các liên kết tượng trưng hoạt động giống như các phím tắt tham chiếu đến một tệp khác.

- Liên kết cứng thực sự là một tên gọi khác của cùng một tệp. Tệp liên kết cứng là một liên kết đến tệp gốc chứa thông tin về nó. Cả tệp liên kết cứng và tệp gốc đều đại diện cho cùng một tệp (nội dung).

Theo mặc định, `ln` tạo liên kết cứng.

Lưu ý rằng khi bạn sao chép tệp liên kết tượng trưng (hoặc tệp liên kết cứng), bạn đang sao chép tệp gốc.

<a name="ViDu"></a>
### 2. Các ví dụ

<a name="LienKetTuongTrung"></a>
##### 2.1. Liên kết tượng trưng.
- Tạo một liên kết tượng trưng đến file1:
```
$ln -s file1 sfile1
```

```
$ ls -al
-rw-r - r-- 2 mtitek mtitek 8163 10 Jan 21:04 file1
lrwxrwxrwx 1 mtitek mtitek 5 10 Jan 21:04 sfile1 -> file1
```

Lưu ý biểu tượng `->` sau tên tệp liên kết tượng trưng. Cũng lưu ý kích thước của tệp liên kết tượng trưng (5 byte so với 8163 byte của tệp gốc).

Bạn có thể sử dụng tùy chọn `-i` để in số inode của mỗi tệp (cho thấy rằng cả hai đều là các tệp vật lý riêng biệt).

- Tạo nhiều liên kết tượng trưng:
```
$ ln -s file1 file2 folder/
```

```
$ ls -al folder/
lrwxr-xr-x  1 mtitek  mtitek    5 10 Jan 21:04 file1 -> file1
lrwxr-xr-x  1 mtitek  mtitek    5 10 Jan 21:04 file2 -> file2
```

<a name="LienKetCung"></a>
##### 2.2. Liên kết cứng.

- Tạo một liên kết cứng đến file1:
```
$ln file1 hfile1
```

```
ls -al
-rw-r--r-- 2 mtitek mtitek 8163 10 Jan 21:04 file1
-rw-r--r-- 2 mtitek mtitek 8163 10 Jan 21:04 hfile1
```

Lưu ý số liên kết (số sau thông tin quyền) hiển thị cùng một số cho cả hai tệp: hai liên kết (vì chúng tôi đã tạo một liên kết tượng trưng đến tệp1).

Cũng lưu ý kích thước của tệp liên kết cứng (cả tệp liên kết cứng và tệp gốc đều có cùng kích thước: 8163 byte).

Bạn có thể sử dụng tùy chọn `-i` để in số inode của mỗi tệp (cho thấy rằng cả hai tệp đều tham chiếu đến cùng một tệp vật lý):
```
ls -ali
4313560874 -rw-r--r-- 2 mtitek mtitek 8163 10 Jan 21:04 file1
4313560874 -rw-r--r-- 2 mtitek mtitek 8163 10 Jan 21:04 hfile1
```

<a name="LenhTroGiup"></a>
### 3. Lệnh trợ giúp ( man ln )
```
-NS
| Tạo một liên kết tượng trưng.

-NS
| Nếu tệp đích đã tồn tại, hãy hủy liên kết nó để liên kết có thể xuất hiện.
| Tùy chọn -f ghi đè bất kỳ tùy chọn -i nào trước đó.

-i
| Nếu tệp đích đã tồn tại, hãy yêu cầu xác nhận của người dùng ('y' hoặc 'Y') trước khi hủy liên kết để liên kết có thể xuất hiện.
| Tùy chọn -i ghi đè bất kỳ tùy chọn -f nào trước đó.

-v
| Nguyên nhân dài dòng, hiển thị các tệp khi chúng được xử lý.
```
