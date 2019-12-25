# Linux_Command1

## Lệnh man
### 1. Các man page
- Được viết tắt của *Manual Page* (Trang hướng dẫn)
- Muốn thoát khỏi trang ta bấm ``q``

### 1.1. Man $command
- Nó giúp ta có cái có thể nhìn chi tiết các lệnh(VD: nó để làm gì, được dùng như thế nào,..)
```
man mkdir
```

![Imgur](https://i.imgur.com/uR0EeOi.png)

### 1.2. man $configfile
- Hầu hết các file config đều có hướng dẫn 
```
man rsyslog.conf
```
![Imgur](https://i.imgur.com/nYtYlGV.png)

### 1.3. man $daemon
- Nó cũng giống như hầu hết chương trình daemons( chương trình background) trên hệ thống  
```
    #man rsyslogd
```
![Imgur](https://i.imgur.com/LXmfsba.png)
### 1.4. man -k(apropos)

man -k(or apropos) giúp hiển thị danh sách các man page có chứa chuỗi
```
man -k syslog
```
![Imgur](https://i.imgur.com/K8gj9dr.png)
### 1.5. whatis
- Dùng để xem phần mô tả của 1 man page
```
#whatis ls
```
![Imgur](https://i.imgur.com/VmMHFrj.png)
### 1.6. whereis
- Dùng để xem vị trí lưu của man page
 ```
 #whereis -m mkdir
  -m ở đây nghĩa là chỉ tìm kiếm man page
 ```

 ![Imgur](https://i.imgur.com/8GzSKTq.png)  

 Tập tin này có thể được đọc trực tiếp bởi ``man``
 ```
 [root@localhost ~]# man /usr/share/man/man1/mkdir.1.gz
```
### 1.7. man sections
ý nghĩa các con số trong dấu ngoặc() khi dùng lệnh ``man``:  
1: Các chương trình thực thi hoặc các lẹnh shell  
2: Các cuộc gọi hệ thống (các chức năng được cung cấp bởi kernel)  
3: Các cuộc gọi từ thư viện(các chức năng trong thư viện chương trình)  
4: Các tệp đặc biệt (thường được tìm thấy trong / dev)  
5: các tệp đặc biệt (thường được tìm thấy trong /etc/passwd  
6: Trò chơi  
7: Khác (bao gồm các gói và quy ước vĩ mô), ví dụ: man (7)  
8: Lệnh quản trị hệ thống (thường chỉ dành cho root)  
9: Kernel routines [Không chuẩn]  
### 1.8. man $section $file
- Khi mà một file có quá nhiều phần (section) thì ta dùng section để mở đúng được page
```
#man 1 mkdir
```
### 1.9 man man
- man cũng có manual page của nó  

```
#man man

```
### 1.10 mandb
- Nếu ta tin rằng 1 man page tồn tại nhưng không thể truy cập thì ta sử dụng lệnh
```
#mandb
```
=================================================  

# Linux_command2

## 1.1 pwd
- Lệnh này giúp ta xem được vị trí đứng của mình đang làm việc
```
[root@localhost ~]# pwd
/root
```
## 1.2 cd 
- Lệnh này giúp ta thay đổi hoặc di chuyển đến 1 thư mục khác
```
[root@localhost ~]# pwd
/root
[root@localhost ~]# cd /home/
[root@localhost home]#
```
## 1.3. cd ~
- Lệnh này giúp ta di chuyển đến thư mục gốc hoặc có thể gõ ``cd`` nó cũng tự quay về thư mục home dir
```
[root@localhost home]# cd
[root@localhost ~]# cd /home/
[root@localhost home]# cd ~
[root@localhost ~]#
```
## 1.4. cd ..
- Giúp ta quay trở lại thư mục cha 
```
[root@localhost lock]# pwd
/var/lock
[root@localhost lock]# cd ..
[root@localhost var]#
```
## 1.5. cd -
- Quay trở lại thư mục trước đó mà ta vừa rời đi
```
[root@localhost var]# cd lock
[root@localhost lock]# pwd
/var/lock
[root@localhost lock]# cd -
/var
[root@localhost var]# pwd
/var
[root@localhost var]# cd -
/var/lock
[root@localhost lock]# pwd
/var/lock
[root@localhost lock]#
```
## 1.6. ls 
- Lệnh này giúp ta liệt kê các nội dung của thư mục
- Các option đi kèm của lệnh ls gồm có:
    ```
    -a: hiển thị tất cả các file, thư mục và cả các thư mục ẩn.
    -l: hiển thị chi tiết hơn gồm các thuộc tính, các quyền, sở hữu, đọ lớn của file và dir
    -lh: Hiển thị chi tiết hơn nữa gồm các thông số dễ đọc hơn
    ```
VD:
```
    [root@localhost lock]# ls -a
    .  ..  kdump  lockdev  lvm  subsys
    [root@localhost lock]# ls -l
    total 0
    -rw-r--r--. 1 root root  0 Dec 25 20:45 kdump
    drwxrwxr-x. 2 root lock 40 Dec 25 20:45 lockdev
    drwx------. 2 root root 40 Dec 25 20:45 lvm
    drwxr-xr-x. 2 root root 60 Dec 25 20:45 subsys
    [root@localhost lock]# ls -lh
    total 0
    -rw-r--r--. 1 root root  0 Dec 25 20:45 kdump
    drwxrwxr-x. 2 root lock 40 Dec 25 20:45 lockdev
    drwx------. 2 root root 40 Dec 25 20:45 lvm
    drwxr-xr-x. 2 root root 60 Dec 25 20:45 subsys
    [root@localhost lock]#
```
## 1.7. mkdir
- Là từ viết tắt của Make Directory(Tạo thư mục)
- Giúp ta tạo các dir(thư mục)
- Ta có lệnh như sau:
```
#mkdir option <tên dir/ đường dẫn đến nơi tạo thư mục kèm tên của thư mục>
```
- Các option thường dùng:  
-p: tạo cả dir cha trong đường dẫn nếu mà dir đó chưa tồn tại  
-v: buộc lệnh này phải in ra xem có tạo thư mục thành công hay không
```
[root@localhost ~]# mkdir huydx99
[root@localhost ~]# ls
abc.txt          file6  file99  huydx    qwr.txt  thu11  thu8  thu99
anaconda-ks.cfg  file9  huy123  huydx99  thu100   thu3   thu9
```
```

[root@localhost ~]# mkdir -p huydx/huy123
[root@localhost ~]# ls
abc.txt          file6  file99  qwr.txt  thu11  thu99
anaconda-ks.cfg  file9  huydx   thu100   thu8
[root@localhost ~]# cd huydx
[root@localhost huydx]# ls
huy123
[root@localhost huydx]#
```
```
[root@localhost huydx]# mkdir -v huydx22
mkdir: created directory ‘huydx22’
[root@localhost huydx]#

```
## 1.8. rmdir
- Lệnh này giúp ta xóa thư mục
- Nếu thư mục trông ta dùng lệnh:
```
#rmdir option path
```
Option:
```
-p: Nó sẽ xóa từ cuối đường dẫn nếu trống rồi đến dir cha của nó rồi chạy ngược lại đến khi dir được xóa không trống
```
```
[root@localhost ~]# rmdir -p huydx/huy123
[root@localhost ~]# ls
abc.txt  anaconda-ks.cfg  file6  file9  file99  qwr.txt  thu100  thu11  thu8  thu99
[root@localhost ~]#
```
