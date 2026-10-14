# Tìm từ khóa trong file
## 1: Mục đích
#### đọc nội dung các file .log xong lọc các dòng có “TIMEOUT” và đếm kết quả (qua đường ống Pipeline | ) theo HĐH PowerShell.
 ### 2+3: Phân tích và giải 
 ##### Hệ điều hành powershell
 - Get-ChildItem -Recurse *.log: liệt kê tất cả các file có đuôi .log
 - Đọc nội dung trong file: Get-Content
 - Lọc từ khóa: select-string “TIMEOUT”
 - Where-Object { $_ -notmatch " NOT TIMEOUT"}) : dùng để tránh các dòng có NOT TIMEOUT và chỉ hiển thị các dòng TIMEOUT.
 - Đếm kết quả: .Count
## Giải 
(Get-ChildItem -Recurse *.log | Get-Content | select-string “TIMEOUT” |    Where-Object { $_ -notmatch " NOT TIMEOUT"}).Count
## 4 :so sánh
|powershell | Git bash | tác dụng |
|:---: | :---: | :---: |
| Get-ChildItem -Recurse *.log| ls .log| liệt kê tất cả các file có đuôi .log|
|Get-Content | cat .log | Đọc nội dung trong file|
|select-string | grep -v| Lọc từ khóa |
|Where-Object { $_ -notmatch " NOT TIMEOUT"})| grep -v| dùng để tránh các dòng có NOT TIMEOUT và chỉ hiển thị các dòng TIMEOUT |
|.Count | wc -l | Đếm kết quả|







