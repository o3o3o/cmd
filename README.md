
##send data to udp
sudo echo -e ":reg_show_sbc:\nuac_registrant" > /dev/udp/192.168.139.142/9999

##dump any | lo
tcpdump   -i  lo  -s  0  -w /tmp/catch.pcap
tcpdump    -i  any  -s  0  -w  catch.pcap

##remove old kernel version
sudo apt-get remove --purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d')

##mount (phone's) ftp to local disk
curlftpfs ftp://192.168.0.105:3721 /tmp/phone

##Install ubuntu
title Install Ubuntu
root (hd0,0)
kernel (hd0,0)/vmlinuz boot=casper iso-scan/filename=/ubuntu-10.04-desktop-i386.iso ro 
initrd (hd0,0)/initrd.lz
boot

sudo umount -l /isodevice

##move linux 
sudo dpkg --get-selections > packagelist.txt
sudo dpkg --set-selections < packagelist.txt
sudo apt-get -u dselect-upgrade


##unzip乱码
unzip -O CP936 xxx.zip
## 录制动画
sudo add-apt-repository ppa:fossfreedom/byzanz
sudo apt-get install byzanz
byzanz-record -d 40 -x 0 -y 0 -w 1200 -h 800 byzanz-demo.gif
其中：
• -d 40 为录制的时长为 40 秒
• -x 0 录制区域的横坐标
• -y 0 录制区域的纵坐标，记住：屏幕右上角为原点（0,0）
• -w 400 录制区域的宽度
• -h 320 录制区域的高度
• byzanz-demo.gif 保存的文件名


##others
cscope -qRb
lsusb
apropos

mkdir -p project/{lib/ext,bin,src,doc/{html,info,pdf},demo/stat/a}
cd tmp/a/b/c || mkdir -p tmp/a/b/c && tar xvf -C tmp/a/b/c ~/archive.tar
echo ls -l | awk '$6== "Dec"'

tar -cvpzf /backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

.config /etc/bashrc
.bashrc .vimrc .vim
.bashOoO .bash_alias
StarDict -> /usr/share/stardict/
