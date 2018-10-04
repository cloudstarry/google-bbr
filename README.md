# The script is from Teddysun

yum -y install wget

wget --no-check-certificate https://raw.githubusercontent.com/cloudstarry/google-bbr/master/bbr.sh

chmod +x bbr.sh

./bbr.sh

lsmod | grep bbr  // if it shows tcp_bbr and two numbers, done

***

# Remark
Sometimes BBR is not be able to speed up, network speed may slower than before especiall China Mobile network. The reason is still researching.
