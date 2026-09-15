# Báo cáo thực hành Git - Bài 1 đến Bài 6

## Bài 1: Khởi tạo Repository và commit đầu tiên
Đã thực hiện: git init, tạo 3 file, git add index.html style.css (không thêm notes.txt), commit "Initial commit: add html and css".

![status truoc](screenshots/bai1-status-truoc.png)
![status sau](screenshots/bai1-status-sau.png)
![log](screenshots/bai1-log.png)

**Câu hỏi tư duy:** Staging area (Index) là nơi trung gian giữa Working Directory và Repository, cho phép chọn lọc chính xác những thay đổi nào sẽ được đưa vào commit. Nếu không có nó, mỗi lần commit sẽ bắt buộc phải đưa toàn bộ thay đổi trong working directory vào, không thể tách riêng các nhóm thay đổi liên quan để commit độc lập, rất bất tiện khi muốn commit từng phần nhỏ, rõ ràng.

## Bài 2: Commit nhiều lần và xem lịch sử
Đã thực hiện: sửa index.html, tạo script.js, sửa style.css + notes.txt, commit 3 lần liên tiếp.

![log oneline](screenshots/bai2-log-oneline.png)
![show head](screenshots/bai2-show-head.png)

## Bài 3: Di chuyển giữa các phiên bản (checkout/reset)
Đã checkout về commit cũ (detached HEAD) rồi quay lại main. Thử nghiệm 3 kiểu reset.

| Kiểu reset | HEAD | Staging Area | Working Directory |
|---|---|---|---|
| --soft | Lùi về commit trước | Giữ nguyên (vẫn staged) | Giữ nguyên |
| --mixed | Lùi về commit trước | Bị reset (unstaged) | Giữ nguyên (thành untracked) |
| --hard | Lùi về commit trước | Bị reset | Bị reset với file đã tracked; file untracked không bị đụng tới |

**Nhận xét quan trọng:** `git reset --hard` không xoá các file đang ở trạng thái untracked, chỉ ảnh hưởng tới các file đã được tracked bởi Git.

**Câu hỏi tư duy:** Nếu đã push code lên GitHub cho cả team dùng, dùng `git reset --hard` để lùi lại commit là **không an toàn**, vì nó chỉ thay đổi lịch sử trên máy local; nếu push --force sau đó sẽ làm mất các commit mà đồng đội đang dựa vào, gây xung đột. Cách an toàn hơn là dùng `git revert` để tạo commit mới đảo ngược thay đổi.

## Bài 4: Tạo project mới trên GitHub và kết nối remote
Link repository: https://github.com/youngdragon26/git-basic-practice

![remote -v](screenshots/bai4-remote-v.png)

## Bài 5: Đồng bộ remote repository (clone/pull/push)
Đã clone một repo mẫu công khai, tạo about.txt và push, sau đó giả lập sửa trực tiếp trên GitHub (thêm README.md), rồi pull về local.

![truoc pull](screenshots/bai5-truoc-pull.png)
![sau pull](screenshots/bai5-sau-pull.png)

**Câu hỏi tư duy:** `git pull` thực chất là tổ hợp của `git fetch` (tải commit mới từ remote về) và `git merge` (gộp các commit đó vào nhánh hiện tại).

## Bài 6: Mô phỏng quy trình làm việc hoàn chỉnh
Đã thêm phần giới thiệu bản thân vào index.html, style hoá bằng CSS, cố tình commit sai rồi dùng `git revert` để hoàn tác an toàn (không mất lịch sử), push bản sửa cuối cùng lên GitHub. Toàn bộ lịch sử commit thể hiện rõ quá trình này tại: https://github.com/youngdragon26/git-basic-practice/commits/main
