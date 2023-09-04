
<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [Xem đường dẫn](#xem-đường-dẫn)
- [Xem file/folder](#xem-filefolder)
- [Di chuyển giữ các path](#di-chuyển-giữ-các-path)
- [Cấu hình HĐH](#cấu-hình-hđh)
- [Thủ thuật tăng hiệu xuất command](#thủ-thuật-tăng-hiệu-xuất-command)
- [Tạo và xóa thư mục](#tạo-và-xóa-thư-mục)
- [Tạo và xóa file](#tạo-và-xóa-file)
- [Copy file/folder](#copy-filefolder)
- [Di chuyển hoặc đổi tên file/folder](#di-chuyển-hoặc-đổi-tên-filefolder)
- [Làm việc với VIM](#làm-việc-với-vim)
- [Làm việc với user](#làm-việc-với-user)
- [Làm việc với group](#làm-việc-với-group)

<!-- /code_chunk_output -->

#### Xem đường dẫn
- pwd: xem đường dẫn 
---------------------
#### Xem file/folder
- ls: xem file và thư mục 
  - ls -R: liệt kê các file con và thư mục bên trong nó
  - ls -a: liệt kê thêm các file ẩn
  - ls -l: hiển thị các thông tin chi tiết của các file
  - ls -al: hiểm thị thêm các thông tin chi tiết của file ẩn
---------------------
#### Di chuyển giữ các path
- cd: chuyển hướng trong hệ thống tập tin 
  - cd ..: di chuyển lên 1 cấp thư mục trên
  - cd: di chuyển tới thư mục home
  - cd /: di chuyển tới thư mục root
  - cd -: di chuyển tới thư mục trước đó 
---------------------
#### Cấu hình HĐH
- init + run level: cấu hình
  - init 0: shutdown hệ thống
  - init 1: dùng cho 1 người dùng để sửa lỗi hệ thống tập tin
  - init 2: không sử dụng
  - init 3: dùng cho nhiều người dùng nhưng chỉ giao tiếp dưới dạng text(không có giao diện)
  - init 4: không sử dụng 
  - init 5: dùng cho nhiều người dùng và được cung cấp đồ họa giao diện
  - init 6: reboot hệ thống
---------------------
#### Thủ thuật tăng hiệu xuất command
- Một vài thủ thuật
  - Gõ lệnh + tab: để gợi ý hoàn thành câu lệnh
  - Dùng phím mũi tên lên xuống để tái sử dụng lệnh
  - Ctrl + c: để hủy lệnh 
  - a && b: thực thi lệnh a và lệnh b cùng lúc (lệnh a thực hiện đúng thì lệnh b mới thực hiện)
  - a;b: không quan tâm lệnh a có đúng hay không => vẫn thực hiện lệnh b
  - Ctrl + r: để tìm kiếm câu lệnh đã thực hiện
  - apropos + 'mô tả chức năng câu lệnh': tìm kiếm câu lệnh để sử dụng
---------------------
#### Tạo và xóa thư mục
- mkdir \<name>: tạo thư mục 
- mkdir \<dir-name1> \<dir-name2> ... \<dir-namen>: tạo nhiều thư mục

  - mkdir -v \<dir-name1> \<dir-name2> ... \<dir-namen>: in ra thông điệp tạo thành công hay thất bại
  - mkdir -p \<dir-name1> \<dir-name2> ... \<dir-namen>: tạo thư mục bên trong 1 thư mục chưa có sẵn (mkdir -p hk2/hoa: tạo thư mục hóa bên trong thư mục hk2 chưa tồn tại)

- rmdir \<dir-name>: xóa thư mục rỗng 
- rmdir \<dir-name1> \<dir-name2> ... \<dir-namen>: xóa nhiều thư mục rỗng 

  - rm -r \<dir-name>: xóa thư mục không rỗng 
  - rm -r \<dir-name1> \<dir-name2> ... \<dir-namen>: xóa nhiều nhiều thư mục không rỗng 
---------------------
#### Tạo và xóa file
- touch \<file1> : tạo file mới 
- touch \<file1> \<file2> ... \<filen> : tạo nhiều file mới
- rm \<file>(rm -r \<file>): xóa file
---------------------
#### Copy file/folder
- cp \<source> \<destination>: copy source vào destination
  - cp -a \<source> \<destination>: 
  - cp -r \<source> \<destination>: copy source(file/folder name) vào destination(path name)
---------------------
#### Di chuyển hoặc đổi tên file/folder
- mv \<old name> \<new name> (mv \<old name-1> \<old name-2> \<old name-n> \<new name>)
    - Nếu new name trùng với thư mục khác => di chuyển
    - Còn không => là đổi tên
---------------------
#### Làm việc với VIM
- Trình soạn thảo văn bản VI
  - vi \<file name>: tạo 1 văn bản mới hoặc mở nếu nó tồn tại
  - Chia làm hai chế độ:
    - Nhấn i: chế độ soạn thảo văn bản (insert mode)
    - Nhấn ESC: chế độ thoát lệnh (command mode)
  - Thoát
    - q!: thoát và không lưu
    - wq!: thoát và lưu
---------------------
#### Làm việc với user
- Có hai loại user
  - User hệ thống (thực thi các module, script cần thiết phục vụ cho HĐH)
  - User người dùng (login để sử dụng HĐH, gồm supper user(root - quyền cao nhất) và regular user)
- Tên user là duy nhất, chỉ có thể đặt tên chữ thường, chữ hoa
- User thì có username và password
- Mỗi user có 1 mã định danh UID duy nhất
- Mỗi user thì có thể thuộc về nhiều nhóm (GID)
- Tài khoản supper user có uid = gid = 0

- cat etc/passwd: chứa tất cả thông tin user

|  name |  password encoder | UID | GID | name(description) | home directory | shell path |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|  root | x  | 0  | 0  | root  | /root  | /bin/bash  |

- sudo cat etc/shadow: chứa tất cả mật khẩu user
- Dùng quyền root

- Tạo user nhớ đặt mật khẩu
> Cú pháp: #useradd [option] \<username>
1. -c: thông tin người dùng
2. -d: thư mục cá nhân
3. -m: tạo thư mục cá nhân nếu chưa tồn tại
4. -g: nhóm người dùng
> Ví dụ: sudo **#useradd** -c "server admin" -g serveradmin vana
> Thay đổi thông tin cá nhân:
> **Cú pháp**: **usermod** [option] \<username>
> Nhũng option tương tự useradd
> Ví dụ: #usermode -g kinhdoanh vana //chuyển vana từ nhóm serveradmin sang nhóm kinhdoanh
> Ví dụ: sudo passwd giamdoc //đổi mật khẩu của giamdoc
> Ví dụ sudo usermode -c "chi la thu ki" giamdoc//đổi mô tả của giám đốc
> Xóa người dùng
> **Cú pháp**: #userdel [option] \<username>
> Ví dụ: #userdel -r vana
> Khóa/Mở khóa người dùng
> sudo passwd -l \<username> / sudo passwd -u \<username>
> sudo usermod -L \<username> / sudo usermode -U \<username>


---------------------
#### Làm việc với group
- Group: là tập hợp của nhiều user. Mỗi nhóm có một tên duy nhất và có một mã định danh duy nhất (GID)
- Khi tạo ra 1 user(không dùng option -g) thì mặc định 1 group được tạo ra
- Các user đọc được file con root mới thay đổi được

|  name |  password encoder | GID | list user |
|:---:|:---:|:---:|:---:|
|  adm | x  | 4  | syslog, ubuntu  |

> Tạo nhóm:
> Cú pháp: #groupadd \<groupname>
> Xóa nhóm:
> Cú pháp: #groupdel \<groupname>
> Chỉnh sửa:
> #groupmod:
> Sửa GID của nhóm users thành 201
> #groupmod -g 201 users
> Đổi tên nhóm accounting thành accountant
> #groupmod -n accountant accounting
> groups \<username> // \<username> ở group nào





