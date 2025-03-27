### shell脚本：
一键给PVE添加CPU频率和各种温度显示，NVME硬盘，机械硬盘，固态硬盘信息：



![image](https://github.com/xdm2211/PVE-manager-status/blob/main/status.jpg)

脚本自动检测：一键给PVE增加温度和cpu频率显示，NVME，机械固态硬盘信息
理论上适合任何设备
自动适配传感器数据
自动检测NVME硬盘数量
自动检测机械，固态硬盘数量
自动检测CPU核心数量


使用方法：
可以一键执行下面：
```
(curl -Lf -o /tmp/temp.sh https://github.com/xdm2211/PVE-manager-status/blob/main/showtempcpufreq.sh || curl -Lf -o /tmp/temp.sh https://mirror.ghproxy.com/https://github.com/xdm2211/PVE-manager-status/blob/main/showtempcpufreq.sh) && chmod +x /tmp/temp.sh && /tmp/temp.sh remod
```


没有显示功耗的，请执行下面的命令安装依赖，请确保安装成功，就是最后的一行的输出，必须为 “成功!” 才表示安装成功了。
```
apt update ; apt install linux-cpupower && modprobe msr && echo msr > /etc/modules-load.d/turbostat-msr.conf && chmod +s /usr/sbin/turbostat && echo 成功！
```

如果你已经用别人的脚本之类的修改过页面，请先用下面命令先回复官方设置之后，才可以运行本脚本：

```
apt update
apt install --reinstall pve-manager=$(dpkg -l pve-manager | tail -n 1 | awk '{print $3}')
apt install --reinstall proxmox-widget-toolkit=$(dpkg -l proxmox-widget-toolkit | tail -n 1 | awk '{print $3}')
rm -f /usr/share/perl5/PVE/API2/Nodes.pm*bak
rm -f /usr/share/pve-manager/js/pvemanagerlib.js*bak
rm -f /usr/share/javascript/proxmox-widget-toolkit/proxmoxlib.js*bak
```

另外：每次pve升级之后都需要执行一次脚本，因为升级后PVE会自己还原文件。
