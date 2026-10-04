# Bài 1: Khởi tạo Local Repository và Cấu hình danh tính

**Session 04 – Exercise 1** · Đường dẫn nộp bài: `homework/session_04/ex1/`

## 1. Mục tiêu

- Khởi tạo một Git repository trống tại thư mục làm việc cục bộ.
- Thiết lập danh tính tác giả (tên, email) ở cấp độ **local**.
- Tạo tệp mới, đưa vào Staging Area và thực hiện commit đầu tiên.
- Đọc trạng thái thư mục làm việc và lịch sử commit.

## 2. Các lệnh đã thực hiện

### Bước 1 – Tạo thư mục dự án và khởi tạo repository

```bash
mkdir session04-ex1
cd session04-ex1
git init
```

`git init` tạo thư mục ẩn `.git/`, biến thư mục hiện tại thành một local repository trống.

### Bước 2 – Cấu hình danh tính ở cấp độ local

```bash
git config --local user.name "Hung"
git config --local user.email "hungthac066@gmail.com"
```

Tùy chọn `--local` ghi cấu hình vào tệp `.git/config` của riêng repository này, không ảnh hưởng đến cấu hình toàn cục (`~/.gitconfig`) của máy.

### Bước 3 – Tạo tệp và kiểm tra trạng thái

```bash
echo "# Session 04 - Exercise 1" > README.md
git status
```

Lúc này `README.md` nằm ở trạng thái **Untracked** (chưa được Git theo dõi).

### Bước 4 – Đưa tệp vào Staging Area

```bash
git add README.md
git status
```

Tệp chuyển sang trạng thái **Changes to be committed** (đã nằm trong Staging Area).

### Bước 5 – Commit đầu tiên

```bash
git commit -m "Initial commit: add README.md"
```

## 3. Kiểm tra kết quả

### 3.1. Cấu hình email và tên cục bộ

```bash
git config --local user.email
git config --local user.name
```

Kết quả:

```text
hungthac066@gmail.com
Hung
```

### 3.2. Toàn bộ cấu hình local

```bash
git config --local --list
```

Kết quả:

```text
<!-- DÁN KẾT QUẢ THỰC TẾ CỦA BẠN VÀO ĐÂY, ví dụ:
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
user.name=Hung
user.email=hungthac066@gmail.com
-->
```

### 3.3. Lịch sử commit

```bash
git log --oneline
```

Kết quả:

```text
<!-- DÁN KẾT QUẢ THỰC TẾ CỦA BẠN VÀO ĐÂY, ví dụ:
a1b2c3d (HEAD -> main) Initial commit: add README.md
-->
```

### 3.4. Ảnh chụp màn hình

![Kết quả git config và git log](./screenshot.png)

## 4. Phân tích

| Nội dung | Giải thích |
| --- | --- |
| `--local` | Cấu hình chỉ áp dụng cho repository hiện tại, lưu trong `.git/config`. Có độ ưu tiên cao hơn `--global` và `--system`. |
| Working Directory → Staging Area | `git add` chọn những thay đổi sẽ được đưa vào commit kế tiếp. |
| Staging Area → Repository | `git commit` lưu snapshot của Staging Area vào lịch sử, gắn với tên và email tác giả đã cấu hình. |
| `git log --oneline` | Hiển thị mỗi commit trên một dòng: mã hash rút gọn + thông điệp commit. |

## 5. Kết luận

- Repository đã được khởi tạo thành công tại local.
- Danh tính tác giả được cấu hình riêng cho dự án bằng `--local`, không thay đổi cấu hình global.
- Lịch sử có 1 commit đầu tiên với thông điệp rõ nghĩa.
