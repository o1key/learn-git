# Lesson1: Git và github là gì tại sao nên dùng?

- **Git** tên gọi của một **Hệ thống quản lý phiên bản phân tán (Distributed Version Control System - DVCS):** Một hệ thống phân tán phổ biến hiện nay.
- **DVCS** là hệ thống giúp mỗi máy tính có thể lưu trữ nhiều phiên bản khác nhau của một mã nguồn (**source code**), được nhân bản (**clone**) từ kho chứa mã nguồn (**repository)**, mỗi thay đổi mã nguồn trên máy tính sẽ có thể uỷ thác (**commit**) rồi đưa lên máy chủ, nơi đặt kho chứa chính.
- Mỗi máy tính khác (nếu họ có quyền truy cập) cũng có thể clone lại mã nguồn về hoặc clone 1 tập hợp các thay đổi mới nhất.
- Trong **Git** trên máy tính gọi là **Working Tree.** Mô hình:
    
    ![Mô hình hoạt động của DVCS](https://thachpham.com/wp-content/uploads/2015/04/dvcs.png)
    
    - ⇒ **Git:** Nó giúp bạn lưu các phiên bản của những lần thay đổi mã nguồn và có thể dễ dàng khôi phục mà không cần copy lại mã nguồn. Và một số người khác có thể xem các thay đổi của bạn ở từng phiên bản, họ cũng có thể đối chiếu các thay đổi của bạn rồi gộp phiên bản và phiên bản của họ ⇒ cuối cùng là tất cả có thể đưa các thay đổi vào mã nguồn của mình lên kho chứa mã nguồn.
- Cơ chế lưu trữ phiên bản của **Git** là nó sẽ tạo ra một “*ảnh chụp*” (***snapshot***) trên mỗi tập tin và thư mục sau khi commit, từ đó nó có thể cho phép bạn tái sử dụng lại một ảnh chụp nào đó mà bạn có thể hiểu đó là một phiên bản

# Github

- **Git** là tên gọi của một mô hình hệ thống. Các máy tính có thể clone lại mã nguồn từ một repository
- **Github:** chính là một dịch vụ máy chủ repository công cộng.

# Tại sao nên sử dụng Git?

- Git dễ sử dụng, an toàn và nhanh chóng.
- Có thể giúp quy trình làm việc code theo nhóm đơn giản hơn rất nhiều bằng việc kết hợp các phân nhánh (branch).
- Bạn có thể làm việc ở bất cứ đâu vì chỉ cần clone mã nguồn từ kho chứa hoặc clone một phiên bản thay đổi nào đó từ kho chứa, hoặc một nhánh nào đó từ kho chứa.
- Dễ dàng trong việc deployment sản phẩm.
- Và nhiều hơn thế nữa.