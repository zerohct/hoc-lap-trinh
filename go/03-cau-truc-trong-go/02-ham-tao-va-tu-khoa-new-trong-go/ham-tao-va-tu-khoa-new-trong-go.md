---
title: "Hàm tạo và từ khoá new trong Go"
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
position: 2
---

## Hàm tạo (Constructors) trong Go

Cấu trúc thì không có hàm tạo. Thay vào đó, bạn tạo một hàm trả về một biến với cấu trúc định nghĩa trước (giống như một factory):

```go
func NewSaiyan(name string, power int) *Saiyan {
  return &Saiyan{
    Name: name,
    Power: power,
  }
}
```

Rất nhiều lập trình viên mắc lỗi ở đây. Một mặt, có một chút thay đổi cú pháp; mặt khác, viết theo cách có ít sự khác biệt hơn.

`factory` không trả về một con trỏ, nhưng vẫn hoàn toàn hợp lệ:

```go
func NewSaiyan(name string, power int) Saiyan {
  return Saiyan{
    Name: name,
    Power: power,
  }
}
```

## Từ khoá `New` trong Go

Dù không có hàm tạo, Go vẫn có một hàm dựng sẵn `new` để cấp phát bộ nhớ cho một kiểu dữ liệu. Kết quả của `new(X)` giống như `&X{}`:

```go
goku := new(Saiyan)
// giống như
goku := &Saiyan{}
```

Bạn sử dụng cách nào thì tùy, nhưng bạn sẽ thấy đa phần người ta chọn cách sau khi họ có thể khởi tạo các trường dữ liệu, cũng như đoạn mã trở nên sáng sủa hơn:

```go
goku := new(Saiyan)
goku.name = "goku"
goku.power = 9001

//vs

goku := &Saiyan {
  name: "goku",
  power: 9000,
}
```

Dù bạn chọn cách nào, nếu bạn làm theo các mô hình factory ở trên, bạn có thể bảo vệ phần còn lại của mã của bạn khỏi lo ngại về vấn đề cấp phát bộ nhớ.
