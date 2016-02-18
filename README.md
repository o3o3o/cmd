
## 在命令行通过dev设置直接发送数据udp包
sudo echo -e ":reg_show_sbc:\nuac_registrant" > /dev/udp/192.168.139.142/9999

## 抓取所有端口设备的包
tcpdump   -i  lo  -s  0  -w /tmp/catch.pcap

## remove old kernel version
sudo apt-get remove --purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d')

## mount (phone's) ftp to local disk
手机使用EsFile软件，打开ftp访问功能，通过curlftpfs来挂载手机内容到电脑
```
curlftpfs ftp://192.168.0.105:3721 /tmp/phone
```

## Install ubuntu
```
title Install Ubuntu
root (hd0,0)
kernel (hd0,0)/vmlinuz boot=casper iso-scan/filename=/ubuntu-10.04-desktop-i386.iso ro 
initrd (hd0,0)/initrd.lz
boot

sudo umount -l /isodevice
```


## 软件迁移
```
sudo dpkg --get-selections > packagelist.txt
sudo dpkg --set-selections < packagelist.txt
sudo apt-get -u dselect-upgrade
```

## unzip乱码
```
unzip -O CP936 xxx.zip
```

## linux下面录制动画gif

```
sudo add-apt-repository ppa:fossfreedom/byzanz
sudo apt-get install byzanz
byzanz-record -d 40 -x 0 -y 0 -w 1200 -h 800 byzanz-demo.gif
```
其中：
• -d 40 为录制的时长为 40 秒
• -x 0 录制区域的横坐标
• -y 0 录制区域的纵坐标，记住：屏幕右上角为原点（0,0）
• -w 400 录制区域的宽度
• -h 320 录制区域的高度
• byzanz-demo.gif 保存的文件名


## 其它

* C文件生成tags
```
cscope -qRb
```

* 建立多个目录
```
mkdir -p project/{lib/ext,bin,src,doc/{html,info,pdf},demo/stat/a}
```
