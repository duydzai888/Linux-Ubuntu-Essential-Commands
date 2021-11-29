# gzip / gunzip - Nén / giải nén
## Menu
[1. Ghi chú](#GhiChu)
- [1.1. Nén tệp](#NenTep)
- [1.2. Giải nén tệp](#GiaiNenTep)
- [1.3. Giải nén tệp ( gunzip )](#GiaiNenTepGunzip)




<a name="GhiChu"></a>
### 1. Ghi chú

<a name="NenTep"></a>
##### 1.1. Nén tệp:
- Thao tác này sẽ nén tệp `file1` và đổi tên tệp thành `file1.gz`:
```
$ touch file1
```

```
$ ls -al
-rw-r--r--  1 mtitek  mtitek  5632  3 Feb 21:01 file1
```

```
$ gzip file1
```

```
$ ls -al
-rw-r--r--  1 mtitek  mtitek  242  3 Feb 21:01 file1.gz
```

<a name="GiaiNenTep"></a>
##### 1.2. Giải nén tệp:
- Thao tác này sẽ giải nén tệp `file1.gz` và đổi tên nó thành `file1`:
```
$ gzip -d file1.gz
```

```
$ ls -al
-rw-r--r--  1 mtitek  mtitek  5632  3 Feb 21:01 file1
```

<a name="GiaiNenTepGunzip"></a>
##### 1.3. Giải nén tệp ( gunzip ):

- Bạn có thể sử dụng gunzipđể giải nén tệp " file1.gz" và đổi tên nó thành " file1":
```
$ gunzip file1.gz
```

```
$ ls -al
-rw-r--r--  1 mtitek  mtitek  5632  3 Feb 21:01 file1
```
