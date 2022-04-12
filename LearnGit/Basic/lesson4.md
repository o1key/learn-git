# **Staging Area là gì?**

**Staging Area** là một khu vực mà nó sẽ được chuẩn bị cho quá trình commit,khu vực sẽ lưu trữ những thay đổi của bạn trên tập tin để nó có thể được commit, vì muốn commit tập tin nào thì tập tin đó phải nằm trong Staging Area. Một tập tin khi nằm trong Staging Area sẽ có trạng thái là **Stagged** 
Và để đưa một tập tin vào Staging Area thì bạn sẽ cần phải sử dụng lệnh `git add tên_file`

![Untitled](https://res.cloudinary.com/practicaldev/image/fetch/s--D7nJOADN--/c_imagga_scale,f_auto,fl_progressive,h_900,q_auto,w_1600/https://cl.ly/569e7f0bbfaf/download/Image%25202018-08-29%2520at%25208.26.35%2520PM.png)

# **Commit là gì và nó hoạt động ra sao?**

Hiểu đơn giản hơn, commit nghĩa là một hành động để Git lưu lại một bản chụp (snapshot) của các sự thay đổi trong thư mục làm việc, và các tập tin và thư mục được thay đổi đã phải nằm trong Staging Area

Mỗi lần commit nó sẽ được lưu lại lịch sử chỉnh sửa của mã nguồn kèm theo tên và địa chỉ email của người commit.

Ngoài ra trong Git bạn cũng có thể khôi phục lại tập tin trong lịch sử commit của nó để chia cho một phân nhánh (branch) khác

Và tất nhiên, lệnh commit trong Git sẽ là `git commit -m "Lời nhắn"`

Và nếu bạn **muốn đưa tập tin lên repository thì bạn phải commit nó trước** rồi sau đó lệnh `git push origin master` sẽ có nhiệm vụ đưa toàn bộ các tập tin đã được commit lên repository.

## **Điều kiện gì để commit một tập tin?**

Nếu bạn muốn commit một tập tin đó, bạn sẽ cần phải đưa tập tin đó vào trạng thái tracked bằng lệnh `git add tên_file`.Trong git có hai loại trạng thái chính đó là 

![Untitled](https://giangmd.net/wp-content/uploads/2020/06/git-tutorial-7-638.jpg)

- **Tracked** – Là tập tin đã được đánh dấu theo dõi trong Git để bạn làm việc với nó. Và trạng thái Tracked nó sẽ có thêm các trạng thái phụ khác là Unmodified (chưa chỉnh sửa gì), Modified (đã chỉnh sửa) và Staged (đã sẵn sàng để commit).
- **Untracked** – Là tập tin còn lại mà bạn sẽ không muốn làm việc với nó trong Git.

## **Bỏ qua Staging Are để commit**

Như mình có nói ở trên là một tập tin sau khi được thay đổi hay tạo mới thì nó phải được thêm vào Staging Area với lệnh git add. Tuy nhiên, bạn có thể đưa một tập tin đã được Tracked để commit mà không cần đưa nó vào Staging Area với tham số `-a`  trong lệnh `git commit`
. Ví dụ: `git commit -a -m "Skipped Staging Are to commit"`

## **Untracked**

Nếu bạn tạo ra hoặc thêm vào một tập tin mới vào trong thư mục làm việc của bạn thì nó sẽ ở trạng thái Untracked. Bây giờ mình thử tạo ra một tập tin mới tên là *faq.html*, sau đó dùng lệnh `git status` để xem trạng thái của Git trong thư mục làm việc.

```tsx
$ touch faq.html
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Untracked files:
 (use "git add <file>..." to include in what will be committed)

 faq.html

nothing added to commit but untracked files present (use "git add" to track)
```

Bây giờ bạn sẽ thấy nó đã liệt kê ra tên tập tin đang ở trạng thái Untracked. Để đưa nó về Tracked bạn sẽ sử dụng lệnh `git add`
 và xem lại trạng thái của nó.

```tsx
$ git add faq.html
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
 (use "git reset HEAD <file>..." to unstage)

 new file: faq.html
```

### Tracked

Một khi một tập tin đã được đưa về Tracked thì nó sẽ có thể thay đổi giữa 3 trạng thái khác nhau là 

- **Modified**
- **Unmodified**
- **Staged**.

## **Chuyển tập tin từ Untracked về Tracked**

Trong Git, bạn có thể đưa một tập tin từ Tracked về Untracked với lệnh rm tên_file. Lệnh rm sẽ giúp bạn đưa tập tin về trạng thái Untracked nhưng không xóa hẳn trong ổ cứng.

```tsx
$ rm faq.html
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
```

```tsx
Changes not staged for commit:
 (use "git add/rm <file>..." to update what will be committed)
 (use "git checkout -- <file>..." to discard changes in working directory)
```

```tsx
deleted: faq.html
```

Còn nếu bạn muốn xóa nó luôn thì dùng lệnh `git rm -f tên_file` và ***nhớ cẩn thận*** khi dùng lệnh này.