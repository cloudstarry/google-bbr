# If your kernel edition of OS is higher than 4.9 like debian 9, please use following simple commands

echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf

echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf

sysctl -p

reboot your system

# Otherwise, use script from Teddysun or 91Yun. 
- Following script has been tested on 64-bit of CentOS 7, Debian 9 and Ubuntu 16 KVM & CentOS 7 XEN_hvm and does not support openVZ

yum -y install wget

wget --no-check-certificate https://raw.githubusercontent.com/cloudstarry/google-bbr/master/bbr.sh

chmod +x bbr.sh

./bbr.sh

lsmod | grep bbr    // if it shows tcp_bbr and two numbers, done


# Uninstall

vi /etc/sysctl.conf

#net.core.default_qdisc = fq  

#net.ipv4.tcp_congestion_control = bbr    // using # masks them

sysctl -p

reboot  your system
***

- Following script has been tested on 64-bit of CentOS 7, Debian 9 and Ubuntu 16 KVM & CentOS 7 XEN_hvm and does not support openVZ
- Following  has been tested on 64-bit CentOS 7 Minial of openVZ and default tcp port 9000-9999

wget --no-check-certificate https://raw.githubusercontent.com/cloudstarry/google-bbr/master/bbrvz.sh && bash bbrvz.sh

ping 10.0.0.2    // if it returns delay, done

Change Speed up Port Range:

vi /root/lkl/run.sh    //search 9000-9999

vi /root/lkl/haproxy.cfg    //search 9000-9999

reboot your system
***

# Remark

Sometimes BBR is not be able to speed up, network speed may be slower than before, espcially China Mobile network.


