Một việc bạn sẽ khá thường xuyên làm trong Git nếu làm việc theo nhóm đó là kiểm tra xem những ai đã commit vào dự án bạn đang làm việc, cũng như cách bạn undo lần commit trước đó nếu như bạn cảm thấy mình thiếu một tập tin nào đó trong lần commit trước để bổ sung vào.

# **Xem git log**

Để xem lịch sử của các lần commit trước đó, bạn sử dụng lệnh `git log` là sẽ thấy.

```tsx
$ git log
commit 3f1ef84ada3dfd936735d8724f9bbb3437c77b19
Author: Thach Pham <contact@thachpham.com>
Date: Tue Apr 21 17:16:37 2015 -0700

 Hihi

commit 6e729a49a36b31919daa6263f8f98f3a59d5bab3
Author: Thach Pham <contact@thachpham.com>
Date: Tue Apr 21 14:47:47 2015 -0700

 First commit on Github
```

Ngoài ra, bạn có thể chèn thêm tham số `-p` vào để hiển thị chi tiết của mỗi lần commit.

```tsx
$ git log -p
commit 3f1ef84ada3dfd936735d8724f9bbb3437c77b19
Author: Thach Pham <contact@thachpham.com>
Date: Tue Apr 21 17:16:37 2015 -0700

 Hihi

diff --git a/README.md b/README.md
index db7e814..e08f24f 100644
--- a/README.md
+++ b/README.md
@@ -1 +1 @@
-# Huong dan Git co ban
+hhih\n
diff --git a/faq.html b/faq.html
new file mode 100644
index 0000000..e69de29

commit 6e729a49a36b31919daa6263f8f98f3a59d5bab3
Author: Thach Pham <contact@thachpham.com>
Date: Tue Apr 21 14:47:47 2015 -0700

 First commit on Github

diff --git a/README.md b/README.md
new file mode 100644
index 0000000..db7e814
--- /dev/null
+++ b/README.md
@@ -0,0 +1 @@
+# Huong dan Git co ban
```

Hoặc nếu bạn muốn chỉ muốn xem 1 lần commit gần nhất thì thêm tham số `-1` vào.

Bạn còn có thể sử dụng thêm một số tùy chọn xem log sau để tối ưu hơn quy trình đọc log.

- `-since`, `-after`: Xem các lần commit kể từ ngày nhất định.
- `-until`: Xem các lần commit trước từ ngày nhất định.
- `-author`: Xem các lần commit của một người nào đó.
- `-grep`: Lọc các chuỗi trong log và in ra.

## **Lọc log với `--pretty`**

Tham số `--pretty` rất có ích nếu bạn muốn lọc xem một đối tượng nào đó trong lịch sử commit, ví dụ như chỉ xem lời nhắn commit hoặc chỉ xem email của người commit.

Cách sử dụng tham số `--pretty` là bạn phải viết kèm các tag của nó như sau:

```tsx
$ git log --pretty="%tag"
```

Các `%tag` phải dược đặt trong cặp dấu ngoặc kép và bạn có thể sử dụng nhiều `%tag` khác nhau.

Danh sách các `%tag`:

- `%H` – Commit hash
- `%h` – Abbreviated commit hash
- `%T` – Tree hash
- `%t` – Abbreviated tree hash
- `%P` – Parent hashes
- `%p` – Abbreviated parent hashes
- `%an` – Author name
- `%ae` – Author e-mail
- `%ad` – Author date (format respects the –date=option)
- `%ar` – Author date, relative
- `%cn` – Committer name
- `%ce` – Committer email
- `%cd` – Committer date
- `%cr` – Committer date, relative
- `%s` – Subject

Ví dụ:

```tsx
$ git log --pretty="%an - %s"
Thach Pham - Hihi
Thach Pham - First commit on Github
```

# Undo Commit

Nếu bạn cần xóa bỏ lần commit trước và cần undo để commit lại thì có thể sử dụng tham số `--amend` trong lệnh `git commit`.

```tsx
$ git log --pretty="%s"
Hihi
First commit on Github
$ git commit --amend -m "Hehe"
[master 3682e56] Hehe
 Date: Tue Apr 21 17:16:37 2015 -0700
 2 files changed, 1 insertion(+), 1 deletion(-)
 create mode 100644 faq.html
$ git log --pretty="%s"
Hehe
First commit on Github
```

Lưu ý rằng undo nghĩa là bạn quay trở lại bước commit lần trước, do vậy nếu cần bổ sung tập tin nào vào để commit thì hãy đưa tập tin đó vào Staging Area trước.

### Bỏ tập tin ra khỏi Staging Area

Nếu bạn đã đưa một tập tin nào đó vào Staging Area nhưng bây giờ bạn muốn loại bỏ nó ra khỏi đây để không phải bị commit theo thì có thể sử dụng lệnh `git reset HEAD tên_file`.