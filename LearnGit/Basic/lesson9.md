# Lệnh git merge

Lệnh `git merge` sử dụng để gộp nhánh, gộp nhánh này vào nhánh khác. Khi gộp nhánh git thường căn cứ vào 3 commit, để tạo ra một commit gộp, nếu có xung đột cần xử lý 

Giả sử có hai nhánh master và beta như sau:

![https://raw.githubusercontent.com/xuanthulabnet/learn-git/master/docs/git010.png](https://raw.githubusercontent.com/xuanthulabnet/learn-git/master/docs/git010.png)

Để gộp các commit trong nhánh beta vào nhánh master thì chuyển làm việc trên master và thực hiện lệnh:

```jsx
git merge beta
```

Sơ đồ và kết quả của lệnh `git merge` như hình sau:

![https://raw.githubusercontent.com/xuanthulabnet/learn-git/master/docs/git011.png](https://raw.githubusercontent.com/xuanthulabnet/learn-git/master/docs/git011.png)

# Lệnh git rebase

Lệnh `git rebase` cũng gộp các commit từ nhánh này vào nhánh khác, bằng cách xây dựng lại các commit base kế thừa từ nhánh khác và viết lại lịch sử commit sau các commit cơ sở mới.

Ví dụ, để gộp nhánh beta vào master, đứng ở master thực hiện lệnh

```jsx
git rebase beta
```

![https://raw.githubusercontent.com/xuanthulabnet/learn-git/master/docs/git012.png](https://raw.githubusercontent.com/xuanthulabnet/learn-git/master/docs/git012.png)

Như trên hình trên, trước thời điểm rebase, nhánh master có các commit cơ sở giống với nhánh beta đó là: C1, C2, C2

Lệnh `git rebase` sẽ đưa toàn bộ nhánh beta làm base của master, do vậy các commit tiếp theo sau commit cơ sở ban đầu của master sẽ được nối tiếp vào, trong đó có thay đổi lại lịch sử commit, cũng sử lý xung đột giữa commit B2 và D1 để viết lại commit D1 thành D1'

Tương tự, nếu gộp master vào beta thì sơ đồ có thể là:

![https://raw.githubusercontent.com/xuanthulabnet/learn-git/master/docs/git013.png](https://raw.githubusercontent.com/xuanthulabnet/learn-git/master/docs/git013.png)

- Ta sử dụng git **rebase** nếu như muốn các sự thay đổi thuộc về branch của mình luôn luôn là mới nhất. Và có thể log một cách có hệ thống dễ nhìn, dễ tracking sau này.
- Ta sử dụng git **merge** nếu muốn sắp xếp các commit theo mặc định. Nếu không biết về những gì mình làm trên branch đó thì dùng **merge** chắc chắn việc tracking sau này có thể tốn nhiều thời gian lần mò.