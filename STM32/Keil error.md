L6235E:# More than one section matches selector - cannot all be FIRST/LAST.
多个启动文件同时添加，需要删去无用；
奇怪的是，源程序中存在多个文件，并未影响。
解释:通过对其他文件配置为禁止驶入

L3900U# 出现在对新版本添加旧版编译器，ARMCC与ARMCLANG （新版本已不含ARMCC）
当尝试将compiler5安装在ARMCLANG中时报错

工程链配置错误：
**交叉编译链**：C/C++程序的二进制编译（预编译、编译、链接）
包含部分：
	arch：目标CPU架构
	os：操作系统
	abi:应用二进制接口
	
[[keil]]**
**