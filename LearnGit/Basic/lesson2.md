## Cài Git vào Linux (ubuntu/Debian)

```tsx
$ sudo apt-get install git
```

- Hoặc lệnh sau để cài trên CentOS/Fedora/RHEL.

```tsx
$ yum install git
```

## Cài Git vào Mac OS

Đối với Mac, bạn có thể sử dụng file installer tải tại địa chỉ [http://git-scm.com/download/mac](https://git-scm.com/download/mac) để cài đặt.

## Cài Git vào Windows

Nếu bạn dùng Windows thì có thể tải file .exe cài đặt Git tại địa chỉ [http://git-scm.com/download/win](https://git-scm.com/download/win). Khi cài bạn có thể để nguyên tùy chọn mặc định mà không cần tùy chỉnh gì thêm nếu bạn chưa hiểu về nó.

# **Thiết lập chứng thực cá nhân**

Sau khi cài Git xong, việc đầu tiên bạn nên làm là khai báo tên và địa chỉ email vào trong file cấu hình của Git trên máy. Để làm điều này bạn sẽ cần sử dụng hai lệnh sau đây để thiết lập tên và email.

```tsx
$ git config --global user.name "Thach Pham"
$ git config --global user.email "contact@thachpham.com"
```

Sau khi thiết lập xong, bạn có thể kiểm tra thông tin chứng thực trên user của bạn bằng cách xem tập tin `~/.gitconfig` (nhắc lại rằng dấu `~` nghĩa là thư mục gốc của user).

```tsx
$ cat ~/.gitconfig
[user]
 name = Thach Pham
 email = contact@thachpham.com
```

Hoặc bạn cũng có thể dùng lệnh git `config --list` để ghi danh sách các thiết lập hiện tại mà bạn đã làm.