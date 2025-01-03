# Lời mở đầu
- Đây là phần 1 của series coding convention cho ngôn ngữ Golang
- Ở series này mình sẽ tập trung vào việc liệt kê các quy tắc và giải thích cho mọi người rằng tại sao lại cần phải tuân thủ chúng
- Các quy tắc dưới đây mình tổng hợp và thu thập chủ yếu trong quá trình mình làm việc ở nhiều nơi. Tuy mỗi nơi làm việc sẽ thường có những quy tắc khác nhau nhưng chung quy họ vẫn sẽ tuân thủ các quy tắc sau đây

# Linting và Formatting
## Naming
- Đối với việc đặt tên functions, variables, struct, interface, ...
- Sử dụng `UpperCamelCase` cho những thứ public và `lowerCamelCase` cho những thứ private
    - Ví dụ:
```go
// Những thứ public và có thể được import từ pkg khác
type Person interface{}
type Student struct{}

func PublicFunc() {}
func (s *Student) PublicMethod() {}

// Những thứ private chỉ sử dụng trong pkg hiện tại
var myArray []string
testPerson := &Student{}

func privateFunc() {}
func (s *Student) privateMethod() {}
```
- Tại sao:
  - Bới theo syntax của golang, nếu bạn đặt tên các struct, interface, func, ... với chữ cái đầu tiên viết hoa, Golang sẽ hiểu những thứ đó là public
  - Chính vì vậy nên các format khác như `snake_case` hay `lowercase` không được áp dụng
    - Bởi nếu bạn sử dụng `snake_case` thì mọi thứ sẽ luôn là private

  
- Đối với việc đặt tên cho package, chỉ sử dụng `lowercase`
  - Ví dụ:
```go
// Nên
package strconv
package main
package syslog

// Không nên
package strConv
package sys_log
```
- Tại sao:
  - Golang được thiết kế để tránh các phức tạp không cần thiết. Việc bắt buộc tên package sử dụng chữ thường giúp tránh các vấn đề liên quan đến:
    - Phân biệt chữ hoa và chữ thường trên các hệ điều hành khác nhau (case sensitivity).
    - Golang không cho phép sử dụng hai package với tên trùng nhau, bất kể có sự khác biệt về chữ hoa hay chữ thường. Điều này đảm bảo rằng tên package luôn duy nhất mà không cần kiểm tra case.
    - Sự thiếu nhất quán khi một số package sử dụng chữ hoa còn một số khác sử dụng chữ thường.


- Thêm một điểm cần chú ý khi đặt tên là hãy tránh các từ lặp lại khi đặt tên package và func/structs trong package
- Ví dụ:
```go
// Đây là ví dụ không nên làm theo
package file

func FileRead(){}
func ReadFile(){}
```
- Chúng ta không nên làm theo ví dụ trên bởi khi pkg khác import function này, chúng sẽ trở thành `file.FileRead()` và `file.ReadFile()`
- Từ `file` sẽ được lặp lại nhiều lần
- Ta nên làm theo như sau
```go
package file

func Read()
```
- Như vậy, khi func được import bởi pkg khác, chúng sẽ trở thành `file.Read()`