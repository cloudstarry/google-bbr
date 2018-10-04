# The script is from Teddysun

yum -y install wget

wget --no-check-certificate https://raw.githubusercontent.com/cloudstarry/google-bbr/master/bbr.sh

chmod +x bbr.sh

./bbr.sh

lsmod | grep bbr    // if it shows tcp_bbr and two numbers, done

***

# Remark
Sometimes BBR is not be able to speed up, network speed may be slower than before, espcially China Mobile network.

***
# Uninstall

vim /etc/sysctl.conf

#net.core.default_qdisc = fq  

#net.ipv4.tcp_congestion_control = bbr    // using # mask them

sysctl -p

reboot  your system
