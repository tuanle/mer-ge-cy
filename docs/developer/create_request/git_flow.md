# Git flow

## 1. Clone code base

### 1.1. Lấy remote address của dự án

```
https://git.lifetimetech.vn/ikaigo/ikaigo.git
```

*Lưu ý: Có thể setting ssh-key để clone code từ địa chỉ dạng "git@git.lifetimetech.vn:ikaigo/ikaigo.git" để không cần nhập username/password khi thực hiện các tao tác với git (Tham khảo tại [đây](https://help.github.com/articles/generating-ssh-keys/))*

### 1.2. Clone code

Tại thư mục chứa code, chẳng hạn `C:\xampp\htdocs` gõ lệnh:

```
git clone https://git.lifetimetech.vn/ikaigo/ikaigo.git ikaigo
```

Code của dự án sẽ được clone về thư mục `C:\xampp\htdocs\ikaigo`

### 1.3. Kiểm tra lại remote

Vào thư mục ikaigo. Kiểm tra lại địa chỉ remote

```
git remote -v
```

Nếu kết quả như sau thì việc clone code đã thành công.

```
origin  https://git.lifetimetech.vn/ikaigo/ikaigo.git (fetch)
origin  https://git.lifetimetech.vn/ikaigo/ikaigo.git (push)
```

## 2. Cập nhật code

Nên thực hiện kiểm tra tình trạng hiện tại vào đầu giờ sáng, trước khi bắt đầu làm việc hoặc trước khi làm một task mới.

```
git fetch origin
```

Kết quả nhận được sẽ có dạng:

```
From git.lifetimetech.vn:ikaigo/ikaigo
   d4afea6..1991b02  master     -> origin/master
 * [new branch]      I6974      -> origin/I6974
 * [new branch]      production -> origin/production
   f432c7a..51ada17  staging    -> origin/staging
```

Ta sẽ thấy các thay đổi trên hệ thống: các branch mới được tạo, các branch được cập nhật. Ngoài ra lệnh fetch còn cập nhật đồng bộ lại dữ liệu giữa repo local và repo remote.

Trường hợp branch master có thay đổi, cần cập nhật branch bằng lệnh:

```
git pull origin master
```

## 3. Bắt đầu code một redmine issue

### 3.1. Kiểm tra branch master đã được cập nhật hay chưa

Quay về branch master

```
git checkout master
```

Cập nhật origin remote repository

```
git fetch origin
```

Pull code mới nhất từ branch master

```
git pull origin master
```

### 3.2. Tạo branch mới từ branch master

**Tuyệt đối không tạo branch làm task từ bất kỳ một branch nào khác, kể cả branch issue có liên quan hoặc issue cha.**

Tạo branch mới

```
git checkout -b tên_branch
```

*Quy tắc đặt tên branch mới:*

```
RedmineIssuesId_Tên_màn_hình
RedmineIssuesId_Tên_chức_năng
```

Ví dụ:

```
6996_admin_login_page
9669_upload_image
```

Trường hợp issue fix bug hoặc issue con từ bất kỳ issue cha nào mà ta đã tạo branch. Tên branch nên được đặt như sau:

```
ParentIssuesId_ChildIssuesId_Tên_màn_hình_fixbug
ParentIssuesId_ChildIssuesId_Tên_chức_năng_enhancement
```

Ví dụ:

```
6996_8888_admin_login_page_fixbug
```

Một branch chỉ nên viết code để thực hiện một issue. Tránh code nhiều issue trên cùng một branch.

## 4. Tạo commit sau khi code xong

### 4.1. Kiểm tra lại các thay đổi sau khi code

```
git status
```

Ta sẽ nhìn thấy danh sách các file đã thay dổi:

```
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   public/js/view.js
        modified:   public/js/view.js.map
        modified:   resources/views/groups/permisions.blade.php
```

Kiểm tra lại các đoạn code đã thay đổi

```
git diff (for all)
git diff tên_file
```

Kết quả nhìn thấy có dạng:

```
diff --git a/public/js/view.js b/public/js/view.js
index a40d16b..74f2570 100644
--- a/public/js/view.js
+++ b/public/js/view.js
@@ -457,110 +457,6 @@ function updateChart(data, options) {
 function changeGroupUserProfileImage() {
     $('.menu-item .avatar').attr('src', $("#new-user-img").attr("src"));
 }
-$(document).ready(function() {
-    //delete manual button
-    $(document).on("click", ".delete-manual-btn", function() {
-        var manualId = $(this).attr("data-manual-id");
-        if (confirm("このマニュアルを削除します。よろしいですか？")) {
-            $('#manual-form-' + manualId).submit();
-        }
-    });
-});
 (function ($) {

     var base = {
@@ -1578,6 +1474,110 @@ $(document).ready(function() {
     });
 });
 $(document).ready(function() {
+    //delete manual button
+    $(document).on("click", ".delete-manual-btn", function() {
+        var manualId = $(this).attr("data-manual-id");
+        if (confirm("このマニュアルを削除します。よろしいですか？")) {
+            $('#manual-form-' + manualId).submit();
+        }
+    });
+});
```

Trong đó các dòng có dấu  "-" màu đỏ là các dòng đã bị xóa, các dòng có dấu "+" màu xanh là các dòng đã thêm vào. Bước này là bước kiểm tra cuối cùng xem các thay đổi về code có vấn đề gì ko? Ngoài ra còn kiểm tra các lỗi về coding convention như đặt tên biến, cấu trúc block, dấu cách thừa cuối dòng, ...

### 5.2. Tạo commit

Add các file thay đổi vào commit

```
git add tên_thư_mục
git add tên_file
```

*Chú ý không nên sử dụng lệnh `git add .`*

Ví dụ:

```
git add public/js/
git add resources/
```

Trường hợp có các file bị xóa, sử dụng lệnh `git add -u tên_thư_mục` lệnh này sẽ kiểm tra lại các trường hợp đổi tên file, trường hợp file bị xóa hoàn toàn hoặc trường hợp xóa file cùng tên sau đó add file mới vào.

Kiểm tra lại lần cuối các file đã được add vào commit:

```
git status
```

Kết quả hiển thị có dạng:

```
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   public/js/view.js
        modified:   public/js/view.js.map
        modified:   resources/views/groups/permisions.blade.php
```

Tạo commit và message commit

```
git commit
```

*Chú ý không nên sử dụng lệnh `git commit -m "message"`*

Màn hình sẽ hiển thị editor nhập message commit. Nhập message commit sau đó tiếp tục, commit sẽ được tạo.

*Quy tắc viết message commit:*

```
[RedmineIssueId][Mô tả ngắn gọn công việc thực hiện]
___Để cách một dòng trống ở đây___
```

Ví dụ:

```
[6996][Create admin login page]
--- NEWLINE ---

[9669][Fix bug when click button login]
--- NEWLINE ---
```

Dòng message đầu tiên không nên quá 50 kí tự vì màn hình log sẽ có thể không hiển thị hết.

Trường hợp issue phức tạp, nên comment nhiều hơn trong message commit. Cách viết như sau:

```
[RedmineIssueId][Mô tả ngắn gọn công việc]
___Để cách một dòng trống ở đây___
- mô tả chi tiết công việc 1
- mô tả chi tiết công việc 2
___Để cách một dòng trống nữa ở đây___
```

### 5.3. Kiểm tra lại commit vừa tạo

Sau khi tạo commit, cần kiểm tra lại commit vừa tạo:

```
git log --oneline -10
```

Kết quả hiển thị có dạng

```
2876587 [6996][Fix bug permission page]
977da01 Merge branch '4974_delete_js' into 'working'
....
```

Ta sẽ thấy commit vừa tạo cùng với mã hash và message nằm trên đầu của list log.

## 6. Push code lên remote repository

### 6.1. Cập nhật các thay đổi (đã diễn ra trong quá trình code ở local)

```
git fetch origin
```

### 6.2. Rebase local commit

Rebase là quá trình lấy các thay đổi trên branch origin master (các thay đổi trong code mà người khác đã làm và merge vào code base) vào branch ở local, sau đó đưa commit mà ta vừa tạo lên đầu  commit stack.

```
git pull --rebase origin master
```

**Tuyệt đối không pull rebase từ bất cứ branch nào khác.**

Trường hợp không có conflict (các mã code vừa do người khác đã thay đổi và merge vào code base, vừa do ta đã thay đổi trên local), sẽ có thông báo thành công hiện ra. Trường hợp có conflict ta cần phải thực hiện việc sửa conflict.

Xem các file conflict

```
git status
```

Các file cần sửa conflict sẽ hiển thị ở dạng "Both modified" màu đỏ. Sửa các file này, sau đó `git add` . Cuối cùng gõ lệnh tiếp tục rebase

```
git rebase --continue
```

### 6.3. Push code

```
git push origin tên_branch
```

Ví dụ:

```
git push origin 6996_admin_login
```

## 7. Tạo merge request

* Kiểm tra branch đã push trên `git.lifetimetech.vn`
* Tạo merge request và thông báo cho reviewer

## 8. Chỉnh sửa khi có comment

* Trường hợp có comment từ reviewer, cần sửa lại code và tiến hành rebase
