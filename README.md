# ProcessesManager
一款windows64位的ark工具 rootkit
进程，线程，模块，驱动等

# 使用方法
* 加载符号表，请点击菜单项  main->加载符号，电脑首次运行软件需要，获取符号表过程中会卡顿
*  ![image](menu.png)
* 如果电脑不能访问符号表，需要自行下载，然后拷贝到软件根目录/syms下面
  * symchk.exe /r C:\Windows\System32\ntoskrnl.exe /s SRV*c:\symbols*http://msdl.microsoft.com/download/symbols
  * symchk.exe /r C:\Windows\System32\hal.dll /s SRV*c:\symbols*http://msdl.microsoft.com/download/symbols
  * symchk.exe /r C:\Windows\System32\user32.dll /s SRV*c:\symbols*http://msdl.microsoft.com/download/symbols
  * symchk.exe /r C:\Windows\SysWow64\user32.dll /s SRV*c:\symbols*http://msdl.microsoft.com/download/symbols

# 功能OneDbg命令支持及示例
命令参考windbg命令
*显示命令
dt [[module!]!Name] [Address]   em: dt _PEB;dt ntdll!_PEB
dt6
.re
.cl

ed"
eb"
ew"
eq"

dd"
db"
dw"
dq"
dds
dbs
dws
dqs

da"
du"
du8

.sy

x",
