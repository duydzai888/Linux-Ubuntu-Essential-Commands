# Linux-Ubuntu (Các lệnh cần thiết)
[1. Cấu trúc thư mục (Cấu trúc phân cấp hệ thống tệp)](#CauTrucThuMuc)

[2. Thư mục gốc](#ThuMucGoc)

[3. Đường dẫn thư mục](#DuongDanThuMuc)

[4. Các đường dẫn bắt đầu bằng dấu chấm (.), Hai dấu chấm (..) hoặc dấu ngã (~)](#CacDuongDan)

[5. Sử dụng các ký tự đại diện để xác định tên tệp và thư mục (ký tự đại diện siêu ký tự)](#SuDungCacKiTu)
## Quản lí tệp

<a name="CauTrucThuMuc"></a>
### 1. Cấu trúc thư mục (Cấu trúc phân cấp hệ thống tệp)
- Hệ thống tệp lưu trữ thông tin theo cấu trúc phân cấp có dạng cây.

- Mức gốc của cây được gọi là thư mục gốc, hoặc thư mục ảo (được biểu thị bằng một dấu gạch chéo " / ").

- Thư mục gốc chứa tất cả các tệp và thư mục từ tất cả các thiết bị (vật lý hoặc điểm gắn kết) của hệ thống.

- Mỗi thư mục có thể có các tệp hoặc các thư mục con khác bên trong nó.

- Tệp hoặc thư mục có tên bắt đầu bằng ký tự dấu chấm `.` Theo mặc định bị ẩn và không được hiển thị theo mặc định trong trình quản lý tệp (nó cũng sẽ bị ẩn nếu bạn sử dụng lệnh ls mà không có tùy chọn `-a`).

<a name="ThuMucGoc"><a/>
### 2. Thư mục gốc
![thư mục gốc](https://user-images.githubusercontent.com/84270045/142725887-ef8cadd7-a89e-4e18-856f-e905003c150d.png)

- / bin : chứa các lệnh của người dùng (cp, rm, ...)
- / sbin : chứa các lệnh quản trị
- / boot : chứa nhân linux có thể khởi động và các tệp cấu hình bộ nạp khởi động
- / dev : chứa các tệp đại diện cho các điểm truy cập vào thiết bị
- / etc : chứa các tệp cấu hình quản trị
- / home : chứa thư mục chính của người dùng
- / lib : chứa các tệp thư viện
- / media : điểm gắn kết cho các thiết bị
- / mnt : điểm gắn kết cho thiết bị, phân vùng đĩa, hệ thống tệp từ xa
- / cdrom : mount point cho cd-roms
- / proc : chứa các tệp đại diện cho tài nguyên hệ thống
- / root : thư mục của người dùng gốc
- / run : chứa các tệp tạm thời của ứng dụng
- / tmp : chứa các tệp tạm thời của ứng dụng
- / usr : chứa các tệp của người dùng (tệp nhị phân, thư viện, cài đặt, tài liệu, ...)
- / var : chứa các tệp của ứng dụng (dữ liệu, cấu hình, nhật ký, ...)

<a name="DuongDanThuMuc"></a>
### 3. Đường dẫn thư mục

- Bạn có thể xác định một thư mục hoặc một tệp bằng cách sử dụng đường dẫn tuyệt đối của nó (bắt đầu từ thư mục gốc).

- Bạn cũng có thể sử dụng một đường dẫn tương đối (liên quan đến thư mục hiện tại) để xác định một thư mục hoặc một tệp.

- Ngoài ra còn có một số dạng đặc biệt để xác định đường dẫn của một thư mục hoặc một tệp, bằng cách sử dụng dấu chấm hoặc dấu ngã của các ký tự (xem bên dưới).

- Đường dẫn cũng có thể chứa các biến mà chúng có thể được thay thế bằng giá trị của chúng khi phân giải tên đường dẫn (ví dụ: $ HOME , $ PWD ).

<a name="CacDuongDan"></a>
### 4. Các đường dẫn bắt đầu bằng dấu chấm (.), Hai dấu chấm (..) hoặc dấu ngã (~)

- Cấu trúc thư mục này sẽ được sử dụng trong các ví dụ dưới đây:
![thư mục](https://user-images.githubusercontent.com/84270045/142726810-4e5e9878-7a10-4caa-8b03-942dab13be7e.png)
    - Một đường dẫn bắt đầu bằng dấu chấm ( . ) Đại diện cho tên đường dẫn tuyệt đối của thư mục hiện tại.
    ![ls](https://user-images.githubusercontent.com/84270045/142726908-d9f8af28-6d7a-405a-8779-c0521b133a3c.png)
    
    - Một đường dẫn bắt đầu bằng hai dấu chấm ( .. ) đại diện cho tên đường dẫn tuyệt đối của thư mục mẹ của thư mục hiện tại.
    ![ls 1](https://user-images.githubusercontent.com/84270045/142727022-fe198d62-1cea-433a-89a0-98595d5ed44f.png)
    
    - Một đường dẫn bắt đầu bằng dấu ngã ( ~ ) đại diện cho tên đường dẫn tuyệt đối của thư mục chính người dùng.
    ![ls 2](https://user-images.githubusercontent.com/84270045/142727055-bcf27523-7092-4b2d-b1d1-4d14df3fd172.png)
    
    - Một chuỗi đứng trước dấu ngã ( ~ ) đại diện cho tên đường dẫn tuyệt đối của thư mục chính của người dùng được tham chiếu bởi giá trị của chuỗi.
    ![ls mtitek](https://user-images.githubusercontent.com/84270045/142727103-485babdb-96fc-4452-b832-80ce79e49eeb.png)
    
<a name="SuDungCacKiTu"></a>
### 5. Sử dụng các ký tự đại diện để xác định tên tệp và thư mục (ký tự đại diện siêu ký tự)
- Bạn có thể sử dụng một số ký tự đại diện (ký tự đại diện siêu ký tự) để khớp với một phần của tệp hoặc tên thư mục.

    - *: khớp với bất kỳ số ký tự nào.
    ![ls gấp](https://user-images.githubusercontent.com/84270045/142727157-e9b03721-7712-4a5c-a21e-485874c97ed3.png)
    
    - ? : khớp một lần xuất hiện của một ký tự.
    ![ls der](https://user-images.githubusercontent.com/84270045/142727191-8b9135b9-8bc6-458d-bd4e-6fef06f4a445.png)
    
    - [...] : xác định một lần xuất hiện, một tập hợp hoặc một phạm vi ký tự.
    ![ls f](https://user-images.githubusercontent.com/84270045/142727262-5a3b1aa7-7ec9-4d66-8898-774c8bda29f4.png)
    
- Bạn cũng có thể sử dụng dấu ngoặc nhọn ( {} ) để mở rộng một tập hợp các ký tự để khớp với một phần của tệp hoặc tên thư mục.
![tệp ls](https://user-images.githubusercontent.com/84270045/142727298-6192f1a0-9bd6-40f0-a3ed-8e5f69b38ff0.png)
![tệp ls-](https://user-images.githubusercontent.com/84270045/142727311-2af627f2-934a-45dd-b23c-01331aaee2c2.png)

- Bạn có thể sử dụng ký tự chấm than ( ! ) Để loại trừ một mẫu:
![tệp-c-3](https://user-images.githubusercontent.com/84270045/142727333-a271dbd9-4e1b-461a-97ed-b57a72ca5422.png)
