**Monorepo** là một kho lưu trữ duy nhất chứa các ứng dụng, công cụ và cấu hình của nhiều dự án hoặc thành phần dự án. Đó là một giải pháp thay thế cho việc tạo các kho lưu trữ riêng biệt cho từng dự án hoặc một phần của dự án.

Hãy xem xét một tình huống trong đó chúng ta đang phát triển một ứng dụng trang tổng quan bằng cách sử dụng một số thư viện hoặc framework front-end. Phần code cho ứng dụng front-end này có thể được lưu trữ trong kho lưu trữ `dashboard`. Các thành phần giao diện người dùng mà kho lưu trữ này sử dụng có thể được lưu trữ trong một kho lưu trữ khác có tên là `components`. Giờ đây, mỗi khi chúng ta cập nhật kho lưu trữ `components`, chúng ta phải truy cập vào kho lưu trữ `dashboard` và cập nhật phần phụ thuộc (dependency) của `components`.

![https://uploads.sitepoint.com/wp-content/uploads/2021/07/1626026159separated.png](https://uploads.sitepoint.com/wp-content/uploads/2021/07/1626026159separated.png)

Để phần nào giải quyết nan đề này, chúng ta có thể hợp nhất repo `components` với repo `dashboard`.

![https://uploads.sitepoint.com/wp-content/uploads/2021/07/1626026158mono-repo-single.png](https://uploads.sitepoint.com/wp-content/uploads/2021/07/1626026158mono-repo-single.png)

Tuy nhiên, có thể có một ứng dụng front-end khác cho trang web tiếp thị được lưu trữ trong kho lưu trữ `marketing` và ứng dụng này phụ thuộc vào kho lưu trữ `components`. Vì vậy, chúng ta sẽ phải sao chép `components` và hợp nhất nó với `marketing`. Tuy nhiên, từ đó, bất kỳ thay đổi nào liên quan đến `components` sẽ phải được thực hiện ở hai nơi, vô cùng bất tiện.

![https://uploads.sitepoint.com/wp-content/uploads/2021/07/1626026155double-mono-repo.png](https://uploads.sitepoint.com/wp-content/uploads/2021/07/1626026155double-mono-repo.png)

Vấn đề trên có thể được giải quyết bằng cách sử dụng monorepo, trong đó các thành phần `dashboard`, `components` và `marketing` nằm trong một kho lưu trữ duy nhất.

![https://uploads.sitepoint.com/wp-content/uploads/2021/07/1626026156mono-repo-all.png](https://uploads.sitepoint.com/wp-content/uploads/2021/07/1626026156mono-repo-all.png)

Có nhiều lợi ích khác nhau khi sử dụng monorepo:

- Việc cập nhật các gói dễ dàng hơn nhiều, vì tất cả các ứng dụng và thư viện đều nằm trong một kho lưu trữ duy nhất. Vì tất cả các ứng dụng và gói đều nằm trong cùng một kho, nên việc thêm mã mới hoặc sửa đổi mã hiện có có thể được kiểm tra và vận chuyển rất dễ dàng.
- Việc khôi phục lại mã dễ dàng hơn nhiều, vì chúng ta sẽ thực hiện điều đó chỉ ở một nơi duy nhất thay vì sao chép cùng một nội dung trên nhiều kho lưu trữ.
- Một monorepo cho phép cấu hình nhất quán cho các CI/CD pipeline, có thể được sử dụng lại bởi tất cả các ứng dụng và thư viện hiện có trong cùng một kho lưu trữ.
- Việc xuất bản các gói cũng trở nên dễ dàng hơn nhiều do các công cụ như Nx.