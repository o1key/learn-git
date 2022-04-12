Github là một máy chủ repository từ xa nên mình sẽ gọi nó là Remote Repository, nghĩa là repository này không nằm trên máy tính của bạn.bạn có thấy mình kêu các bạn gửi dữ liệu lên repository bằng cách dùng lệnh `git push origin master` sau khi commit không? Cái `master` là tên ranch, nhưng cái `origin` trong đoạn đó chính là **tên remote repository**. Mặc định khi clone một repository thì nó tự đặt tên là `origin`

Để kiểm tra tên remote, bạn có thể gõ lệnh `git remote -v`.

```tsx
$ git remote -v
origin https://github.com/thachphamblog/hoc-git.git (fetch)
origin https://github.com/thachphamblog/hoc-git.git (push)
```

Trong đó bạn có thể thấy cái repository mình đã clone đều được đặt tên là `origin`, và mỗi repository bạn có hai đều có hai hành động là fetch (lấy dữ liệu về từ server) và push (gửi dữ liệu lên server).

Nhìn lại đoạn lệnh `git push origin master` ở trên, điều đó có nghĩa là bạn gửi tất cả các thay đổi trên mã nguồn ở máy bạn lên remote tên là `origin` với branch `master`.

# **Đổi tên remote**

Nếu bạn không thích tên `origin` thì có thể đổi tên nó lại nó bằng tên khác cho dễ quản lý nếu như bạn có nhiều remote trong một dự án với lệnh `git remote rename tên_cũ tên_mới`. Ví dụ mình cần đổi từ `origin` sang `thach` thì sẽ đổi như sau:

```tsx
$ git remote rename origin thach
$ git remote -v
thach https://github.com/thachphamblog/hoc-git.git (fetch)
thach https://github.com/thachphamblog/hoc-git.git (push)
```

Bây giờ khi commit hay push bạn có thể gõ `git push thach master` để gửi mã nguồn lên remote repository này.

# **Thêm một remote**

Trường hợp bạn cần thêm một cái remote để lấy dữ liệu khi cần thì có thể sử dụng lệnh `git remote add tên_remote URL`

```tsx
$ git remote add unuit https://github.com/thachpham92/inuit.css-web-template
$ git remote -v
thach https://github.com/thachphamblog/hoc-git (fetch)
thach https://github.com/thachphamblog/hoc-git (push)
inuit https://github.com/thachpham92/inuit.css-web-template (fetch)
inuit https://github.com/thachpham92/inuit.css-web-template (push)
```

# **Sự khác nhau giữa`clone`, `fetch` và `pull`**

Nhưng cả ba loại đều là lấy dữ liệu, thế sự khác nhau của nó là gì?

## git clone

Lệnh này sẽ sao chép toàn bộ dữ liệu trên repository và sao chép luôn các thiết lập về repository, tức là nó sẽ tự động tạo một master branch trên máy tính của bạn. Lệnh này chỉ nên sử dụng khi bạn cần tạo mới một Git mới trên máy tính với toàn bộ dữ liệu và thiết lập của một remote repository.

## **git fetch**

Lệnh `git fetch` tải về dữ liệu từ Remote Repo (các dữ liệu như các commit, các file, refs), dữ liệu tải về để bạn theo dõi sự thay đổi của remote, tuy nhiên tải về bằng `git fetch` nó chưa tích hợp thay đổi ngay local repository của bạn, mục đích để theo dõi các commit người khác đã cập nhật lên server, để có được thông thông tin khác nhau giữa remote và local

Tải về thông tin của tất cả các nhánh của remote có tên origin

```tsx
git fetch origin
```

Hoặc

```tsx
git fetch --all
```

Tải thông tin của một nhánh, ví dụ master của remote origin

```tsx
git fetch origin master
```

Sau khi tải về, để có thể khám phá sự khác biệt giữa local và remote bạn có thể xem trạng thái của thư mục làm việc, xem log của một nhánh local và log của nhánh remote

Ví dụ xem log nhánh master của remote origin

```tsx
git log --oneline origin/master
```

Sau khi kiểm tra sự khác biệt của nhánh giữa remote và local, bản có thể thay đổi cập nhật vào local repo dữ liệu tải về bằng lệnh git pull hoặc git merge, ví dụ gộp thay đổi của remote/master và master bằng merge thì thi hành

```tsx
git merge origin/master
```

## git pull

Lệnh này sẽ tự động lấy toàn bộ dữ liệu từ remote repository và gộp vào cái branch hiện tại bạn đang làm việc.