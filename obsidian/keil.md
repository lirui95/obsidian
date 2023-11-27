STLINK显示  
no target connected
1、首先检查驱动程序是否存在问题 
 （stlink存在不同版本，目前暂不清楚具体有什么影响）
   固件更新但是驱动不更新可能影响连接
2、ISP下载，如果SW-DO口被锁，可以采用ISP擦除，此外电压不稳也可能锁芯片。
3、更新keil固件的
在keil目录下有ST-LINK更新固件的程序，更新下固件有时候有可能解决问题(特别是报错为“Internal Command Error”的时候，有可能是这个问题)。如果更新固件后STLINK不能识别(即出现USB Communication Error)，重新安装驱动并重启(实在不行主板掉电即可)。

keil 定义函数不可在初始化函数之前 
keil 注释符号注意为英文
