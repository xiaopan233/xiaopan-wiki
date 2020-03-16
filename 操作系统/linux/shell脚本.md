# shell脚本

不想让字符串作为命令：
	s=$(cat a.txt)
	
即可

curl

	curl -b "cookie" "网址"

for

	for i in $(seq 1 1 40)
	do
		echo $i
	done

if

	if [ "$res"x = ""x ]	#注意 = 两边有空格，[ ] 和字符串之间也有空格
	then
		echo "AAAAAAAAAAAAAAAAA"
	else
		echo "BBBBBBBBBBBBBBBBBB"
	fi
