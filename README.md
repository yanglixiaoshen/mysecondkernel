# mysecondkernel
基于myfirstkenel,修改了mymian.c和myinterrupt.c后增加了进程间的切换和进程调度。

-------mysecondkernel 承接之前的myfirstkernel项目进行-------

sudo apt-get install qemu # install QEMU

sudo ln -s /usr/bin/qemu-system-i386 /usr/bin/qemu

wget https://www.kernel.org/pub/linux/kernel/v3.x/linux-3.9.4.tar.xz # download Linux Kernel 3.9.4 source code

wget https://raw.githubusercontent.com/yanglixiaoshen/myfirstkernel/master/mykernel_for_linux3.9.4sc.patch # download mykernel_for_linux3.9.4sc.patch

xz -d linux-3.9.4.tar.xz

tar -xvf linux-3.9.4.tar

cd linux-3.9.4

patch -p1 < ../mykernel_for_linux3.9.4sc.patch

这时把此工程下的新写的mymain.c和myinterrupt.c,mypcb.h下载下来，替换到之前mykernel目录下面。

make allnoconfig

make

cd mykernel 您可以看到qemu窗口输出的内容的代码mymain.c和myinterrupt.c

当前有一个CPU执行C代码的上下文环境，同时具有中断处理程序的上下文环境，我们初始化好了系统环境。

您只要在mymain.c基础上继续写进程描述PCB和进程链表管理等代码，在myinterrupt.c的基础上完成进程切换代码，一个可运行的小OS kernel就完成了。

start to write your own OS kernel,enjoy it!
