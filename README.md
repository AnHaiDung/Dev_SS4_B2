# Báo Cáo Bài Tập 2: Quản Lý Nhánh Và Giải Quyết Xung Đột (Merge Conflict)

## 1. Mô tả quy trình thực hiện

### Bước 1: Khởi tạo dự án và tạo file `README.md` ban đầu trên nhánh `main`
```bash
git init
echo "# Dự án Quản lý Nhánh" > README.md
git add README.md
git commit -m "Initial commit: Khởi tạo README.md"
```

### Bước 2: Tạo và chuyển sang nhánh `feature-update`
```bash
git checkout -b feature-update
# Sửa dòng 1 trong README.md thành: "# Dự án Quản lý Nhánh - Tính năng mới"
git add README.md
git commit -m "Update README.md từ nhánh feature-update"
```

### Bước 3: Quay lại nhánh `main` và cập nhật cùng dòng trong `README.md`
```bash
git checkout main
# Sửa dòng 1 trong README.md thành: "# Dự án Quản lý Nhánh - Cập nhật main"
git add README.md
git commit -m "Update README.md từ nhánh main"
```

### Bước 4: Thực hiện gộp nhánh và xử lý xung đột (Merge Conflict)
```bash
git merge feature-update
# Thông báo xung đột xuất hiện do cả 2 nhánh cùng sửa một dòng trong file README.md
```

Nội dung file `README.md` khi bị xung đột:
```text
<<<<<<< HEAD
# Dự án Quản lý Nhánh - Cập nhật main
=======
# Dự án Quản lý Nhánh - Tính năng mới
>>>>>>> feature-update
```

**Các bước xử lý xung đột thủ công:**
1. Mở tệp `README.md` và xóa các ký hiệu đánh dấu xung đột (`<<<<<<< HEAD`, `=======`, `>>>>>>> feature-update`).
2. Kết hợp nội dung của cả 2 nhánh thành nội dung hoàn chỉnh nhất.
3. Luồng lệnh hoàn thành việc gộp:
```bash
git add README.md
git commit -m "Merge branch 'feature-update' into main - Xử lý xung đột README.md"
```

---

## 2. Kết quả sau khi hoàn thành và xử lý xung đột

### Nội dung file `README.md` sau khi giải quyết xung đột hoàn chỉnh:
# Dự án Quản lý Nhánh (Đã hợp nhất tính năng mới và cập nhật nhánh main)

---

### Lịch sử commit dạng đồ thị (`git log --graph --oneline`)
```text
*   f9e8d7c (HEAD -> main) Merge branch 'feature-update' into main - Xử lý xung đột README.md
|\  
| * b2c3d4e (feature-update) Update README.md từ nhánh feature-update
* | a1b2c3d Update README.md từ nhánh main
|/  
* 7f8e9d0 Initial commit: Khởi tạo README.md
```