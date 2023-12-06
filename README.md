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
命令参考windbg命令,**注意16进制的地址需要加0x,不加会以10进制计算**
 * dt [[module!]!Name] [filed] [Address]     显示结构体 em: dt _PEB  0x401000;dt ntdll!_PEB
 * dt6 [[module!]!Name] [Address]    wow64进程下显示 64位的结构体  em: dt _PEB64
 * .reload [modulePath]   加载符号表   em：.reload C:\Windows\System32\ntoskrnl.exe
 * .cls  清屏
 
 * eb address value    以单字节写入内存  em: eb 0x401000 1
 * ew address value    以双字节写入内存 em: ew 0x401000  0x1111
 * ed address value    以四字节写入内存 em: ed  0x401000 0x4a5c1111
 * eq address value    以八字节写入内存 em: eq 0x401000  0x1111ffff123123

 * db address [Range]    以单字节读内存  em: db 0x401000
 * dw address [Range]    以双字节读内存 em: dw 0x401000  
 * dd address [Range]    以四字节写入内存 em: dd  0x401000  ; dd  0x401000 20
 * dq address [Range]    以八字节写入内存 em: dq 0x401000  
 * dbs address [Range]
 * dws address [Range]
 * dds address [Range]
 * dqs address [Range]

 * da address  显示ansi字符串
 * du address   显示unicode字符串
 * du8 address  显示utf8字符串

 * .sympath [path]  设置符号路径 em:.sympath SRV\*E:\symbol\*http://msdl.microsoft.com/download/symbols 

 * x [[module!]Name]模糊查找符号  em:  x  ntdll!*PEB*; x ntkrnlmp!PsGet*
