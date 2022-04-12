Trong khi làm việc với **Git**, bạn đã quá quen thuộc với việc chỉnh sửa mã nguồn, sau đó là **commit** mỗi khi chỉnh sửa xong và **push** lên **remote repository** nếu cần thiết. Nhưng bây giờ mình có một ví dụ đặt ra là mình muốn **tạo một phiên bản thử nghiệm với mã nguồn đang làm việc trong working tree hiện tại mà không gây ảnh hưởng đến các code hiện tại**
. Vậy thì làm cách nào? Không lẽ clone một repository từ chính cái working tree hiện tại rồi sửa đổi hay sao? Như thế rất là mất công, mà lại không tối ưu và không thể đồng bộ hóa hoặc rất khó khăn để đồng bộ hóa.**.**

# **Branch trong Git là gì?**

Branch là cái dùng để phân nhánh và ghi lại luồng của lịch sử. Branch đã phân nhánh sẽ không ảnh hưởng đến branch khác nên có thể tiến hành nhiều thay đổi đồng thời trong cùng 1 repository.

### Cách tạo một branch

Trước tiên bạn có thể xem toàn bộ các branch mà bạn đang có trong working tree bằng lệnh `git branch`. Sau đó nếu muốn tạo thêm branch, chỉ cần gõ lệnh `git branch tên_brand`. Ví dụ mình cần tạo branch`develop`.

```tsx
$ git branch develop
```

Bây giờ bạn có thể gõ lại lệnh `git branch` một lần nữa để xem sẽ thấy brand tên develop xuất hiện.

Bây giờ bạn sẽ làm việc trong branch mới chuyển

Bây giờ bạn thử tạo một tập tin nào đó, sau đó commit ở branch `develop` rồi chuyển về branch master sẽ thấy những gì bạn đã làm ở branch `develop` hoàn toàn vô nghĩa ở`master`. Dưới đây là ví dụ về việc ở branch `master` không có tập tin develop.html được tạo ra từ branch `develop`.

```tsx
$ touch develop.html
$ git add .
$ git commit -m "Commit develop.html from develop branch"
[develop 8c68896] Commit develop.html from develop branch
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 develop.html
$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'thach/master' by 3 commits.
 (use "git push" to publish your local commits)
$ ls
faq.html README.md tag.html version1.txt
```

Tương tự với việc sửa tập tin hay bất kỳ làm việc gì khác nó cũng chỉ áp dụng thay đổi ở branch bạn đang trỏ tới.

# **Gộp dữ liệu từ một branch**

Nếu mỗi branch nó nằm riêng như vậy thì bạn muốn sử dụng các thay đổi ở một branch nào đó cho master thì sao? À, chúng ta có thể sử dụng lệnh git merge để chuyển dữ liệu từ một branch nào đó về branch mà bạn đang trỏ đến. Lưu ý là ở branch cần chuyển về đã phải được commit. Ví dụ mình cần chuyển dữ liệu từ branch develop về master thì sẽ làm lần lượt các lệnh sau:

```tsx
$git checkout master
Already on 'master'
Your branch is ahead of 'thach/master' by 3 commits.
 (use "git push" to publish your local commits)
$git merge develop
Updating 83e9976..8c68896
Fast-forward
 develop.html | 0
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 develop.html
$ls
develop.html faq.html README.md tag.html version1.txt
```

# **Xóa branch**

```tsx
$ git branch -d develop
Deleted branch develop (was 8c68896).
```

Trường hợp có commit chưa được merge vào HEAD thì không thể xóa branch. Để xóa branch có commit chưa được merge cách cưỡng chế thì thêm lựa chọn -D vào rồi thực thi.