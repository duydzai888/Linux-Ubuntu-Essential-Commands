# Các kí tự đặc biệt

### 1. Các ví dụ
- Dấu ngoặc kép ký tự `"` được sử dụng để phân tách một giá trị chuỗi.
Nếu chuỗi chứa các ký tự đặc biệt ( `$`, `\` ), chúng sẽ được diễn giải trước khi trả về kết quả cuối cùng.
```
$ var1=xyz

$ echo "text1 $var1 \$notvar"
text1 xyz $notvar
```

- Dấu nháy đơn ký tự `'` được sử dụng để phân tách một giá trị chuỗi.
Nếu chuỗi chứa các ký tự đặc biệt ( `$`, `\` ), chúng sẽ không được diễn giải và chúng sẽ được trả về như trong kết quả cuối cùng.
```
$ var1=xyz

$ echo 'text1 $var1 \$notvar'
text1 $var1 \$notvar
```

- Ký tự dấu trọng âm **(`)** được sử dụng để phân tách một giá trị chuỗi.
Toàn bộ chuỗi sẽ được diễn giải trước khi trả về kết quả cuối cùng.
```
$ echo `date | tr [A-Z] [a-z]`
sat 24 feb 2015 16:21:33 est
```