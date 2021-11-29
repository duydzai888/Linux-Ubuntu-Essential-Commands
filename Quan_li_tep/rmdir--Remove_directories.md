# rmdir -- Remove directories
## Menu
[1. Ghi chú](#GhiChu)

[2. Các ví dụ](#ViDu)
- [2.1. Xóa một thư mục](#XoaMotThuMuc)
- [2.2. Xóa một thư mục và các thư mục con của nó](#XoaMotThuMucVaThuMucConCuaNo)

<a name="GhiChu"></a>
### 1. Ghi chú

Lệnh `rmdir` loại bỏ danh sách các thư mục đã cung cấp (chúng được loại bỏ theo thứ tự đã cho).

Thư mục phải trống để được xóa bằng lệnh `rmdir`.

Bạn phải nhập tất cả các thư mục con trước thư mục mẹ của chúng để có thể xóa tất cả chúng.

<a name="ViDu"></a>
### 2. Các ví dụ

<a name="XoaMotThuMuc"></a>
##### 2.1. Xóa một thư mục.
```
$ rmdir folder1
```
Thư mục phải trống, nếu không, bạn sẽ gặp lỗi này: `rmdir: folder: Directory not blank`.

<a name="XoaMotThuMucVaThuMucConCuaNo"></a>
##### 2.2. Xóa một thư mục và các thư mục con của nó.
```
$ rmdir folder/folder1 folder/folder2 folder
```
