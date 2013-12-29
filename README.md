我的初步想法是一个后台进程监听某个端口，收到指令后，启动mac server。
这个进程应该可以附着在mac server上
1.让后台进程监听端口

2.获得权限，启动mac server。

苹果提供的用来启动别的程序例子（SMJobBless https://developer.apple.com/library/mac/samplecode/SMJobBless/Introduction/Intro.html）运行报错。。
##Four types of background processes in OS 
Login item
XPC service
Launch Daemon
Launch Agent

https://developer.apple.com/library/mac/documentation/macosx/conceptual/bpsystemstartup/Chapters/DesigningDaemons.html#//apple_ref/doc/uid/10000172i-SW4-BBCBHBFBX. 

我认为应该用Launch Agent方式, 对比XPC, 他可以展示UI，也可以不。
#Launch Agents
Agents are managed by launchd, but are run on behalf of the currently logged-in user (that is, in the user context). Agents can communicate with other processes in the same user session and with system-wide daemons in the system context. They can display a visual interface, but this is not recommended.

#XPC
The XPC Services API, part of libSystem, provides a lightweight mechanism for basic interprocess communication integrated with Grand Central Dispatch (GCD) and launchd. The XPC Services API allows you to create lightweight helper tools, called XPC services, that perform work on behalf of your application.

#Tip
Who is listening on a given TCP port on Mac OS X?

`lsof -n -i4TCP:$PORT | grep LISTEN`