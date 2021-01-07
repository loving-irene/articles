### /sys/devices 目录说明

该目录下包含所有被发现的注册在各种总线上的各种物理设备。一般来说，所有的物理设备都按照拓扑结构来显示。但有两个例外：platform devices 和 system devices。

platform devices一般是挂在芯片内部的高速或者低速总线上的各种控制器和外设，它们能被CPU直接寻址；

system devices不是外设，而是芯片内部的核心结构，比如CPU，timer等，它们一般没有相关的驱动，但是会有一些体系结构相关的代码来配置它们。