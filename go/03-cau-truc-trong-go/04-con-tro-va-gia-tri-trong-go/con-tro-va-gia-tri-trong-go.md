---
title: "Con trỏ và giá trị trong Go"
description: "Go không phải là một ngôn ngữ hướng đói tượng (OO) giống như C++, java, Ruby hoặc C#. Go không có các đối tượng cũng như khả năng kế thừa (inheritance). Do đó, Go không có các lý thuyết thường được nhắc đến khi nói về OO như đa hình (polymorphism) hay ghi đè (overloading). Thứ mà Go có là các cấu trúc, có thể kết hợp với các phương thức. Go hỗ trợ một dạng đơn giản nhưng hiệu quả của tổ hợp (composition). Nhìn chung, đó là sự kết hợp của những đoạn mã đơn giản, mà lại không cần đến một số tính năng mà OO cung cấp. (Điều đó cho thấy sự tối ưu của *composition* so với *inheritance* và Go là ngôn ngữ đầu tiên tôi sử dụng có một nền tảng vững chắc về vấn đề này.) Mặc dù Go không giống như OO mà bạn quen dùng, bạn sẽ nhận thấy có rất nhiều điểm giống nhau giữa định nghĩa một cấu trúc (structure) và định nghĩa một lớp (class)."
keywords:
  [
    "gioi thieu go",
    "giới thiệu go",
    "khoá học go",
    "giới thiệu Go",
    "giới thiệu go cơ bản",
    "go la gi",
    "tong quan ve go",
    "gioi thieu ve ngon ngu lap trinh go",
    "tom tat go",
    "code go la gi",
  ]
chapter:
  name: "Cấu trúc trong Go"
  slug: "chuong-03-cau-truc-trong-go"
category:
  name: "Go"
  slug: "go"
image: https://kungfutech.edu.vn/thumbnail.png
position: 4
---

## Con trỏ và giá trị

Khi viết mã Go, bạn có thể sẽ tự hỏi _khi nào nên dùng giá trị, khi nào thì dùng con trỏ?_ Trước hết, câu trả lời là giống nhau, trừ một trong các tình huống sau:

- Gán một biến cục bộ
- Thay đổi trường của một cấu trúc
- Giá trị trả về của một hàm
- Tham số của một hàm
- receiver của một phương thức

Sau đó, nếu bạn vẫn không chắc chắn, hãy dùng con trỏ.

Như chúng ta thấy, truyền một giá trị cho hàm là cách để giá trị đó không thay đổi được (các thay đổi bên trong hàm sẽ không làm thay đổi đến các giá trị bên ngoài hàm). Đôi khi, cách xử lý này là cách mà bạn muốn.

Thậm chí nếu bạn không muốn thay đổi dữ liệu, hãy xem xét chi phí để tạo một bản sao của một cấu trúc lớn. Ngược lại, bạn có các cấu trúc nhỏ, ví dụ:

```go
type Point struct {
  X int
  Y int
}
```

Trong trường hợp này, chi phí của việc sao chép cấu trúc là có thể bù đắp được bằng việc có thể truy cập `x` và `y` trực tiếp.

Một lần nữa, đây là tất cả các tình huống khá tinh tế. Bạn sẽ quen với điều này nếu trải nghiệm hàng nghìn hoặc hàng chục nghìn tình huống tương tự.

<content-warning>

Tóm lại, chương này giới thiệu các cấu trúc, làm thế nào để tạo một receiver cho một hàm, và chúng ta biết thêm được kiểu dữ liệu con trỏ trong Go. Các chương sau sẽ xây dựng trên những gì chúng ta biết về cấu trúc cũng như các hoạt động bên trong mà chúng ta đã tìm hiểu.

</content-warning>
