[connection]
 
id=my-network
 
uuid=72111c67-4a5d-4d5c-925e-f8ee26efb3c3
 
type=802-11-wireless
 
 
[802-11-wireless]
 
mode=infrastructure
 
#下面的MY_SSID改成你的wifi名称
 
ssid=MY_SSID
 
# Uncomment below if your SSID is not broadcasted
 
#hidden=true
 
 
[802-11-wireless-security]
 
auth-alg=open
 
key-mgmt=wpa-psk
 
#下面的MY_WLAN_SECRET_KEY改成你的wifi密码
 
psk=MY_WLAN_SECRET_KEY
 
 
[ipv4]
#这里是自动获取的，如果不想自动获取可以把下面的method=auto前面加上#，然后把它下面的#号去掉，改成#你家的ip即可。后续可以ha网页里面更改
method=auto
 
#method=manual
#address=192.168.1.111/24;192.168.1.1
#dns=8.8.8.8;8.8.4.4;
 
 
 
[ipv6]
addr-gen-mode=stable-privacy
method=auto