# **Git cherry-pick**

Là một cách để checkout 1 commit bất kỳ tại 1 branch được chỉ định về brach hiện tại. Hay chính là git cherry-pick sẽ bốc thay đổi của 1 commit trên 1 nhánh nào đó áp dụng vào nhánh hiện tại.

Cùng xem thao tác cụ thể nào:

## **Lấy 1 commit từ 1 brach bỏ vào master**

```tsx
git checkout master

git cherry-pick feature-A~1

# Hoặc chúng ta có thể chỉ định hash commit
git cherry-pick C2
```

Quá đơn giản nhỉ, trên đó, nghĩa là ta đã đưa thay đổi của commit C2 thuộc branch feature-A vào branch master

## **Lấy n commits từ 1 brach bỏ vào master**

Giả sử, bây giờ mình cần đưa n commits (giả sử ở đây là 2 commits) thì mình làm như sau:

```tsx
# Nếu muốn thêm 1 vài commit, không liên tục
git cherry-pick commit_id1 commit_id3

# Nếu muốn thêm 1 loạt commit lần lượt cạnh nhau
git cherry-pick commit_id1...commit_id5

# Với code trên, thì  commit_id1 sẽ ko được thêm vào
# Để đưa commit được tính vào trong branch muốn thêm thì 
git cherry-pick commit_id1^..commit_id5
```

## **1 lần commit cho cả 2 branches**

Commit A cần apply cho 2 branch là branch-X và branch-Y

```tsx
# Đang ở branch-X, thực hiện commit để tạo ra commit A
git add -A
git commit -m " finish commit A"

# Checkout sang branch Y và dùng cherry-pick nào
git checkout branch-Y
git cherry-pick branch-X
```

Với lệnh này, cherry-pick sẽ lấy commit cuối cùng ở branch branch-X và merge vào branch branch-Y

### **Fix conflict**

Cũng như **git merge hay rebase, git cherry-pick** cũng xãy ra conflict nếu xung đột code. việc của chúng ta chỉ đơn giản là fix conflict sau đó dùng:
***
# **git revert**

git reset không tạo mới commit, trong khi đó git revert sẽ “undo” lại tất cả những thay đổi của một commit mà chúng ta chỉ định và tạo mới một commit mới trên history.

![https://thaunguyen.com/blog/wp-content/uploads/2021/07/image-8-1024x284.png](https://thaunguyen.com/blog/wp-content/uploads/2021/07/image-8-1024x284.png)

Lệnh **git revert C2** sẽ tạo ra một commit mới C4 và bỏ (undo) lại tất cả thay đổi của commit C2.