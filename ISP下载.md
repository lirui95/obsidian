 [csdn:isp下载](https://blog.csdn.net/qq_54967231/article/details/126448765?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522170091795716800180619561%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=170091795716800180619561&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_click~default-1-126448765-null-null.142^v96^pc_search_result_base1&utm_term=ISP%E4%B8%8B%E8%BD%BD&spm=1018.2226.3001.4187)
 stm32的ISP下载只能使用串口1，也就是对应串口发送接受引脚PA9和PA10。

不能使用其他串口，如串口2（串口2：PA2和PA3）。的ISP下载只能使用串口1，也就是对应串口发送接受引脚PA9和PA10。

不能使用其他串口，如串口2（串口2：PA2和PA3）。
 注意：（1）板子上的PA9和PA10（串口1引脚）分别用跳线帽与RX、TX连接（此为连接USB串口的发送接收电路）。

                 （2）在使用ISP下载时，应确保电脑已经安装了CH340驱动（可在设备管理器中查看）。

     下载工具：mcuisp（FlyMcu）
写入新程序，覆盖原有程序。

[[keil]]