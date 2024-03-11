[[LINUX]]
shell是C语言编写的程序{文本编译器+解释执行器}
|
	==记录常见shell==
		alias：别名 
		echo ：回显
shell 变量：赋值与调用
	变量赋值 =
	变量调用 $
	只读 readonly var
	删除 unset var

	变量类型：整型 字符串 数组
		整型 declear var
		string="runoob"
		数组变量 my_array=（1 2 3 4 5）
		环境变量 PATH
		**特殊变量：** 有一些特殊变量在 Shell 中具有特殊含义，例如 $0 表示脚本的名称，$1, $2, 等表示脚本的参数。

	特殊变量： 有一些特殊变量在 Shell 中具有特殊含义，例如 $0 表示脚本的名称，$1, $2,                  表示脚本的参数。
	$#表示传递给脚本的参数数量，$? 表示上一个命令的退出状态等。

	获取字符串长度
		string="abcd"
		echo ${#string}   # 输出 4

编写注释
	以 # 开头的行就是注释，会被解释器忽略。

	通过每一行加一个 **#** 号设置多行注释，像这样：
	
	
	
	
	每一行加个#符号太费力了，可以把这一段要注释的代码用一对花括号括起来，定义成一个函数，没有地方调用这个函数，这块代码就不会执行，达到了和注释一样的效果。
	
	### 多行注释
	
	**使用 Here 文档**
	
	多行注释还可以使用以下格式：
	
	:<<EOF  
	注释内容...  
	注释内容...  
	注释内容...  
	EOF  
	
	以上例子中，: 是一个空命令，用于执行后面的 Here 文档，<<'EOF' 表示开启 Here 文档，COMMENT 是 Here 文档的标识符，在这两个标识符之间的内容都会被视为注释，不会被执行。
	
	EOF 也可以使用其他符号:
	
	## 实例
	
	: <<'COMMENT'  
	这是注释的部分。  
	可以有多行内容。  
	COMMENT  
	  
	:<<'  
	注释内容...  
	注释内容...  
	注释内容...  
	'  
	  
	:<<!  
	注释内容...  
	注释内容...  
	注释内容...  
	!  
	
	**直接使用 : 号**
	
	我们也可以使用了冒号 : 命令，并用单引号 ' 将多行内容括起来。由于冒号是一个空命令，这些内容不会被执行。
	
	格式为：: + 空格 + 单引号。
	
	## 实例
	
	: '  
	这是注释的部分。  
	可以有多行内容。  
	'


shell参数传递  
	执行shell脚本时，想脚本传递参数，$n,n你哦啊是数字，1为执行脚本第一个参数，
		echo "第二个参数为：$2";  
		echo "第三个参数为：$3";
特殊字符使用：
|参数处理|说明|
	
参数处理	说明
$#	传递到脚本的参数个数
$*	以一个单字符串显示所有向脚本传递的参数。
如"$*"用「"」括起来的情况、以"$1 $2 … $n"的形式输出所有参数。
$	脚本运行的当前进程ID号
$!	后台运行的最后一个进程的ID号
$@	与$*相同，但是使用时加引号，并在引号中返回每个参数。
如"$@"用「"」括起来的情况、以"$1" "$2" … "$n" 的形式输出所有参数。
$-	显示Shell使用的当前选项，与set命令功能相同。
$?	显示最后命令的退出状态。0表示没有错误，其他任何值表明有错误。


shell数组
	shell数组可以存放多值，初始时不需要指定大小；
	array_my=(1 2 3 4)
	读取数组的一般格式 
		${array_name[index]}
	关联数组
		键值关联映射
		-关联数组使用 
			[declare](https://www.runoob.com/linux/linux-comm-declare.html) 命令来声明，
			语法格式如下：
			declare -A array_name
		-关联数组访问
			declare -A site #声明关联数组
			site["google"]="www.google.com"
			site["runoob"]="www.runoob.com"
			site["taobao"]="www.taobao.com"
			echo ${site["runoob"]}
			
		-获取数组中的元素
			使用 @ 或 * 可以获取数组中的所有元素，例如：
			## 实例
			#!/bin/bash  
			# author:菜鸟教程  
			# url:www.runoob.com    
			my_array[0]=A  
			my_array[1]=B  
			my_array[2]=C  
			my_array[3]=D    
			echo "数组的元素为: ${my_array[*]}"  
			echo "数组的元素为: ${my_array[@]}"

shell运算符
	原生bash不支持数学运算，但可以通过其他命令实现，例如awk expr
		val=`expr 2 + 2`（注意为反引号，且符号之间有空格）
		echo "$val"
		执行为4
		
		条件表达式
			[$a==$b]
			if[$a!=$b]
			then echo"不等于"
			
		**注意：**
			- 乘号(*)前边必须加反斜杠(\)才能实现乘法运算；
			- if...then...fi 是条件语句，后续将会讲解。
			- 在 MAC 中 shell 的 expr 语法是：**$((表达式))**，此处表达式中的 "*" 不需要转义符号 "\" 。
		
		关系运算符
			|-eq|检测两个数是否相等，相等返回 true。|[ $a -eq $b ] 返回 false。|
			|-ne|检测两个数是否不相等，不相等返回 true。|[ $a -ne $b ] 返回 true。|
			|-gt|检测左边的数是否大于右边的，如果是，则返回 true。|[ $a -gt $b ] 返回 false。|
			|-lt|检测左边的数是否小于右边的，如果是，则返回 true。|[ $a -lt $b ] 返回 true。|
			|-ge|检测左边的数是否大于等于右边的，如果是，则返回 true。|[ $a -ge $b ] 返回 false。|
			|-le|检测左边的数是否小于等于右边的，如果是，则返回 true。|[ $a -le $b ] 返回 true。|

		bool运算符
			同数字逻辑运算

		字符串运算符
			|运算符|说明|举例|
			|---|---|---|
			|=|检测两个字符串是否相等，相等返回 true。|[ $a = $b ] 返回 false。|
			|!=|检测两个字符串是否不相等，不相等返回 true。|[ $a != $b ] 返回 true。|
			|-z|检测字符串长度是否为0，为0返回 true。|[ -z $a ] 返回 false。|
			|-n|检测字符串长度是否不为 0，不为 0 返回 true。|[ -n "$a" ] 返回 true。|
			|$|检测字符串是否不为空，不为空返回 true。|[ $a ] 返回 true。|

		文件检测运算符
			文件测试运算符用于检测 Unix 文件的各种属性。
			属性检测描述如下：
			
			|操作符|说明|举例|
			|---|---|---|
			|-b file|检测文件是否是块设备文件，如果是，则返回 true。|[ -b $file ] 返回 false。|
			|-c file|检测文件是否是字符设备文件，如果是，则返回 true。|[ -c $file ] 返回 false。|
			|-d file|检测文件是否是目录，如果是，则返回 true。|[ -d $file ] 返回 false。|
			|-f file|检测文件是否是普通文件（既不是目录，也不是设备文件），如果是，则返回 true。|[ -f $file ] 返回 true。|
			|-g file|检测文件是否设置了 SGID 位，如果是，则返回 true。|[ -g $file ] 返回 false。|
			|-k file|检测文件是否设置了粘着位(Sticky Bit)，如果是，则返回 true。|[ -k $file ] 返回 false。|
			|-p file|检测文件是否是有名管道，如果是，则返回 true。|[ -p $file ] 返回 false。|
			|-u file|检测文件是否设置了 SUID 位，如果是，则返回 true。|[ -u $file ] 返回 false。|
			|-r file|检测文件是否可读，如果是，则返回 true。|[ -r $file ] 返回 true。|
			|-w file|检测文件是否可写，如果是，则返回 true。|[ -w $file ] 返回 true。|
			|-x file|检测文件是否可执行，如果是，则返回 true。|[ -x $file ] 返回 true。|
			|-s file|检测文件是否为空（文件大小是否大于0），不为空返回 true。|[ -s $file ] 返回 true。|
			|-e file|检测文件（包括目录）是否存在，如果是，则返回 true。|[ -e $file ] 返回 true。|

SHELL命令 ：

SHELL流程控制：
	shell流程不可为空，
	一、if语句控制 
	if confition 
	then 
		command1
		command2
	fi
	
	if else 的 [...] 判断语句中大于使用 -gt，小于使用 -lt。
		if [ "$a" -gt "$b" ]; then
		    ...
		fi
		
		如果使用 ((...)) 作为判断语句，大于和小于可以直接使用 > 和 <。
		
		if (( a > b )); then
		    ...
		fi
	二、for语句控制 
		## for 循环
		与其他编程语言类似，Shell支持for循环。
		
		for循环一般格式为：
		
		for var in item1 item2 ... itemN
		do
		    command1
		    command2
		    ...
		    commandN
		done
	三、while流程控制
		while 循环用于不断执行一系列命令，也用于从输入文件中读取数据。其语法格式为：
		while condition
		do
		    command
		done
		以下是一个基本的 while 循环，测试条件是：如果 int 小于等于 5，那么条件返回真。int 从 1 开始，每次循环处理时，int 加 1。运行上述脚本，返回数字 1 到 5，然后终止。
		## 实例
				#!/bin/bash  
		int=1  
		while(( $int<=5 ))  
		do  
		    echo $int  
		    let "int++"  
		done
		until不再介绍
	四、case...esac选择语句 
		**case ... esac** 为多选择语句，与其他语言中的 switch ... case 语句类似，是一种多分支选择结构，每个 case 分支用右圆括号开始，用两个分号 ;; 表示 break，即执行结束，跳出整个 case ... esac 语句，esac（就是 case 反过来）作为结束标记。
		可以用 case 语句匹配一个值与一个模式，如果匹配成功，执行相匹配的命令。
		**case ... esac** 语法格式如下：
			case 值 in
		模式1)
		    command1
		    command2
		    ...
		    commandN
		    ;;
		模式2)
		    command1
		    command2
		    ...
		    commandN
		    ;;
		esac

SHELL函数：
LINUX shell可以定义函数，然后在脚本随意调用
	定义格式如下
		[ function ] funname [()]
		{
		
		    action;
		
		    [return int;]
		
		}
	函数返回值通过 #$? 获得 
		函数可以传入参数
			
			|   |   |
	|---|---|
	|$#|传递到脚本或函数的参数个数|
	|$*|以一个单字符串显示所有向脚本传递的参数|
	|$$|脚本运行的当前进程ID号|
	|$!|后台运行的最后一个进程的ID号|
	|$@|与$*相同，但是使用时加引号，并在引号中返回每个参数。|
	|$-|显示Shell使用的当前选项，与set命令功能相同。|
	|$?|显示最后命令的退出状态。0表示没有错误，其他任何值表明有错误。|


SHELL输入输出重定向
	需要注意的是文件描述符 0 通常是标准输入（STDIN），1 是标准输出（STDOUT），2 是标准错误输出（STDERR）
		|command > file|将输出重定向到 file。|
		|command < file|将输入重定向到 file。|
		|command >> file|将输出以追加的方式重定向到 file。|
		|n > file|将文件描述符为 n 的文件重定向到 file。|
		|n >> file|将文件描述符为 n 的文件以追加的方式重定向到 file。|
		|n >& m|将输出文件 m 和 n 合并。|
		|n <& m|将输入文件 m 和 n 合并。|
		|<< tag|将开始标记 tag 和结束标记 tag 之间的内容作为输入。|

SHELL文件包含 
	Shell 也可以包含外部脚本。这样可以很方便的封装一些公用的代码作为一个独立的文件
		格式如下 
			. filename   # 注意点号(.)和文件名中间有一空格，source filename
