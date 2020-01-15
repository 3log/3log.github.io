
#获取系统信息
str_system_version=`cat /etc/issue`
echo "$str_system_version"
#如果包含"Ubuntu"
if [[ $str_system_version =~ "Ubuntu" ]]

#获取当前目录, cur_path不包含最后的 /
cur_path=$(cd "$(dirname "$0")"; pwd)

#判断目录是否存在
dir_path="/home/dir/"
if [ ! -d "${dir_path}" ]; then 
	echo "dir not exist"
fi

#判断文件是否存在
file_path="/home/file.txt"
if [ ! -f "${file_path}" ]; then
	echo "file.txt not exist"
fi
 
#判断是否存在并且是否具有可执行权限
file="/home/app"
if [ ! -x "${file}"]; then
 echo "file not exe permission"
fi

#判断一个变量是否有值
if [ ! -n "${tmp}" ]; then
 echo "变量为空！"
fi
 
# 判断两个变量的字符串内容是否相同
if [ "${aa}" = "${bb}" ]; then
 echo "${aa} equal ${bb}"
else
 echo "${aa} not equal ${bb}"
fi

#读取配置文件
config_path="/config/config"
input_eth=`awk -F'=' '/input_eth/{print $2}' ${config_path}`

#字符串逗号分隔
array_eth=(${input_eth//,/ })
eth_count=${#array_eth[@]}
echo "eth count="${eth_count}
for eth in ${array_eth[@]}
do
   echo "${eth}"
done
