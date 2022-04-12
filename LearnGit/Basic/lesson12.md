# Cơ chế xác thực bằng SSH Key

Ngoài cơ chế xác thức bằng cách nhập mật khẩu như trên còn có cơ chế sử dụng SSH Key để xác thực. Để tạo nên xác thực này cần có hai file, một file lưu `Private Key` và môt lưu `Public key`

- **Public Key** khóa chung, là một file text - nó lại lưu ở phía Server SSH, nó dùng để khi Client gửi Private Key  lên để xác thực thì kiểm tra phù hợp giữa Private Key và Public Key này. Nếu phù hợp thì cho kết nối.
    
    
- **Private Key** khóa riêng, là một file text bên trong nó chứa mã riêng để xác thực . Máy khách kết nối với máy chủ phải chỉ ra file này khi kết nối SSH thay vì nhập mật khẩu. Hãy lưu file Private key cận thận, bất kỳ ai có file này có thể thực hiện kết nối đến máy chủ của bạn
    
**1) Tạo SSH Key**

Tìm hiểu chi tiết về SSH, SSH Key thì xem tại [Truy cập Server với SSH](https://xuanthulab.net/su-dung-putty-ket-noi-ssh-den-server-linux-va-windows.html), ở đây coi như máy tính của bạn đã có cài `Open SSH`, hãy chạy tạo một thư mục ví dụ `c:\sshforgithub`, sau đó chạy `cmd` chuyển vào thư mục đó và gọi lệnh sau:

```
cd c:\sshforgithub
ssh-keygen -t rsa -f id_rsa
```

Khi nó hỏi `Enter passphrase` có thể nhấn `Enter` để trống cái này. Kết thúc lệnh đó thì trong `c:\sshforgithub` sẽ có SSH Key cho bạn gồm có public key là file `id_rsa.pub` và private key là file: `id_rsa`

**2) Thiết lập SSH public key cho GitHub**

Mở file `id_rsa.pub` copy toàn bộ nội dung trong file đó vào clipboad, nội dung trong đó có dạng như:

```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDBMTYB/VzdxuVQXY81NUP4aZL4Urk+
tKPN9M12JQLzuTIuQL+eioECGL592xCja+NxsGDRW62rwQqMlJDZvF49EfdaWDT/FyhHfGcuy6laQHHEuv+kIVAPcT7JIRjUD5NMztvlaGvONnD0jMCdDjVmXmkNLJJuQCg
/lhLhSSiR4EhtLyWYfb4gs0Kl5qnVSs1pNCuGOR8St1WzdOoZVJm9QPPQN98NLX0PlZLrOnYsbP+ILUhuC1NmvY8zh8ebtikitoZq1OS5Mboo9d8EYenKAA19+FoBLT
+d1W0ofL0Sm5pAwxE5lva19drGIFZIfmQJ7nbB4SAmQ4kRb4fPJm8j dao xuan thu@DESKTOP-K03L9RD
```

Trở lại tài khoản `GitHub` truy cập vào `Setting`

![https://xuanthulab.net/photo/github-4356.png](https://xuanthulab.net/photo/github-4356.png)

Ở màn hình mới, chọn mục có tên **SSH and GPG key**, sau đó chọn đến mục **new SSH Key**

Tại cửa sổ mới này, điền một tiêu đề SSH ở phần `Title`, còn phần key thì copy và past toàn bộ nội dung file `id_rsa.pub` vào. Cuối cùng bấn `Add SSH Key` để hoàn thành

![https://xuanthulab.net/photo/github-4357.png](https://xuanthulab.net/photo/github-4357.png)

Vậy là hoàn thành bước thiết lập public SSH key cho GitHub, giờ có thể truy cập tới các Repo của bạn bằng kết nối SSH với file private ksy `c:\sshforgithub\id_rsa` và user truy cập là tên user bạn đăng ký, như ví dụ trên là `xuanthulabnet`

**3) Thiết lập private SSH cho SSH/Git tại máy của bạn**

Mở thư mục người dùng, ví dụ user đang logon máy Windows là XuanThuLab, thì thường thư mục đó là `C:\Users\XuanThuLab`, nếu đã cài đúng SSH cho Windows, thì sẽ có thư mục `.ssh` trong đó, mở thư mục đó ra, mở file `config` thêm vào đoạn cấu hình để chị ra host, user, private key khi truy cập SSH với nội dung như sau

```
Host GitHub.com - xuanthulabnet
User git
Hostname github.com
Port 22
PreferredAuthentications publickey
IdentityFile "C:\sshforgithub\id_rsa"
```

Nhớ thay phần màu vàng đúng thông tin của riêng bạn