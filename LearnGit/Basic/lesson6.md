Nếu bạn commit quá nhiều thì sẽ gây khó khăn cho bạn về sau nếu cần xem lại thông tin của lần commit trước mà bạn có thể gắn thẻ đánh dấu (tag) cho mỗi commit và khi cần xem bạn chỉ cần sử dụng lệnh `git show tên_tag` là đã có thông tin rất rõ ràng,

Ngoài ra nó còn giúp bạn dễ dàng diff (đối chiếu) sau này khi không cần nhớ checksum (dù chỉ cần nhớ vài ký tự đầu tiên) của mỗi commit mà chỉ cần nhớ tag, cũng như có thể tạo thêm branch từ tag để bạn thuận tiện hơn trong việc phân nhánh.

Trong Git có hai kiểu tag chính đó là:

- **Lightweight Tag**: Các tag này chỉ đơn thuần là đánh dấu snapshot của commit.
- **Annotated Tag**: Với tag này, bạn có thể đặt tiêu đề cho tag, và khi xem nó sẽ có thông tin về người tag, ngày tag,….

# Lightweight Tag

Gõ `git tag` để xem danh sách các tag có trong dự án của bạn. Sau đó để tạo thêm một tag, bạn có thể gõ `git tag tên_tag` để tạo. Ví dụ như `v1.0` chẳng hạn.

```tsx
$ git tag v1.0
$ git tag
v1.0
```

Bây giờ bạn có thể xem thông tin của lần commit được gắn tag này bằng lệnh `git show tên_tag`. Lưu ý rằng lệnh trên nó sẽ đánh dấu lần commit cuối cùng của bạn vào tag `v1.0`.

```tsx
$ git show v1.0
commit 05193375f7a7c1295fd26c6388d81e188f405b0b
Author: Thach Pham <contact@thachpham.com>
Date: Thu Apr 23 02:20:50 2015 -0700

 Added a new tag

diff --git a/tag.html b/tag.html
new file mode 100644
index 0000000..e69de29
```

# Annotated Tag

Để tạo Annotated Tag thì bạn cũng sử dụng lệnh git tag nhưng sẽ có thêm tham số `-a` và tham số `-m` để thiết lập lời nhắn cho tag này.

```
$ git tag -a v1.0-an -m "Ra mat phien ban 1.0"
$ git show v1.0-an
tag v1.0-an
Tagger: Thach Pham <contact@thachpham.com>
Date: Thu Apr 23 02:41:11 2015 -0700

Ra mat phien ban 1.0

commit d5a599e3385a8fc7a65958ed50bc8b54666b45ad
Author: Thach Pham <contact@thachpham.com>
Date: Thu Apr 23 02:40:31 2015 -0700

 Commit for Annotated Tag

diff --git a/tag.html b/tag.html
index e69de29..fea03c1 100644
--- a/tag.html
+++ b/tag.html
@@ -0,0 +1 @@
+Annotated Tag
```

Bạn có thể thấy khi show ra, cái Annotated tag sẽ có nhiều thông tin hơn là so với cái tag thông thường, và đây cũng là kiểu tag bạn nên sử dụng để có nhiều thông tin hơn.

# Thêm tag cho các commit cũ

Để xem mã checksum của các lần commit trước đó thì bạn có thể sử dụng git log với tham số `--pretty` với giá trị `oneline` để lọc log nhé.

```tsx
$ git log --pretty=oneline
d5a599e3385a8fc7a65958ed50bc8b54666b45ad Commit for Annotated Tag
05193375f7a7c1295fd26c6388d81e188f405b0b Added a new tag
435f642f951fbab1037fc2feef239ab26d6e6115 Added faq.html
6904d5232bf90821068279311e205e3e1ff929f1 Initial commit
```

# Push Tag

Mặc định lệnh `git push` sẽ không push các tag đã tạo lên repository mà bạn có thể dùng lệnh `git push --tags` để đẩy toàn bộ tag lên repository.

```tsx
$ git push --tags
Username for 'https://github.com': thachphamblog
Password for 'https://thachphamblog@github.com':
Counting objects: 7, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (6/6), done.
Writing objects: 100% (7/7), 775 bytes | 0 bytes/s, done.
Total 7 (delta 1), reused 0 (delta 0)
To https://github.com/thachphamblog/hoc-git.git
 * [new tag] v0.0 -> v0.0
 * [new tag] v1.0 -> v1.0
 * [new tag] v1.0-an -> v1.0-an
```

## **Nhập tag vào branch**

Với lệnh `git checkout -b tên_branch tên_tag`

```tsx
$ git checkout -b version1 v1.0-an
Switched to a new branch 'version1'
```

Lúc này bạn đã tự động chuyển qua branch `version1` thay vì `master` ban đầu, kèm theo đó là dữ liệu của lần commit được gắn tag `v1.0-an`.