---
title: 如何在Ubuntu系统下启用硬件watchdog
category: computer
tags: watchdog ubuntu
published: true
---
我的一台GK41迷你主机因为系统的某种故障，会不定期死机，于是我尝试启用watchdog来实时检测系统状态，如果系统发生死机，则watchdog会自动将系统重启,保证系统的可用性。以下是我根据网上文章结合自己的机器整理的在Ubuntu系统下启用硬件watchdog的教程。

## 1. 检查系统是否有硬件watchdog

根据`/etc/watchdog.conf`:

```
# =================== The hardware timer settings ====================
#
# For this daemon to be effective it really needs some hardware timer
# to back up any reboot actions. If you have a server then see if it
# has IPMI support. Otherwise for Intel-based machines try the iTCO_wdt
# module, otherwise (or if that fails) then see if any of the following
# module load and work:
#
# it87_wdt it8712f_wdt w83627hf_wdt w83877f_wdt w83977f_wdt
#
# If all else fails then 'softdog' is better than no timer at all!
# Or work your way through the modules listed under:
#
# /lib/modules/`uname -r`/kernel/drivers/watchdog/
#
# To see if they load, present /dev/watchdog, and are capable of
# resetting the system on time-out.
```

使用modprobe命令依次尝试加载以下kernel module，看是否能正常加载（如果没有任何报错就是正常加载）：

```
sudo modprobe iTCO_wdt
sudo modprobe it87_wdt
sudo modprobe it8712f_wdt
sudo modprobe w83627hf_wdt
sudo modprobe w83877f_wdt
sudo modprobe w83977f_wdt
```

如果某个module加载成功了，则表示系统可能存在相应的硬件watchdog。

可以运行以下两个命令检查硬件watchdog是否被启用：

`sudo dmesg | grep wdt`

如果有类似以下返回内容则表示watchdog硬件成功被启用:

```
[    7.292623] w83977f_wdt: driver v1.00
[    7.293821] w83977f_wdt: initialized. timeout=45 sec (nowayout=0 testmode=0)
[    7.392506] w83977f_wdt: activated
```

`sudo lsmod | grep wdt`

如果有类似以下返回内容则表示watchdog硬件成功被启用:

```
w83977f_wdt            12288  1
```

## 2. 启用硬件watchdog

修改`/usr/lib/modprobe.d`目录下的linux内核blacklist文件(比如`/blacklist_linux-hwe-6.8_6.8.0-52-generic.conf`），将watchdog相应的module移除（即取消禁用）：

```
blacklist w83627hf_wdt
blacklist w83877f_wdt
blacklist w83977f_wdt # remove this line in my case
blacklist wafer5823wdt
```

## 3. 安装watchdog服务

`sudo apt-get install watchdog`

检查watchdog设备文件正常被watchdog自动生成：

```
ls -al /dev/watchdog*

crw------- 1 root root 10, 130 Oct 10 10:05 /dev/watchdog
```

## 4. 配置watchdog服务

`sudo vi /etc/watchdog.conf`

Uncomment the following lines by removing the `#` from beginning of the line:

```
watchdog_device: /dev/watchdog
interval: 10
```

Set the realtime option to yes and priority to 1:

```
realtime = yes
priority = 1
```

Save and close the file.

Modify the `/etc/default/watchdog` file and set the `watchdog_module` to `w83977f_wdt` (in my case):

`watchdog_module="w83977f_wdt"`

# 5. 配置wd_keepalive服务

使用wd_keepalive服务代替watchdog服务，可能是因为wd_keepalive服务功能更全面。以下步骤参考自[此文章](https://iobitsolutions.com/how-to-enable-linux-hardware-watchdog-service-on-ubuntu-22-04-on-vultr/)：

You will use the wd_keepalive service to monitor the watchdog device, therefore the watchdog daemon required to be stopped and disabled on startup.

Make sure the watchdog service is not running :

`sudo systemctl status watchdog.service`

```
    ● watchdog.service - watchdog daemon

       Loaded: loaded (/lib/systemd/system/watchdog.service; enabled; vendor preset: enabled)

       Active: inactive (dead)
```

Make sure the watchdog service is running then stop it:

`sudo systemctl stop watchdog.service`

check again and Make sure the watchdog service is not running : 

```
● watchdog.service - watchdog daemon

       Loaded: loaded (/lib/systemd/system/watchdog.service; enabled; vendor preset: enabled)

       Active: inactive (dead)
```

Disable the watchdog service on boot:

`sudo systemctl disable watchdog.service`

Edit the Systemd configuration file /lib/systemd/system/wd_keepalive.service and add the following lines under the [Install] section.

Just paste it in the end if there isn’t any  [Install] section on your file.

```
[Install]
WantedBy=multi-user.target
```

## 6. 设置wd_keepalive服务自启动

Reload systemd manager configuration:

`sudo systemctl daemon-reload`

Start the wd_keepalive service:

`sudo systemctl start wd_keepalive`

Enable the service to start at system boot:

`sudo systemctl enable wd_keepalive`

Check the status of the wd_keepalive service:

`sudo systemctl status wd_keepalive`

Reboot the system and confirm again that the wd_keepalive service is started on system boot:

`sudo systemctl status wd_keepalive`

Check the watchdog module is up and working by running `dmesg | grep w83977f_wdt` (in my case)

```
sudo dmesg | grep w83977f_wdt

[    7.292623] w83977f_wdt: driver v1.00
[    7.293821] w83977f_wdt: initialized. timeout=45 sec (nowayout=0 testmode=0)
[    7.392506] w83977f_wdt: activated
```

## 7. 测试watchdog是否正常工作

To test the watchdog service is configured properly and works as expected, you can trigger a system crash to check if the instance get rebooted.

by running this command you can perform a system crash by a NULL pointer dereference.

`sync; sleep 2; sync; echo c > /proc/sysrq-trigger`

Your system should automatically reboot in about a minute.

至此如果系统1分钟后自动重启，则说明硬件watchdog配置完成并且正常工作。

## 参考

- [https://iobitsolutions.com/how-to-enable-linux-hardware-watchdog-service-on-ubuntu-22-04-on-vultr/](https://iobitsolutions.com/how-to-enable-linux-hardware-watchdog-service-on-ubuntu-22-04-on-vultr/)