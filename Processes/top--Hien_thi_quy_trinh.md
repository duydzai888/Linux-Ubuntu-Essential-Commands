# top - Hiển thị quy trình
## Menu
[1. Ghi chú](#GhiChu)

[2. Các ví dụ](#CacViDu)


<a name="GhiChu"></a>
### 1. Ghi chú
Sử dụng:
```
top -hv | -bcHiOSs -d secs -n max -u|U user -p pid(s) -o field -w [cols]
```

Lệnh đầu hiển thị các thông tin tóm tắt hệ thống được tổ chức vào 5 lĩnh vực.
Khu vực đầu tiên hiển thị thời gian hiện tại, thời gian kể từ lần khởi động cuối cùng, tổng số người dùng, tải trung bình của hệ thống trong 1, 5 và 15 phút qua.
Khu vực thứ hai hiển thị số lượng tiến trình và bao nhiêu tiến trình đang chạy, đang ngủ, đã dừng, thây ma.

Các khu vực cuối cùng hiển thị thông tin về CPU, bộ nhớ vật lý và bộ nhớ hoán đổi.

Trên cùng của lệnh cũng hiển thị danh sách chi tiết của tất cả các tiến trình đang chạy.
Theo mặc định, danh sách cung cấp các tiêu đề sau:
- `PID` : id quy trình.
- `USER` : chủ sở hữu của quá trình.
- `PR` : mức độ ưu tiên của quy trình.
- `NI` : giá trị tốt đẹp của quá trình.
- `VIRT` : bộ nhớ ảo được sử dụng bởi tiến trình.
- `RES` : bộ nhớ vật lý được sử dụng bởi quá trình.
- `SHR` : bộ nhớ được chia sẻ với các tiến trình khác.
- `S` : trạng thái của tiến trình (`D`: ngủ liên tục, `R`: đang chạy, `S`: đang ngủ, `T`: dừng bởi tín hiệu điều khiển công việc, `t`: dừng bởi trình gỡ lỗi trong quá trình theo dõi, `Z`: zombie).
- `% CPU` : tỷ lệ thời gian CPU mà quá trình đang khởi kiện.
- `% MEM` : phần bộ nhớ vật lý mà quá trình đang khởi kiện.
- `TIME` + : thời gian CPU được sử dụng bởi tiến trình.
- `COMMAND` : dòng lệnh dùng để bắt đầu tiến trình.

<a name="CacViDu"></a>
### 2. Các ví dụ
```
$ top
top - 17:23:08 up 1 day,  6:10,  1 user,  load average: 0.11, 0.04, 0.01
Tasks: 226 total,   1 running, 159 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.2 us,  0.1 sy,  0.0 ni, 99.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem : 32654668 total, 29423936 free,   798248 used,  2432484 buff/cache
KiB Swap: 37109756 total, 37109756 free,        0 used. 31335344 avail Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 1602 root      20   0 1570844  46868  26052 S   0.7  0.1   1:09.06 containerd
 1595 mongodb   20   0 1583628 106204  38000 S   0.3  0.3   9:02.59 mongod
 1792 mysql     20   0 1426572 181280  15792 S   0.3  0.6   1:21.88 mysqld
 ...
 ```
 
 Theo mặc định, danh sách được sắp xếp bằng cách sử dụng cột % CPU .
Để thay đổi tiêu đề (thêm hoặc bớt) và / hoặc điều chỉnh cột sắp xếp, hãy nhấn phím `f`.

Điều hướng bằng Up / Dn.
- Nhấn phím `d` hoặc <dấu cách> để thêm hoặc xóa tiêu đề.
- Nhấn phím `s` để áp dụng các thay đổi.
- Nhấn phím `q ` hoặc <esc> để thoát.
```
Fields Management for window 1:Def, whose current sort field is %CPU
   Navigate with Up/Dn, Right selects for move then <Enter> or Left commits,
   'd' or <Space> toggles display, 's' sets sort.  Use 'q' or <Esc> to end!

* PID     = Process Id             ENVIRON = Environment vars    
* USER    = Effective User Name    vMj     = Major Faults delta  
* PR      = Priority               vMn     = Minor Faults delta  
* NI      = Nice Value             USED    = Res+Swap Size (KiB) 
* VIRT    = Virtual Image (KiB)    nsIPC   = IPC namespace Inode 
* RES     = Resident Size (KiB)    nsMNT   = MNT namespace Inode 
* SHR     = Shared Memory (KiB)    nsNET   = NET namespace Inode 
* S       = Process Status         nsPID   = PID namespace Inode 
* %CPU    = CPU Usage              nsUSER  = USER namespace Inode
* %MEM    = Memory Usage (RES)     nsUTS   = UTS namespace Inode 
* TIME+   = CPU Time, hundredths   LXC     = LXC container name  
* COMMAND = Command Name/Line      RSan    = RES Anonymous (KiB) 
  PPID    = Parent Process pid     RSfd    = RES File-based (KiB)
  UID     = Effective User Id      RSlk    = RES Locked (KiB)    
  RUID    = Real User Id           RSsh    = RES Shared (KiB)    
  RUSER   = Real User Name         CGNAME  = Control Group name  
  SUID    = Saved User Id       
  SUSER   = Saved User Name     
  GID     = Group Id            
  GROUP   = Group Name          
  PGRP    = Process Group Id    
  TTY     = Controlling Tty     
  TPGID   = Tty Process Grp Id  
  SID     = Session Id          
  nTH     = Number of Threads   
  P       = Last Used Cpu (SMP) 
  TIME    = CPU Time            
  SWAP    = Swapped Size (KiB)  
  CODE    = Code Size (KiB)     
  DATA    = Data+Stack (KiB)    
  nMaj    = Major Page Faults   
  nMin    = Minor Page Faults   
  nDRT    = Dirty Pages Count   
  WCHAN   = Sleeping in Function
  Flags   = Task Flags <sched.h>
  CGROUPS = Control Groups      
  SUPGIDS = Supp Groups IDs     
  SUPGRPS = Supp Groups Names   
  TGID    = Thread Group Id     
  OOMa    = OOMEM Adjustment    
  OOMs    = OOMEM Score current
```