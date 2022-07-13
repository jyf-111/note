wsl2 ./.bashrc 最后一行加上   

export DISPLAY="`grep nameserver /etc/resolv.conf | sed 's/nameserver //'`:0"

获取wsl 交换机ip 连接 xserve

function setproxy() {
	host_ip=$(cat /etc/resolv.conf |grep "nameserver" |cut -f 2 -d " ") # 获取ip地址
	echo $host_ip # 输出ip地址
	export ALL_PROXY="http://$host_ip:10809" # 设置代理，7890为我的代理端口
	echo "set proxy down"
}

terminal ctrl+s反向搜索 ctrl+r正向搜索
