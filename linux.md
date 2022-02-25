wsl2 ./.bashrc 最后一行加上   

export DISPLAY="`grep nameserver /etc/resolv.conf | sed 's/nameserver //'`:0"

获取wsl 交换机ip 连接 xserve