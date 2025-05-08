
# 💡 Tips Tối Ưu Hóa Code Trong Go (Golang)

Viết code Go hiệu quả không chỉ giúp chương trình chạy nhanh hơn mà còn cải thiện khả năng bảo trì và mở rộng. Dưới đây là một số mẹo giúp bạn tối ưu hóa code của mình trong Golang! 🚀

---

## 1. ✅ Tránh cấp phát bộ nhớ không cần thiết

**Sai:**
```go
data := make([]int, 0)
for i := 0; i < 1000; i++ {
    data = append(data, i)
}
```

**Đúng:**
```go
data := make([]int, 0, 1000) // Cấp phát sẵn capacity
for i := 0; i < 1000; i++ {
    data = append(data, i)
}
```

🔍 *Việc cấp phát trước capacity cho slice giúp tránh việc reallocation trong quá trình append, tiết kiệm thời gian và bộ nhớ.*

---

## 2. ⛔ Không dùng `interface{}` nếu không cần thiết

**Sai:**
```go
func Print(v interface{}) {
    fmt.Println(v)
}
```

**Đúng:**
```go
func Print(v string) {
    fmt.Println(v)
}
```

🔍 *Sử dụng `interface{}` làm mất đi lợi ích của static typing, và có thể ảnh hưởng hiệu năng do cần type assertion.*

---

## 3. 🧮 Sử dụng buffer khi thao tác với chuỗi lớn

**Ví dụ:**
```go
var b strings.Builder
for i := 0; i < 10000; i++ {
    b.WriteString("hello")
}
result := b.String()
```

✅ *`strings.Builder` hiệu quả hơn nhiều so với dùng phép cộng chuỗi (`+`) trong vòng lặp.*

---

## 4. 🚫 Tránh sử dụng goroutine quá mức

**Sai:**
```go
for _, item := range items {
    go process(item)
}
```

**Đúng:**
```go
sem := make(chan struct{}, 10) // Giới hạn 10 goroutines chạy song song
for _, item := range items {
    sem <- struct{}{}
    go func(i Item) {
        defer func() { <-sem }()
        process(i)
    }(item)
}
```

🔍 *Tạo quá nhiều goroutine cùng lúc có thể gây nghẽn hoặc "out of memory". Luôn giới hạn số lượng chạy song song nếu có thể.*

---

## 5. 📦 Dùng các package chuẩn đúng cách

- `sync.Pool` → tái sử dụng đối tượng, giảm GC
- `context.Context` → kiểm soát timeout, hủy bỏ goroutine
- `time.Timer` / `time.Ticker` → tối ưu xử lý theo chu kỳ

---

## Kết luận 🧠

Tối ưu hóa không phải là viết code "hacky" hay khó đọc, mà là viết **đúng cách, đúng lúc và đúng chỗ**. Hãy hiểu cách Go hoạt động để tận dụng tối đa sức mạnh của nó!
