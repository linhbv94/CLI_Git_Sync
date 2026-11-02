# Git Multi-Sync Tool (CLI)

[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg?style=flat-square)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Windows-0284c7?style=flat-square)](https://github.com/linhbv94/CLI_Git_Sync)
[![Ecosystem](https://img.shields.io/badge/part%20of-VXUtilities-0ea5e9?style=flat-square)](../_summary/master_overview.md)

**Git Multi-Sync Tool** là tiện ích dòng lệnh (CLI / Terminal) siêu nhẹ, chạy đa nền tảng (macOS & Windows), giúp tự động hóa việc quét, theo dõi trạng thái và đồng bộ hàng loạt kho lưu trữ Git cục bộ với remote (GitHub, GitLab, Bitbucket).

> **Tôn chỉ:** *Quét đệ quy thần tốc, phân loại trạng thái trực quan, đồng bộ an toàn 1-lệnh, không bao giờ tự ý ghi đè mất dữ liệu.*

---

## 1. Tính năng nổi bật

* **Quét đệ quy thông minh:** Tự động phát hiện toàn bộ các kho lưu trữ Git trong workspace làm việc (hỗ trợ danh sách bỏ qua `ignore_folders` như `node_modules`, `venv`, `.build`).
* **Phân loại trạng thái Git chuẩn xác:**
  * 🔴 **DIRTY:** Có tệp tin chưa commit (staged/unstaged changes, untracked files).
  * 🟡 **AHEAD:** Nhánh local có commit mới hơn remote cần `push`.
  * 🔵 **BEHIND:** Nhánh remote có commit mới hơn local cần `pull`.
  * 🟣 **DIVERGED:** Cả local và remote đều có commit mới lệch nhau (yêu cầu can thiệp thủ công).
  * 🟢 **UP_TO_DATE:** Nhánh local đã đồng bộ hoàn toàn với remote.
* **Đồng bộ thông minh 1-lệnh (Smart Sync):** Tự động thực hiện chuỗi lệnh `fetch`, `pull` (chỉ khi clean) và `push` (khi ahead) một cách an toàn. Bỏ qua các repo dirty hoặc xung đột.
* **Giao diện bảng điều khiển Terminal màu sắc:** Hiển thị dạng bảng trực quan, màu sắc rõ ràng (Green/Yellow/Red/Cyan) kèm thanh tiến trình.

---

## 2. Cài đặt & Hướng dẫn Sử dụng

### Chạy trực tiếp từ mã nguồn Python
```bash
cd zcli_gitsync

# Tạo môi trường ảo và cài đặt thư viện
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt  # hoặc pip install colorama pyyaml

# Chạy công cụ
python3 src/main.py
```

### Đóng gói thành file thực thi độc lập (.spec)
```bash
# Đóng gói binary bằng PyInstaller
pyinstaller git_multi_sync.spec
# File nhị phân độc lập sẽ nằm trong thư mục dist/
```

---

## 3. Cấu trúc Dự án

```text
zcli_gitsync/
├── docs/                 # Tài liệu hướng dẫn
├── git_sync_prd.md       # Đặc tả yêu cầu sản phẩm chi tiết
├── git_multi_sync.spec   # Cấu hình đóng gói PyInstaller
├── src/                  # Mã nguồn Python
│   ├── git_engine.py     # Lõi tương tác Git CLI & phân tích commit
│   ├── scanner.py        # Quét đệ quy thư mục
│   └── ui.py             # Render giao diện Terminal màu sắc
├── LICENSE               # Giấy phép MIT
└── README.md             # Hướng dẫn sử dụng này
```

---

## 4. Giấy phép & Bản quyền (License)

Dự án được phân phối dưới giấy phép mã nguồn mở **MIT License**.  
Xem toàn văn giấy phép tại tệp [LICENSE](LICENSE).

Bản quyền © 2026 Viet Linh Bui. Đã đăng ký toàn bộ quyền.
