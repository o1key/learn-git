# **Lưu lại thay đổi**

`Git stash` được sử dụng khi muốn lưu lại các thay đổi **chưa commit**, thường rất hữu dụng khi bạn muốn đổi sang 1 branch khác mà lại đang làm dở ở branch hiện tại.

Muốn lưu toàn bộ nội dung công việc đang làm dở, bạn có thể sử dụng `git stash` như sau

```jsx
$ git stash save# or just "git stash"
```

Khi này branch đã trở nên "sạch sẽ" và `git status` sẽ cho thấy bạn có thể chuyển sang branch tuỳ thích. Bạn có thể `git stash` **bao nhiêu lần tuỳ thích** và mỗi lần đó git sẽ lưu toàn bộ lần thay đổi đó như 1 phần tử trong 1 stack.

# **Lấy lại thay đổi**

Sau khi đã git stash 1 hoặc vài lần, bạn có thể xem lại danh sách các lần lưu thay đổi bằng câu lệnh

```jsx
$ git stash list
stash@{0}: WIP on <branch-name>: <lastest commit>
stash@{1}: WIP on <branch-name>: <lastest commit>
stash@{2}: WIP on <branch-name>: <lastest commit>
```

Nếu muốn xem cả nội dung của từng thay đổi thì thêm option `-p`

```jsx
$ git stash list -p
```

hoặc xem nội dung cụ thể hơn nữa của lần thay đổi thứ 1:

```jsx
$ git stash show stash@{1}
```

Khi muốn apply lại thay đổi từ stash lần 1 bạn có thể

```jsx
$ git stash apply stash@{1}
```

# **Xoá các thay đổi không cần thiết**

Đôi khi bạn muốn lấy lại thay đổi và xoá nội dung thay đổi lưu trong stack đi, khi đó bạn có thể

```jsx
$ git stash apply stash@{1}
$ git stash drop stash@{1}
```

hoặc đơn giản hơn là

```jsx
$ git stash pop stash@{1}
```

Thậm chí nếu muốn xoá *toàn bộ stack* thì có thể dùng `clear`

```jsx
$ git stash clear
```