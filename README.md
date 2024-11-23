# ROS-cnip-script
代码fork自DMF2022/ROS-cnip-script。

此列表代码搬运自[kiddin9/china_ip_list](https://github.com/kiddin9/china_ip_list)

IP地址使用

纯真库: https://raw.githubusercontent.com/metowolf/iplist/master/data/special/china.txt

ipip.net: https://raw.githubusercontent.com/17mon/china_ip_list/master/china_ip_list.txt

ispip.clang: https://ispip.clang.cn/all_cn.txt。

自动合并、去重、修改为ROS命令脚本文件，不定期更新。

根据个人使用习惯导入ROS到 “china-ip” 列表

>加了一条在导入前清空名为“china-ip”列表的命令，避免出现新旧列表交叉冲突。

>加了一条导入列表时关闭日志输出的指令，避免日志刷屏。

附：ROS导入脚本


###### 在/System Script下添加如下脚本内容
```
/tool fetch url=https://ghp.ci/https://raw.githubusercontent.com/HAOMK/ROS-cnip-script/refs/heads/main/cnip.rsc
/system logging disable 0
/import cnip.rsc
/system logging enable 0
:local CNIP [:len [/ip firewall address-list find list="china-ip"]]
/file remove [find name="cnip.rsc"]
:log info ("CNIP列表更新:"."$CNIP"."条规则")
```
建议手动执行，也可以在/System Scheduler下添加一个脚本定时
