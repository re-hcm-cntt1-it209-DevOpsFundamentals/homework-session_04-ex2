Bài 2: Quản lý nhánh và Giải quyết xung đột
1. Mục tiêu
Tạo và chuyển đổi giữa các branch.
Làm việc trên hai branch main và feature-update.
Tạo merge conflict khi hai branch cùng chỉnh sửa một dòng trong README.md.
Tự xử lý conflict bằng cách chỉnh sửa các conflict marker.
Tạo merge commit sau khi giải quyết conflict.
Kiểm tra lịch sử commit bằng git log --graph --oneline.
2. Khởi tạo Repository

Khởi tạo Git repository:

git init

Cấu hình thông tin Git cho repository hiện tại:

git config --local user.name "Nguyen Dai Phat"
git config --local user.email "n24dtcn062@student.ptithcm.edu.vn"

Kiểm tra cấu hình:

git config --local --list
3. Tạo commit ban đầu

Tạo file README.md:

# Feature Update

Version: Original

Đưa file vào staging:

git add README.md

Tạo commit đầu tiên:

git commit -m "Initial commit"

Đổi tên branch mặc định thành main:

git branch -M main
4. Tạo branch Feature

Tạo và chuyển sang branch feature-update:

git switch -c feature-update

Trên branch feature-update, thay đổi nội dung README thành:

# Feature Update

Version: Feature branch

Commit thay đổi:

git add README.md
git commit -m "Update README on feature branch"
5. Cập nhật branch main

Chuyển lại branch main:

git switch main

Trên branch main, thay đổi cùng dòng trong README.md thành:

# Feature Update

Version: Main branch

Commit thay đổi:

git add README.md
git commit -m "Update README on main branch"
6. Tạo Merge Conflict

Thực hiện merge branch feature-update vào main:

git merge feature-update

Git phát hiện hai branch đã chỉnh sửa cùng một dòng theo hai nội dung khác nhau nên xảy ra conflict:

CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.

Git đánh dấu vùng conflict trong README.md:

<<<<<<< HEAD
Version: Main branch
=======
Version: Feature branch
>>>>>>> feature-update

Ý nghĩa:

<<<<<<< HEAD: bắt đầu phần nội dung hiện tại của branch main.
=======: phân cách hai phần nội dung xung đột.
>>>>>>> feature-update: kết thúc phần nội dung đến từ branch feature-update.
7. Giải quyết Conflict

Conflict được giải quyết thủ công bằng cách xóa các conflict marker và giữ lại nội dung mong muốn.

Kết quả cuối cùng:

# Feature Update

Version: Main + Feature Update

Sau khi chỉnh sửa, đưa file vào staging:

git add README.md

Tạo merge commit:

git commit -m "Merge feature-update into main"
8. Kiểm tra lịch sử Git

Kiểm tra lịch sử commit dạng đồ thị:

git log --graph --oneline

Kết quả cho thấy hai branch đã phát triển riêng từ commit ban đầu và sau đó được hợp nhất bằng một merge commit:

*   e87aaf1 (HEAD -> main) Merge feature-update into main
|\
| * b695494 (feature-update) Update README on feature branch
* | 9703f5a Update README on main branch
|/
* 9291e97 Initial commit
Giải thích

9291e97 là commit ban đầu. Từ đây lịch sử được tách thành hai nhánh:

main tạo commit 9703f5a.
feature-update tạo commit b695494.

Sau khi giải quyết conflict, Git tạo merge commit e87aaf1.

Merge commit có hai parent, thể hiện việc hợp nhất lịch sử của hai branch.

9. Hình ảnh minh chứng
Git Graph ( để file images)

10. Kết quả

Đã hoàn thành:

 Khởi tạo Git repository.
 Tạo và chuyển đổi branch.
 Cập nhật main.
 Cập nhật feature-update.
 Tạo merge conflict.
 Giải quyết conflict thủ công.
 Tạo merge commit.
 Kiểm tra lịch sử bằng git log --graph --oneline.